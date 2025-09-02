# Exo 2

## Jouons un peu avec les containers

1. Démarrer Bash en intéractif dans un container, avec pour image de base `rockylinux:9`

2. Télécharger le fichier <http://ifconfig.me> avec la commande `wget` dans un **fichier**
  * Faites le nécéssaire pour que la commande fonctionne dans votre container

3. Afficher le fichier dans le **container**

4. **Quitter** le container et démarrer s'en un nouveau

   Trouvez-vous le fichier télécharger à l'étape précédente ?

   Expliquer pourquoi vous pouvez ou ne pouvez pas.

## exo :
```bash
docker run -it --rm rockylinux:9 bash
dnf install -y wget
wget -O ifconfig.me http://ifconfig.me
cat ifconfig.me
exit or ctrl+D
```