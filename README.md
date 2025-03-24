
# Docker OCR Project - Résumé des Apprentissage

Ce projet regroupe les connaissances et compétences que j'ai acquises lors de l'apprentissage de Docker et de son intégration avec Docker Hub. Vous trouverez ici un résumé de toutes les étapes importantes pour créer, gérer et publier une image Docker.

## Table des matières

1. [Introduction à Docker](#introduction-à-docker)
2. [Création d'une Image Docker](#création-dune-image-docker)
3. [Taguer une Image Docker](#taguer-une-image-docker)
4. [Se Connecter à Docker Hub](#se-connecter-à-docker-hub)
5. [Publier une Image sur Docker Hub](#publier-une-image-sur-docker-hub)
6. [Rechercher des Images Docker sur Docker Hub](#rechercher-des-images-docker-sur-docker-hub)
7. [Commandes Docker Importantes](#commandes-docker-importantes)
8. [Conclusion](#conclusion)



## Introduction à Docker

Docker est une plateforme qui permet de créer, déployer et exécuter des applications dans des conteneurs. Ces conteneurs sont des environnements isolés, qui permettent d'exécuter des applications avec toutes leurs dépendances, garantissant ainsi que l'application fonctionne de manière cohérente sur n'importe quel système.

---

## Création d'une Image Docker

Pour commencer à utiliser Docker, vous devez d'abord créer une image. L'image Docker contient toutes les informations nécessaires pour exécuter une application, comme les dépendances et les configurations. Pour créer une image Docker, on utilise un fichier appelé **Dockerfile**.

### Exemple de création d'image :

1. Créez un fichier `Dockerfile` dans votre répertoire de projet.
2. Utilisez la commande suivante pour construire l'image :

```bash
docker build -t ocr-docker-build .
```

Cette commande crée une image Docker à partir du `Dockerfile` et lui donne le tag `ocr-docker-build`.

---

## Taguer une Image Docker

Une fois que vous avez créé une image Docker, vous pouvez la **taguer** afin de lui attribuer un nom spécifique qui permet de l'identifier sur Docker Hub.

### Exemple de tagging :

Si vous voulez envoyer cette image vers Docker Hub, vous devez l’associer à votre nom d’utilisateur Docker Hub. Utilisez la commande suivante :

```bash
docker tag ocr-docker-build:latest YOUR_USERNAME/ocr-docker-build:latest
```

Remplacez `YOUR_USERNAME` par votre nom d'utilisateur Docker Hub. Cela permet de créer une relation entre l'image locale et l'image Docker Hub.

---

## Se Connecter à Docker Hub

Avant de pouvoir pousser une image sur Docker Hub, vous devez vous connecter à Docker Hub via votre terminal.

### Commande de connexion :

```bash
docker login
```

Il vous sera demandé de saisir votre nom d'utilisateur et mot de passe Docker Hub.

---

## Publier une Image sur Docker Hub

Une fois l'image taguée et la connexion établie, vous pouvez publier votre image sur Docker Hub avec la commande `docker push`.

### Commande pour publier :

```bash
docker push YOUR_USERNAME/ocr-docker-build:latest
```

Cela enverra l'image vers Docker Hub, où elle sera disponible pour les autres utilisateurs ou pour être utilisée sur d'autres machines.

---

## Rechercher des Images Docker sur Docker Hub

Docker Hub est une registry publique où vous pouvez trouver des milliers d'images prêtes à l'emploi. Vous pouvez rechercher des images en utilisant la commande `docker search`.

### Exemple de recherche d'image :

```bash
docker search <image_name>
```

Cela vous permet de trouver une image Docker sur Docker Hub en fonction du nom que vous spécifiez.

---

## Commandes Docker Importantes

Voici un résumé des commandes Docker essentielles que vous devez connaître :

- **docker build** : Crée une image Docker à partir d'un Dockerfile.
- **docker tag** : Tagge une image locale pour la préparer à être envoyée vers Docker Hub.
- **docker push** : Envoie une image locale vers Docker Hub ou une autre registry.
- **docker login** : Se connecte à Docker Hub.
- **docker search** : Recherche une image sur Docker Hub.
- **docker pull** : Récupère une image depuis Docker Hub.
- **docker images** : Affiche toutes les images disponibles localement sur votre machine.
- **docker ps** : Affiche les conteneurs en cours d'exécution.
- **docker run** : Exécute un conteneur à partir d'une image.

---

## Conclusion

En résumé, Docker est un outil puissant pour le développement et le déploiement d'applications dans des environnements isolés et reproductibles. Ce projet m'a permis de comprendre le processus complet de la création, du taggage et de la publication d'images Docker, ainsi que de l'intégration avec Docker Hub pour partager des images avec d'autres utilisateurs.

Grâce à Docker, il est possible de garantir que les applications fonctionneront de manière cohérente sur différentes machines, ce qui est essentiel pour le développement d'applications modernes et distribuées.

## Ressources supplémentaires

- [Documentation Docker officielle](https://docs.docker.com/)
- [Docker Hub](https://hub.docker.com/)

---

Merci d'avoir consulté ce résumé de mes apprentissages avec Docker !

Je vous invite à parcourir les fichiers de ce projet pour obtenir davantage d'informations sur Docker et Docker Compose.