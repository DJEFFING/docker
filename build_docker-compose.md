**Définissez la version de Docker Compose**

Un fichier ``docker-compose.yml`` commence toujours par les informations suivantes :

````
version: '3'
````

L'argument ``version`` permet de spécifier à Docker Compose quelle version on souhaite utiliser, et donc d'utiliser ou pas certaines versions. Dans notre cas, nous utiliserons la version 3, qui est actuellement la version la plus utilisée.


**Déclarez le premier service et son image**

Nous allons maintenant déclarer notre premier service, et donc créer notre stack WordPress !
````
services:
  db:
    image: mysql:5.7
````

Puis, vous devez **décrire votre conteneur** ; dans notre cas, nous utilisons l’argument ``image`` qui nous permet de définir l'image Docker que nous souhaitons utiliser.

**Définissez le volume pour faire persister vos données**

````
services:
  db:
    image: mysql:5.7
    volumes:
      - db_data:/var/lib/mysql

````

Pour rappel, nous avons vu précédemment que **les conteneurs Docker ne sont pas faits pour faire fonctionner des services stateful**, et une base de données est par définition un service stateful. Cependant, vous pouvez utiliser l'argument ``volumes`` qui vous permet de stocker l'ensemble du contenu du dossier ``/var/lib/mysql`` dans un disque persistant. Et donc, de pouvoir garder les données en local sur notre host.

Cette description est présente grâce à la ligne ``db_data:/var/lib/mysql``  . ``db_data`` est un volume créé par Docker directement, qui permet d'écrire les données sur le disque hôte sans spécifier l'emplacement exact. Vous auriez pu aussi faire un /``data/mysql:/var/lib/mysql`` qui serait aussi fonctionnel.

**Définissez la politique de redémarrage du conteneur**

````
services:
  db:
    image: mysql:5.7
    volumes:
      - db_data:/var/lib/mysql
    restart: always
````
Un conteneur étant par définition monoprocessus, s'il rencontre une erreur fatale, il peut être amené à s'arrêter. Dans notre cas, si le serveur MySQL s'arrête, celui-ci redémarrera automatiquement grâce à l'argument restart: ``always``


**Définissez les variables d'environnement**
````
services:
  db:
    image: mysql:5.7
    volumes:
      - db_data:/var/lib/mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: somewordpress
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: wordpress
````

L'image ***MySQL*** fournie dispose de plusieurs variables d'environnement que vous pouvez utiliser ; dans votre cas, nous allons donner au conteneur les valeurs des différents mots de passe et utilisateurs qui doivent exister sur cette base. Quand vous souhaitez donner des variables d'environnement à un conteneur, vous devez utiliser l'argument ``environment``  , comme nous l'avons utilisé dans le fichier ``docker-compose.yml`` ci-dessus.


**Décrivez votre second service : WordPress**

Dans le second service, nous créons un conteneur qui contiendra le nécessaire pour faire fonctionner votre site avec WordPress. Cela nous permet d'introduire deux arguments supplémentaires.

````
services:
  wordpress:
    depends_on:
      - db
    image: wordpress:latest
    ports:
      - "8000:80"
    restart: always
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: wordpress
      WORDPRESS_DB_NAME: wordpress
````
Le premier argument, ``depends_on``  , nous permet de créer une **dépendance** entre deux conteneurs. Ainsi, Docker démarrera le service db avant de démarrer le service WordPress. Ce qui est un comportement souhaitable, car WordPress dépend de la base de données pour fonctionner correctement.

Le second argument, ``ports``  , permet de dire à Docker Compose qu'on veut exposer un **port** de notre machine hôte vers notre conteneur, et ainsi le rendre accessible depuis l'extérieur.


Voici le fichier **docker-compose.yml**dans sa version finale :
````
version: '3'
services:
  db:
    image: mysql:5.7
    volumes:
      - db_data:/var/lib/mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: somewordpress
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: wordpress
    
  wordpress:
    depends_on:
      - db
    image: wordpress:latest
    ports:
      - "8000:80"
    restart: always
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: wordpress
      WORDPRESS_DB_NAME: wordpress

volumes:
  db_data: {}
````

**En résumé**

Vous savez maintenant utiliser les commandes de base de Docker Compose, et créer un fichier docker-compose.yml pour orchestrer vos conteneurs Docker.

Pour rappel, voici les arguments que nous avons pu voir dans ce chapitre :

- ``image`` qui permet de spécifier **l'image source** pour le conteneur ;

- ``build`` qui permet de spécifier le **Dockerfile source** pour créer l'image du conteneur ;

- ``volume`` qui permet de spécifier les **points de montage** entre le système hôte et les conteneurs ;

- ``restart`` qui permet de définir le comportement du conteneur **en cas d'arrêt** du processus ;

- ``environment`` qui permet de définir les **variables d’environnement** ;

- ``depends_on`` qui permet de dire que le conteneur **dépend** d'un autre conteneur ;

- ``ports`` qui permet de définir les **ports** disponibles entre la machine host et le conteneur.