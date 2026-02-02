# Conduit Container

Containerized version of the RealWorld "Conduit" application using Docker and Docker Compose.

This repository combines an existing Django backend, a React frontend, and a PostgreSQL database
to demonstrate multi-service container orchestration.

---

## Architecture

- **Frontend**: React application served via nginx
- **Backend**: Django application served via Gunicorn (WSGI)
- **Database**: PostgreSQL with persistent volume storage

All services are orchestrated using Docker Compose.

---

## Requirements

- Docker
- Docker Compose

No local installation of Node.js, Python, or PostgreSQL is required.

---

## Quickstart

```bash
cp .env.example .env
docker compose up --build
```

## After startup:
- Frontend: http://YOUR/URL 
- Backend API: http://YOUR/URL


## Notes
- The focus of this project is containerization and orchestration, not application development.
- Frontend and backend source code are based on the RealWorld Conduit example.
- Sensitive data is not committed; configuration is handled via environment variab

