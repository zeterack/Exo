# Exo1

## Vérification de l'installation

Pour valider que votre installation a été correctement effectuer, valider les commandes suivantes :

```bash
docker info
docker run --rm rockylinux:9 date
```

Si vous devez mettre un `sudo` devant pour obtenir la date, utiliser la commande suivante pour ajouter votre utilisateur au groupe Docker

```bash
export current_user=${USER}
sudo usermod -a -G docker $current_user
```

Redémarrer ensuite le système ou fermer/ouvrer la session de votre utilisateur.