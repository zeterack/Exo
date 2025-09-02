# Exo 7

## Construction d'un docker-compose

1. Construisez un docker-compose qui permettra de monter la stack suivante:

* Deux sites Wordpress (à l'aide de l'image `wordpress`)
  * Un wordpress sur le port 8080, l'autre sur le port 8088
* Deux instances MySQL **différentes** (à l'aide de l'image `mysql:8`)
  * Les bases doivent **être persistées sur le disque**
* Une instance PHPMyAdmin (à l'aide de l'image `phpmyadmin`)
  * Sur le port 8090
  * L'instance PHPMyAdmin **doit être préconfigurée** avec les deux instances MySQL

2. Rajouter la construction d'un service qui affichera un site/page HTML personnalisé.
   1. L'image utilisé sera `nginx`.
   2. Les fichiers ne seront pas monter à travers un volume, mais seront intégrés à l'image.
