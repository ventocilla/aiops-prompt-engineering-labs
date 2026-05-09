# Justification

The R-T-F (Role, Task, Format) framework was applied by clearly separating the prompt into three structured sections.

## Role

The prompt defines the AI as a "Senior Platform Engineer and SRE specialized in Docker containers, Kubernetes and Python/Flask workloads in production environments". This role selection intentionally guides the model toward production-grade infrastructure practices, security concerns and operational readiness instead of generating a simplistic Dockerfile.

## Task

The task section provides:
- the project structure;
- runtime requirements;
- dependencies;
- execution command with Gunicorn;
- Kubernetes context;
- required environment variables;
- production constraints and best practices.

This detailed context reduces ambiguity and helps the model generate a realistic and operationally aligned Dockerfile.

## Format

The format section explicitly defines how the response should be delivered:
1. complete Dockerfile;
2. commented sections;
3. short technical explanation;
4. optional `.dockerignore`.

This structure improves readability, reproducibility and evaluation consistency.
