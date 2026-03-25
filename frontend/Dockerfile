# Build Stage
FROM node:20-alpine as build

WORKDIR /app

COPY package*.json ./
RUN npm ci

COPY . .
RUN npm run build

# Runtime Stage
FROM nginx:alpine

# Copy built app files into nginx html directory. The Angular build outputs into
# dist/angular-conduit (see angular.json). Copy the contents of that folder so
# the app's index.html replaces the default nginx welcome page.
COPY --from=build /app/dist/angular-conduit/ /usr/share/nginx/html/

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]