# Conduit Container (Starter)

This is the starter branch for review purposes.

This repository contains:
- **backend/** Django API (Gunicorn)
- **frontend/** Angular app served via nginx
- **PostgreSQL** via Docker Compose


## Table of Contents
- [Requirements](#Requirements)
- [Quickstart](#Quickstart)
- [Usage](#Usage)
- [Configuration](#Configuration)
- [Logs](#Logs)
- [Code Conventions](#Code Conventions) 
- [Deployment](#Deployment)

## Requirements
- Docker
- Docker Compose

No local installation of Python/Node/Postgres required.



## Quickstart
 1. Create environment file
    
```bash
cp .env.example .env
```

 2. Start the application
    
```bash
docker compose up --build
```


3. After startup: open the aplication:
- Frontend: 'http://<your_ip>:8282'
- Backend API: 'http://<your_ip>:8000/api'

Stop: the application:

```bash
docker compose down
```

## Usage

Configuration is done via environment variables in .env.
> [!IMPORTANT] 
> Create a .env file from .env.example before running Docker Comose. The stack andopen the app:
> - Backend: http://<your_IP>
> - Frontned: http://<your_IP> 



## Logs

View logs via CLI:
```bash
docker compose logs backend
docker compose logs frontend
docker compose logs db
```

Persist logs to file:

```bash
docker compose logs backend > backend-logs.txt
```

## Code Conventions

- Environment variables follow `UPPER_CASE_WITH_UNDERSCORE`
- Variables are always referenced using `${VAR_NAME}` syntax


## Deployment

This project uses GitHub Actions to automatically deploy the application to a remote VM via SSH.

### Deployment workflow
- The workflow is triggered on push to the `feature-deployment` branch.
- GitHub Actions connects to the remote server using SSH.
- The server pulls the latest version of the repository.
- Docker Compose stops old containers and rebuilds the application.
- The application is then started again in detached mode.

### Server setup
The deployment target is a remote Linux VM with Docker and Docker Compose installed.

### Exposed services
- Frontend: Port 8282
- Backend: Port 8000

### Notes
Sensitive data such as SSH credentials are stored in GitHub repository secrets and are not hardcoded in the repository.