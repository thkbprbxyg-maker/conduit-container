# Änderungen am Original Conduit Projekt

## Backend
- Integration in Docker Container
- Nutzung von Gunicorn statt Django Dev Server
- Konfiguration über Environment Variablen
- PostgreSQL-Anbindung via Docker Compose
- Entfernen lokaler Abhängigkeiten

## Frontend
- Build mit Node.js im Multi-Stage Dockerfile
- Auslieferung über Nginx
- Trennung von Build- und Runtime-Stage
- Anpassung der API-Base-URL für Container-Netzwerk