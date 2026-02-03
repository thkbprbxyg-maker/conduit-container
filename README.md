# Conduit Container

Containerized version of the RealWorld "Conduit" application using Docker and Docker Compose.

This repository contains:
- **backend/** Django API (Gunicorn)
- **frontend/** Angular app served via nginx
- **PostgreSQL** via Docker Compose


## Project Structure & Review Notes

This repository intentionally uses a minimal `main` branch and a fully implemented `future` branch.

### Background
The initial setup used Git submodules for backend and frontend.  
This approach made the project harder to review and understand.

### Current Approach
- All backend and frontend source code is included directly in this repository
- Git submodules were completely removed
- The project is now fully self-contained and reviewable

### Branch Strategy
- `main` contains only a minimal README and serves as a clean baseline
- `future` contains:
  - Full backend source code
  - Full frontend source code
  - Dockerfiles
  - docker-compose configuration
  - `.env.example` (no sensitive data)

### Environment Variables
- `.env` is ignored and **not committed**
- `.env.example` is provided as a template
- Configuration is handled exclusively via environment variables


## Requirements
- Docker
- Docker Compose

No local installation of Python/Node/Postgres required.



## Quickstart

```bash
cp .env.example .env
docker compose up --build
```

After startup:
- Frontend: http://localhost:8282
- Backend API: http://localhost:8000/api

Stop:
```bash
docker compose down
```

## Configuration

Configuration is done via environment variables in .env.
Important: .env is not committed. Only .env.example is tracked.

## Logs

```bash
docker compose logs -f backend
docker compose logs -f frontend
docker compose logs -f db
```

## Table of Contents
- Overview
- Architecture
- Requirements
- Quickstart
- Usage
- Configuration
- Testing Checklist
- Logs
- Security Notes


## Testing Checklist

Before submitting this project, the following points were verified:

- [x] Frontend is reachable via browser on port 8282
- [x] Backend runs as WSGI application using Gunicorn (no dev server)
- [x] All services restart automatically on failure
- [x] Application is fully navigable and loads data correctly
- [x] Logs can be viewed via CLI
- [x] Logs can be persisted into files if required


## Logs

View logs via CLI:
```bash
docker compose logs backend
docker compose logs frontend
docker compose logs db
```

Persist logs to file:
docker compose logs backend > backend-logs.txt

## Code Conventions

- Environment variables follow `UPPER_CASE_WITH_UNDERSCORE`
- Variables are always referenced using `${VAR_NAME}` syntax