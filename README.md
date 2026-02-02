# Conduit Container

Containerized version of the RealWorld "Conduit" application using Docker and Docker Compose.

This repository contains:
- **backend/** Django API (Gunicorn)
- **frontend/** Angular app served via nginx
- **PostgreSQL** via Docker Compose

---

## Requirements
- Docker
- Docker Compose

No local installation of Python/Node/Postgres required.

---

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
