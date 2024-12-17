# Étape 1 : Installation des dépendances
FROM node:20 as builder
WORKDIR /app
COPY package.json package-lock.json ./
RUN npm install

# Copier tout le code source
COPY . .

# Étape 2 : Production
FROM node:20-slim
WORKDIR /app
COPY --from=builder /app /app

# Définir les variables d'environnement
ARG JWT_SECRET
ARG MONGO_URI

# Exposer le port
EXPOSE 3000

# Lancer l'application
CMD ["node", "src/app.js"]
