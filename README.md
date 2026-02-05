# Conduit Container

Containerized version of the RealWorld "Conduit" application using Docker and Docker Compose.

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
- Frontend: http://<your_ip>:8282
- Backend API: http://<your_ip>:8000/api

Stop: the application:

```bash
docker compose down
```

## Usage

Configuration is done via environment variables in .env.
Important: .env is not committed. Only .env.example is tracked.



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
