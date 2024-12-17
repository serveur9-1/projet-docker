# Étape 1 : Build Vue.js
FROM node:20 as builder
WORKDIR /app

# Copier les fichiers de configuration et installer les dépendances
COPY package.json package-lock.json ./
RUN npm install

# Copier tout le projet et construire
COPY . .
RUN npm run build

# Étape 2 : Serveur Nginx pour la production
FROM nginx:stable
COPY --from=builder /app/dist /usr/share/nginx/html

# Exposer le port HTTP
EXPOSE 80

# Commande par défaut pour Nginx
CMD ["nginx", "-g", "daemon off;"]
