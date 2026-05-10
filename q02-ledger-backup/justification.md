# Justification

The R-T-F (Role, Task, Format) framework was applied by structuring the prompt into three clearly separated sections that guided the model toward a production-grade operational solution.

## Role

The prompt defines the AI as a "Senior SRE/DBA specialized in PostgreSQL, Linux automation, backup/restore operations and critical workload management in AWS environments".

This role selection intentionally directs the model toward operational reliability, infrastructure security, automation best practices and production-oriented Bash scripting instead of generating a simplistic backup example.

## Task

The task section provides detailed operational context, including:
- PostgreSQL environment configuration;
- AWS region and S3 bucket;
- Secrets Manager integration through IAM Roles;
- backup storage constraints;
- logging requirements;
- retention policy;
- execution through cron;
- dependency validation;
- security requirements and Bash best practices.

This detailed context significantly reduces ambiguity and encourages the generation of a realistic and operationally safe backup automation workflow.

## Format

The format section explicitly defines the expected deliverables:
1. complete Bash script;
2. commented sections;
3. cron execution example;
4. technical explanation;
5. operational and security considerations.

This structure improves readability, maintainability and evaluation consistency while ensuring the output remains aligned with real-world SRE operational documentation standards.
