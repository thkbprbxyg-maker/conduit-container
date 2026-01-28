# Changes Compared to the Original Conduit Project

## Backend
- Integration into a Docker container
- Use of Gunicorn instead of the Django development server
- Configuration via environment variables
- PostgreSQL integration via Docker Compose
- Removal of local machine dependencies

## Frontend
- Build using Node.js in a multi-stage Dockerfile
- Delivery via Nginx
- Separation of build and runtime stages
- Adjustment of the API base URL for the container network

 ## Original Source

This project is based on the RealWorld Conduit reference implementation:

- Frontend: https://github.com/gothinkster/react-redux-realworld-example-app
- Backend: https://github.com/gothinkster/django-realworld-example-app

## Changes in this Project

### Backend
- Dockerized Django backend using Gunicorn
- Environment-based configuration via .env
- PostgreSQL service added via docker-compose
- Production-ready WSGI setup

### Frontend
- Multi-stage Docker build for production
- Static build served via Nginx
- Environment separation between dev and prod
