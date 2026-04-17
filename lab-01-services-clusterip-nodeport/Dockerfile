# Étape 1 : build React avec Node
FROM node:18-alpine AS build
WORKDIR /app

# Copier les fichiers package depuis frontend
COPY frontend/package*.json ./
RUN npm install

# Copier le reste du code frontend et build
COPY frontend/ ./
RUN npm run build

# Étape 2 : servir le build avec Nginx
FROM nginx:alpine
COPY --from=build /app/dist /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
