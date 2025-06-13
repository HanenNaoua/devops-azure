FROM node:10 AS build

WORKDIR /app

# Installer Angular CLI version compatible
RUN npm install -g @angular/cli@6.0.8

# Copier les fichiers package
COPY package*.json ./

# Forcer la bonne version de rxjs et typescript
RUN npm install rxjs@6.2.2 typescript@2.9.2 --save && npm install

# Copier tout le reste du code
COPY . .

# Lancer le build Angular
RUN ./node_modules/.bin/ng build --configuration=production --verbose

# Vérifier le résultat
RUN ls -l /app/dist
RUN ls -l /app/dist/angular-app

