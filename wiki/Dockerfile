# Étape 1 : Utiliser une image de base officielle de Node.js
FROM node:16-alpine

# Étape 2 : Créer un répertoire de travail pour l'application
WORKDIR /wiki

# Étape 3 : Télécharger et extraire Wiki.js
RUN wget https://github.com/Requarks/wiki/releases/latest/download/wiki-js.tar.gz && \
    tar xzf wiki-js.tar.gz -C ./ && \
    rm wiki-js.tar.gz  # Supprimer l'archive après extraction

# Étape 4 : Déplacer dans le répertoire Wiki.js
WORKDIR /wiki

# Étape 5 : Installer les dépendances nécessaires pour Wiki.js
RUN npm install --production --legacy-peer-deps

# Étape 6 : S'assurer que le fichier de configuration est fourni depuis le système hôte ou un volume
# Nous copions un fichier `config.yml` de l'extérieur dans le conteneur
# Notez que vous devrez vous assurer d'avoir ce fichier `config.yml` prêt à être utilisé
COPY config.yml /wiki/config.yml

# Étape 7 : Exposer le port sur lequel Wiki.js écoute (par défaut 3000)
EXPOSE 3000

# Étape 8 : Démarrer le serveur Wiki.js
CMD ["node", "server"]
