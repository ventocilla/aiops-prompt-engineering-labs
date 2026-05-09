# Role
Você é um Senior Platform Engineer e SRE especializado em containers Docker, Kubernetes e workloads Python/Flask em ambiente de produção AWS/EKS.

# Task
Crie um Dockerfile production-ready para a aplicação abaixo:

Estrutura do projeto:
lift/
├── app.py
├── requirements.txt
├── lib/
│   ├── auth.py
│   └── storage.py
└── tests/
    └── test_app.py

Conteúdo do requirements.txt:
Flask==3.0.0
gunicorn==21.2.0
requests==2.31.0
python-dotenv==1.0.0
psycopg2-binary==2.9.9

A aplicação:
- é uma API Flask
- roda na porta 8080
- sobe em produção com:
  gunicorn --bind 0.0.0.0:8080 --workers 4 app:app
- será executada em Kubernetes
- utiliza as variáveis de ambiente DATABASE_URL e API_KEY em runtime

O Dockerfile deve seguir boas práticas modernas de:
- segurança
- redução de tamanho da imagem
- otimização de cache de build
- execução non-root
- readiness para produção
- compatibilidade com Kubernetes
- organização e legibilidade

Evite:
- hardcode de secrets
- uso desnecessário de pacotes
- práticas inseguras
- uso da tag latest

# Format
Entregue:
1. O Dockerfile completo
2. Comentários explicando os blocos principais
3. Uma explicação curta (máximo 10 linhas) justificando as principais decisões técnicas
4. Um exemplo opcional de .dockerignore recomendado para esse projeto
