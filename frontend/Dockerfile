# ---- Build stage ----
FROM node:20-alpine AS build
WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build


# ---- Runtime stage ----
FROM nginx:alpine

COPY --from=build /app/dist/angular-conduit/ /usr/share/nginx/html

# HIER rein, nicht im build-stage!
RUN printf "window.__env = { apiUrl: 'http://46.224.26.224:8000/api' };\n" > /usr/share/nginx/html/env.js

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
