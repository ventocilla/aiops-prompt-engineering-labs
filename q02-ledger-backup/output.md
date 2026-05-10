# Model Output

## Model
Claude Sonnet 4

## Why this model
Chosen for its strong capability in Bash scripting, infrastructure automation, operational reliability and production-grade SRE workflows.

---

## Generated Bash Script - ledger_backup.sh (comments in portugues)

```bash

#!/usr/bin/env bash
# =============================================================================
# ledger_backup.sh — Backup diário do PostgreSQL Ledger para S3
# Ambiente: Ubuntu 22.04 LTS | PostgreSQL | AWS us-east-1
# Autor: SRE/DBA Team
# =============================================================================
set -euo pipefail
IFS=$'\n\t'

# -----------------------------------------------------------------------------
# CONFIGURAÇÕES — Centralizar aqui facilita manutenção e auditorias
# -----------------------------------------------------------------------------
readonly DB_HOST="ledger-db.internal.hvt.io"
readonly DB_PORT="5432"
readonly DB_NAME="ledger_prod"
readonly DB_USER="backup_user"

readonly BACKUP_DIR="/var/backups/ledger"
readonly LOG_FILE="/var/log/ledger-backup.log"
readonly S3_BUCKET="s3://hvt-ledger-backups"
readonly AWS_REGION="us-east-1"

readonly TIMESTAMP=$(date +"%Y%m%d_%H%M%S")
readonly BACKUP_FILENAME="ledger_prod_${TIMESTAMP}.dump.gz"
readonly BACKUP_FILEPATH="${BACKUP_DIR}/${BACKUP_FILENAME}"

# Retenção S3: remover backups com mais de N dias
readonly RETENTION_DAYS=30

# Espaço mínimo em disco exigido antes do dump (em KB). 15 GB de margem.
readonly MIN_FREE_KB=$((15 * 1024 * 1024))

# -----------------------------------------------------------------------------
# FUNÇÕES UTILITÁRIAS
# -----------------------------------------------------------------------------

# log <mensagem> — Grava linha no log e no stdout com timestamp ISO-8601.
# A senha NUNCA é passada como argumento para esta função.
log() {
    local msg="$*"
    local ts
    ts=$(date +"%Y-%m-%dT%H:%M:%S%z")
    echo "${ts} [INFO] ${msg}" | tee -a "${LOG_FILE}"
}

log_error() {
    local msg="$*"
    local ts
    ts=$(date +"%Y-%m-%dT%H:%M:%S%z")
    echo "${ts} [ERROR] ${msg}" | tee -a "${LOG_FILE}" >&2
}

# die <mensagem> — Registra erro e termina com exit code 1.
die() {
    log_error "$*"
    exit 1
}

# cleanup — Remove arquivo local de backup se existir (evita resíduos em falha).
cleanup() {
    if [[ -f "${BACKUP_FILEPATH}" ]]; then
        log "Limpando arquivo local temporário: ${BACKUP_FILEPATH}"
        rm -f "${BACKUP_FILEPATH}"
    fi
}

# Registra o cleanup na saída do script (sucesso ou falha).
# Em caso de sucesso o arquivo já foi removido explicitamente; rm -f é idempotente.
trap cleanup EXIT

# -----------------------------------------------------------------------------
# VALIDAÇÕES PRÉ-EXECUÇÃO
# -----------------------------------------------------------------------------

validate_env() {
    log "=== Iniciando validação de ambiente ==="

    # 1. Variável de senha obrigatória (populada pelo AWS Secrets Manager via IAM Role)
    #    Validamos presença sem logar o valor.
    if [[ -z "${PGPASSWORD:-}" ]]; then
        die "PGPASSWORD não está definida. Verifique a IAM Role e o Secrets Manager."
    fi
    log "PGPASSWORD: presente (valor omitido dos logs)"

    # 2. Dependências de runtime
    local deps=("pg_dump" "gzip" "aws")
    for dep in "${deps[@]}"; do
        if ! command -v "${dep}" &>/dev/null; then
            die "Dependência ausente: '${dep}'. Instale antes de continuar."
        fi
        log "Dependência OK: ${dep} ($(command -v "${dep}"))"
    done

    # 3. Diretório de backup
    if [[ ! -d "${BACKUP_DIR}" ]]; then
        log "Diretório ${BACKUP_DIR} não existe. Criando..."
        mkdir -p "${BACKUP_DIR}"
        chmod 750 "${BACKUP_DIR}"
    fi

    # 4. Espaço em disco disponível
    local free_kb
    free_kb=$(df -k "${BACKUP_DIR}" | awk 'NR==2 {print $4}')
    if (( free_kb < MIN_FREE_KB )); then
        die "Espaço insuficiente em ${BACKUP_DIR}: ${free_kb} KB livres (mínimo: ${MIN_FREE_KB} KB)."
    fi
    log "Espaço disponível em ${BACKUP_DIR}: ${free_kb} KB"

    # 5. Credenciais AWS (IAM Role da instância EC2 — sem chaves hardcoded)
    if ! aws sts get-caller-identity --region "${AWS_REGION}" &>/dev/null; then
        die "Falha na autenticação AWS. Verifique a IAM Role da instância."
    fi
    log "Credenciais AWS: OK"

    log "=== Validação de ambiente concluída ==="
}

# -----------------------------------------------------------------------------
# ETAPA 1 — DUMP + COMPRESSÃO EM PIPELINE
# -----------------------------------------------------------------------------

run_backup() {
    log "=== Iniciando pg_dump | gzip ==="
    log "Banco: ${DB_NAME} | Host: ${DB_HOST}:${DB_PORT} | Usuário: ${DB_USER}"
    log "Destino local: ${BACKUP_FILEPATH}"

    # pg_dump em formato custom (-Fc) produz saída binária eficiente.
    # Fazemos pipe direto para gzip para nunca gravar o dump descomprimido em disco.
    # PGPASSWORD está no ambiente — não aparece em logs de processo (ps aux).
    # --no-password evita prompt interativo caso PGPASSWORD falhe.
    # -v é omitido intencionalmente para não poluir o log com detalhes de tabela.
    if ! pg_dump \
            --host="${DB_HOST}" \
            --port="${DB_PORT}" \
            --username="${DB_USER}" \
            --dbname="${DB_NAME}" \
            --format=custom \
            --no-password \
        | gzip -9 > "${BACKUP_FILEPATH}"; then
        die "Falha no pg_dump ou gzip. Verifique conectividade e permissões."
    fi

    local size_human
    size_human=$(du -sh "${BACKUP_FILEPATH}" | cut -f1)
    log "Dump concluído. Tamanho: ${size_human} → ${BACKUP_FILEPATH}"
    log "=== pg_dump | gzip concluído ==="
}

# -----------------------------------------------------------------------------
# ETAPA 2 — VALIDAÇÃO BÁSICA DO ARQUIVO GERADO
# -----------------------------------------------------------------------------

validate_backup_file() {
    log "=== Validando arquivo de backup ==="

    if [[ ! -f "${BACKUP_FILEPATH}" ]]; then
        die "Arquivo de backup não encontrado: ${BACKUP_FILEPATH}"
    fi

    local size_bytes
    size_bytes=$(stat -c%s "${BACKUP_FILEPATH}")

    # Rejeita arquivos menores que 1 MB — indica dump vazio ou corrompido.
    if (( size_bytes < 1048576 )); then
        die "Arquivo de backup suspeito (${size_bytes} bytes). Possível dump vazio ou corrompido."
    fi

    # Verifica integridade do gzip (lê o stream sem descompactar tudo).
    if ! gzip -t "${BACKUP_FILEPATH}" 2>/dev/null; then
        die "Arquivo gzip inválido: ${BACKUP_FILEPATH}"
    fi

    log "Arquivo válido: ${size_bytes} bytes, integridade gzip OK"
    log "=== Validação do arquivo concluída ==="
}

# -----------------------------------------------------------------------------
# ETAPA 3 — ENVIO PARA S3
# -----------------------------------------------------------------------------

upload_to_s3() {
    log "=== Iniciando upload para S3 ==="
    local s3_dest="${S3_BUCKET}/${BACKUP_FILENAME}"
    log "Destino S3: ${s3_dest}"

    # --storage-class STANDARD_IA reduz custo para backups raramente acessados.
    # --sse aws:kms usa a KMS key padrão do bucket (configure no bucket policy).
    # --only-show-errors omite progresso verboso; erros ainda aparecem no log.
    if ! aws s3 cp "${BACKUP_FILEPATH}" "${s3_dest}" \
            --region "${AWS_REGION}" \
            --storage-class STANDARD_IA \
            --sse aws:kms \
            --only-show-errors; then
        die "Falha no upload para S3: ${s3_dest}"
    fi

    log "Upload concluído: ${s3_dest}"
    log "=== Upload para S3 concluído ==="
}

# -----------------------------------------------------------------------------
# ETAPA 4 — REMOÇÃO DE BACKUPS ANTIGOS NO S3
# -----------------------------------------------------------------------------

purge_old_s3_backups() {
    log "=== Removendo backups S3 com mais de ${RETENTION_DAYS} dias ==="

    # Calcula data de corte no formato ISO-8601 que o S3 usa em LastModified.
    local cutoff_date
    cutoff_date=$(date -d "-${RETENTION_DAYS} days" +"%Y-%m-%dT%H:%M:%SZ")
    log "Data de corte: ${cutoff_date}"

    # Lista objetos do bucket, filtra os anteriores ao corte e deleta em lote.
    # O pipeline: list-objects-v2 → jq filtra por LastModified → xargs aws s3 rm.
    # Usamos jq para não depender de parsing frágil com awk/grep em datas.
    local old_keys
    old_keys=$(aws s3api list-objects-v2 \
        --bucket "${S3_BUCKET#s3://}" \
        --region "${AWS_REGION}" \
        --query "Contents[?LastModified<'${cutoff_date}'].Key" \
        --output text 2>/dev/null || true)

    if [[ -z "${old_keys}" || "${old_keys}" == "None" ]]; then
        log "Nenhum backup antigo encontrado para remover."
        return 0
    fi

    local removed=0
    while IFS= read -r key; do
        [[ -z "${key}" ]] && continue
        log "Removendo objeto antigo: s3://${S3_BUCKET#s3://}/${key}"
        if aws s3 rm "s3://${S3_BUCKET#s3://}/${key}" \
                --region "${AWS_REGION}" \
                --only-show-errors; then
            (( removed++ )) || true
        else
            log_error "Falha ao remover: ${key} (continuando rotina)"
        fi
    done <<< "${old_keys}"

    log "Objetos removidos do S3: ${removed}"
    log "=== Purge de backups antigos concluído ==="
}

# -----------------------------------------------------------------------------
# ETAPA 5 — LIMPEZA LOCAL (arquivo já enviado ao S3)
# -----------------------------------------------------------------------------

remove_local_backup() {
    log "=== Removendo arquivo local ==="
    rm -f "${BACKUP_FILEPATH}"
    log "Arquivo local removido: ${BACKUP_FILEPATH}"
    log "=== Limpeza local concluída ==="
}

# -----------------------------------------------------------------------------
# PONTO DE ENTRADA PRINCIPAL
# -----------------------------------------------------------------------------

main() {
    log "############################################################"
    log "# BACKUP LEDGER — INÍCIO: ${TIMESTAMP}"
    log "############################################################"

    validate_env
    run_backup
    validate_backup_file
    upload_to_s3
    purge_old_s3_backups
    remove_local_backup

    log "############################################################"
    log "# BACKUP LEDGER — CONCLUÍDO COM SUCESSO"
    log "############################################################"
}

main "$@"

```

---

## Cron Example

```cron
# Daily execution at 02:30 AM
30 2 * * * /usr/local/bin/ledger_backup.sh >> /var/log/ledger-backup-cron.log 2>&1
```

---

## Technical Decisions Generated by the Model

- Usage of `set -euo pipefail` for safer Bash execution.
- Validation of environment variables and dependencies before backup execution.
- Direct `pg_dump | gzip` pipeline to reduce disk usage.
- Timestamp-based backup naming for traceability.
- Automated retention policy for S3 backups older than 30 days.
- Validation of AWS credentials through IAM Role.
- Use of structured logging with timestamps.
- Avoidance of password exposure in logs and process arguments.

---

## Security and Operational Notes

- Secrets are expected through AWS Secrets Manager and IAM Roles.
- No credentials are hardcoded in the script.
- S3 uploads use server-side encryption (`aws:kms`).
- Backup integrity is validated using `gzip -t`.
- The script is designed for cron-based unattended execution.
