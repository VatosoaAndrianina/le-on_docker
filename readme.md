# leçon docker
# Télécharger une image depuis Docker Hub
docker pull <nom_de_l_image>

# Lister les images disponibles localement
docker images

# Supprimer une image
docker rmi <image_id>
# Exécuter un conteneur
docker run <options> <nom_image>

# Exemple : lancer nginx sur le port 8080
docker run -d -p 8080:80 nginx

# Lister les conteneurs en cours d'exécution
docker ps

# Lister tous les conteneurs (même ceux arrêtés)
docker ps -a

# Arrêter un conteneur
docker stop <container_id>

# Supprimer un conteneur
docker rm <container_id>
# Créer un volume
docker volume create mon_volume

# Lister les volumes
docker volume ls

# Supprimer un volume
docker volume rm mon_volume
FROM node:18
WORKDIR /app
COPY . .
RUN npm install
CMD ["npm", "start"]
docker build -t mon_app .
version: '3'
services:
  web:
    image: nginx
    ports:
      - "8080:80"
  db:
    image: postgres
    environment:
      POSTGRES_PASSWORD: exemple
docker-compose up -d
nginx.1 et nginx.2 sont des réplicas du même service.
Si n = 5 :
quorum = floor(5 / 2) + 1 = 3
tolérance = 5 - 3 = 2
→ Le système peut continuer à fonctionner avec 2 managers en moins
n = 5
quorum = 3
tolérance = 2
# Vérifier l’espace utilisé par Docker
docker system df

# Supprimer les ressources inutilisées
docker system prune

