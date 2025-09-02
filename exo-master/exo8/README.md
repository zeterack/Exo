# Exo 8 - Bonus !

## Dockerception

En partant du principe que **tout est fichier** sous Linux, vous pouvez monter la socket Docker dans un container.



1. Monter, dans l'image `docker`, le fichier `/var/run/docker.sock` dans le container (avec le même path)

   Lancer l'image Docker en interactif

2. Dans le container que vous venez de lancer, lancer un nouveau container (`centos7`, en mode intéractif) avec le volume `-v /DATA:/DATA`

3. Si vous écrivez dans dans le répertoire `/DATA/` du dernier container:

   1. Vous allez écrire dans le répertoire `/DATA/` du host ?

      ou

   2. Vous allez écrire dans le répertoire `/DATA/` du container que vous avez lancé à l'étape **1** ( container avec pour image `docker`)



## Serveur Docker - Daemon Docker

Sans utiliser **le client Docker**, faites des appels vers l'API Docker avec une commande `curl` pour arrêter et stopper un container.

* Exemple d'appel vers une socket Unix qui est l'équivalent à `docker ps` 

````bash
curl --unix-socket /var/run/docker.sock http:/localhost/containers/json | jq
````

[Docker Engine API Doc 1.41](https://docs.docker.com/engine/api/v1.41/)



