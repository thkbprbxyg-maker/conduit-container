# Conduit Container

Containerized version of the RealWorld "Conduit" application using Docker and Docker Compose.
The project consists of a Django backend, a React frontend, and a PostgreSQL database.

---

## Table of Contents
- Overview
- Architecture
- Requirements
- Quickstart
- Configuration
- Usage
- Logs
- Notes

---

## Overview
This project demonstrates how to containerize a multi-service web application using Docker.
It follows best practices such as:
- multi-stage builds
- environment-based configuration
- separation of frontend, backend, and database services

The application itself is based on the RealWorld "Conduit" example app.

---

## Architecture
The setup consists of three services:

- **frontend**  
  React application built with Node.js and served via nginx

- **backend**  
  Django application served via Gunicorn (WSGI)

- **db**  
  PostgreSQL database with persistent volume storage

All services are orchestrated using Docker Compose.

---

## Requirements
- Docker
- Docker Compose

No local installation of Node.js, Python or PostgreSQL is required.

---

## Quickstart

```bash
cp .env.example .env
```
```bash
docker compose up --build
```
After startup, the frontend is available at:
http://localhost:8282


## Configuration

Configuration is done via environment variables.

Sensitive data (credentials, secrets) is not stored in the repository.
Instead, a .env file is used and excluded via .gitignore.

Example variables:
```bash
POSTGRES_USER=conduit
POSTGRES_PASSWORD=conduit_password
POSTGRES_DB=conduit
SECRET_KEY=change_me
PORT=8000
```


## Usage
- Access the frontend via browser
- Backend is exposed internally and consumed by the frontend
- Containers automatically restart on failure


## Logs

Logs can be viewed via CLI:
```bash
docker compose logs backend
```
```bash
docker compose logs frontend
```
```bash
docker compose logs db
```


Logs can also be persisted to a file:
```bash
docker compose logs backend > backend-logs.txt
```

## Notes
- The backend uses Gunicorn (WSGI), no development server
- Docker images are kept small using multi-stage builds
- Database data is persisted via Docker volumes

Starter repository for the Conduit Container project.
This repository focuses on containerization and orchestration.
Application source code is included for completeness and demonstration purposes.

## Source Code Reference 

The original RealWorld Conduit repositories are archived and read-only, therefore forking and creating pull requests is not possible.

- Frontend: https://github.com/gothinkster/react-redux-realworld-example-app
- Backend: https://github.com/gothinkster/django-realworld-example-app