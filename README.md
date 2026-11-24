J'ai créé un Dockerfile pour le backend Node.js.

The Dockerfile permet de :

Use Node.js Alpine as the base image.

Set the working directory.

Copy the package files and install dependencies.

Copy the application source code.

Expose port 9000.

Start the server using npm start.

Pour le frontend React, j'ai créé un autre Dockerfile.

Les étapes principales sont :

Install the project dependencies.

Build the React application using Vite.

Install serve to serve the generated files.

Expose port 3000.

'ai utilisé docker-compose.yml pour gérer les différents services dans un seul fichier.

The application contains three services:

mongodb: database service.

server: Node.js backend, accessible on port 9000.

client: React frontend, accessible on port 3000.

J'ai également configuré un volume mongo-data pour conserver les données de MongoDB.

J'ai créé un Jenkinsfile pour automatiser le processus.

The pipeline contains the following stages:

Checkout: récupérer le projet depuis GitHub.

Build: construire les Docker images du serveur et du client.

Deploy & Test: démarrer les containers avec Docker Compose et vérifier que le backend et le frontend répondent correctement.

Post: arrêter les containers après l'exécution du pipeline.

Après les corrections de configuration, le pipeline Jenkins s'est exécuté avec succès.
Quelques commandes utilisées pendant le TP :

# Build and start containers

docker compose up -d --build

# Display containers

docker ps -a

# Display Docker images

docker images

# Stop containers

docker compose down
