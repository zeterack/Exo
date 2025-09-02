# Exo 4

## Part 1 Création d'image docker

1. __Créer__ une image ayant pour base `rockylinux:9`
2. Installer le package `sl` dans cette image.
   1. Vous aurez besoin pour cela d'installer au **préalable** le package `epel-release` (Google It)
3. Réalisez une première version de l'image qui lance le binaire `sl`
   1. Lors du `docker run` vous __allez devoir préciser__ une option pour permettre à `sl` de dessiner sur votre terminal.

> Le tag de l'image doit être `:1st`

5. Faites en sorte que le train vol _par défaut_ mais, **si** on précise un autre argument (lors de la commande `docker run`), **seuls** ces arguements seront appliqués (les arguments peuvent être cumuler):
   - Pour voler, `sl` a besoin de l'argument `-F`
   - Pour que les gens crient "à l'aide", préciser l'argurment `-a`
   - Pour un petit train, utiliser l'argument `-l`
   - **Attention**, je veux pouvoir utiliser l'argument `-a` ou `-l` sans forcément avoir l'effet du `-F`

> Le tag de cette version de l'image sera `:2nd`

6. En plus du comportement précédent, faites en sorte que le train soit __toujours__ de petite taille, qu'importe les arguments saisis.

> Le tag de cette image sera `:3rd`

## Part 2 Publication d'une image Docker

1. Créer un compte sur le registry Docker-Hub.

2. Créer un nouveau repository dans votre namespace.

3. Publier l'image créé dans la partie 1 dans ce repository (poussez les trois versions de votre image dans le même repository):
   - Vous allez devoir vous logger au registry DockerHub. Utilisez la commande `docker login` pour effectuer cette authentification .
   - Pour créer une nouvelle image/tag, vous pouvez utiliser la commande `docker tag <img_src:tag> <img_dst:tag>`
   - Utiliser la commande `docker push <img:tag>` pour publier votre image sur le registry par défault (docker.hub)

4. Supprimer les image en local.

   `docker rmi <img_name>`

5. Téléchager l'image avec le tag `:3rd`.

6. Vérifier que votre image est toujours fonctionnel.

### Avec l'un de vos voisins

1. Publier l'image avec le tag `:1st` en prenant soin de la tagger en tant que `:latest`

2. Votre voisin télécharge cette image avec le tag `:latest`. Votre voisin doit voir la première version de votre image sur son poste.

3. Publier l'image avec le tag `:3rd` en prenant soin de la tagger avec `:latest`.

4. Que ce passe-t-il si votre voisin rejoue la commande `docker run <image>` sur son poste après que vous ayez pushé la version 3 avec le tag latest. Que faire ?!

> Si vous n'êtes pas sur votre PC personnel, **supprimer** le fichier `~/.docker/config.json` afin de ne pas laisser votre compte sur la machine !


``` bash
# First version (:1st)
sudo docker build -t my-sl-image:1st .

# Second version (:2nd) - flying train by default
sudo docker build -t my-sl-image:2nd .

# Test the versions
sudo docker run --rm -it my-sl-image:1st        # Basic train
sudo docker run --rm -it my-sl-image:2nd        # Flying train (default -F)
sudo docker run --rm -it my-sl-image:2nd -a     # People crying for help (only -a, no -F)
sudo docker run --rm -it my-sl-image:2nd -l     # Small train (only -l, no -F)
sudo docker run --rm -it my-sl-image:2nd -a -l  # Small train + people crying (no -F)
sudo docker tag my-sl-image:2nd zeterack/virtualisation:1.0.1
sudo docker push zeterack/virtualisation:1.0.1
```


