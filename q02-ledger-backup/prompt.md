# Role
You are a Senior SRE/DBA specialized in PostgreSQL, Linux automation, backup/restore operations and critical workload management in AWS environments.

# Task
Create a production-ready Bash script to automate the daily backup of the Ledger PostgreSQL database.

Environment:
- Host: ledger-db.internal.hvt.io
- Port: 5432
- Database: ledger_prod
- Backup user: backup_user
- Password: PGPASSWORD environment variable populated by AWS Secrets Manager through the EC2 instance IAM role
- AWS Region: us-east-1
- Instance OS: Ubuntu 22.04 LTS
- Working directory with 80 GB free space: /var/backups/ledger
- Current average compressed dump size: ~12 GB
- S3 Bucket: hvt-ledger-backups
- Execution log: /var/log/ledger-backup.log

The script must:
- execute the database dump using pg_dump
- compress the dump using gzip
- generate backup filenames with timestamps
- validate whether PGPASSWORD is defined before execution
- validate required dependencies: pg_dump, gzip and aws cli
- upload the compressed file to S3 using aws s3 cp
- remove S3 backups older than 30 days
- log each execution step with timestamps
- return proper exit codes in case of failure
- avoid exposing passwords in logs
- follow Bash best practices: set -euo pipefail, functions, top-level variables and error handling

Assume the routine will be executed daily through cron.

# Format
Deliver:
1. Complete Bash script
2. Comments explaining the main blocks
3. Example cron entry for daily execution
4. Short explanation of the main technical decisions
5. Security and operational considerations
