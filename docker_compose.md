**Docker Compose est un outil permettant de définir et de gérer des applications multi-conteneurs.** En d'autres termes, Docker Compose simplifie le déploiement d'applications complexes qui nécessitent plusieurs conteneurs pour fonctionner, en permettant de les orchestrer facilement.

**À la découverte du CLI de Docker Compose**

Pour récupérer l'ensemble des images décrites dans votre fichier ``docker-compose.yml`` et les télécharger depuis le Docker Hub, vous devez faire un ``docker-compose pull``  . Du côté de Docker, la commande serait un ``docker pull``  .

 **les principales commandes de docker compose**
 - ``docker-compose up`` permet de lancer la création de l'ensemble des conteneurs (pour rappel, vous faites un ``docker run`` pour lancer un seul conteneur). Vous pouvez ajouter l’argument ``-d`` pour faire **tourner les conteneurs en tâche de fond**.

 - ``docker-compose stop`` permet d'arrêter une **stack** Docker Compose.**un stack est un ensemble de conteneurs Docker lancés via un seul et unique fichier Docker Compose**.

 - ``docker-compose down`` permet de supprimer l'ensemble de la stack Docker Compose et détruire l'ensemble des ressources.

 - ``docker-compose config`` qui vous permet de **valider la syntaxe de votre fichier**, et ainsi d'être certain de son bon fonctionnement.

***En résumé***

Vous connaissez maintenant les commandes principales pour utiliser une stack Docker Compose. Voici les commandes les plus importantes :

- ``docker-compose up -d`` vous permettra de démarrer l'ensemble des conteneurs en arrière-plan ;

- ``docker-compose ps`` vous permettra de voir le statut de l'ensemble de votre stack ;

- ``docker-compose logs -f --tail 5`` vous permettra d'afficher les logs de votre stack ;

- ``docker-compose stop`` vous permettra d'arrêter l'ensemble des services d'une stack ;

- ``docker-compose down`` vous permettra de détruire l'ensemble des ressources d'une stack ;

- ``docker-compose config`` vous permettra de valider la syntaxe de votre fichier docker-compose.yml  .
