FROM node:20-alpine AS build

WORKDIR /app

#Éviter les erreurs OpenSSL,
ENV NODE_OPTIONS="--openssl-legacy-provider"

#Copier les fichiers package.json et installer les dépendances,
COPY package.json package-lock.json ./

RUN npm install --legacy-peer-deps

#Copier le reste du projet,
COPY . .

#Vérifier la version Angular CLI,
RUN npx ng version (echo "❌ Angular CLI non trouvé !" && exit 1)

#Lancer le build Angular,
RUN npm run build -- --configuration=production --deleteOutputPath=false (echo "❌Build Angular failed!" && exit 1)

#Vérifier que le dossier dist existe,
RUN ls -l /app/dist/angular-app || (echo "❌ Dossier dist/ non trouvé !" && exit 1)
