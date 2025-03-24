**PUBLIER UNE IMAGE DOCKER SUR LE DOCKERHUB**

Voici la première commande que vous allez utiliser : 

````
docker tag ocr-docker-build:latest YOUR_USERNAME/ocr-docker-build:latest  
````
 Celle-ci va créer un lien entre notre image ``ocr-docker-build:latest`` créée précédemment et l'image que nous voulons envoyer sur le Docker Hub ``YOUR_USERNAME/ocr-docker-build:latest``.


Vous pouvez maintenant exécuter la dernière commande nécessaire pour envoyer votre image vers le Docker Hub. Pour cela, vous allez exécuter la commande

````
docker push YOUR_USERNAME/ocr-docker-build:latest 
```` 

**En résumé**

Vous savez maintenant envoyer votre image sur le Docker Hub, et vous êtes aussi capable de rechercher des images sur celui-ci.

Retenez ces commandes importantes :

- ``docker push`` qui vous permet d'envoyer vos images locales sur une registry ;

- ``docker search`` qui vous permet de rechercher une image sur votre registry.