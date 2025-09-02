# Exo 6

## Utilisation des volumes

### Information sur PostgreSQL

PostGreSQL, dans une même version majeure, utilise le même filesystem pour stocker ses données.

Donc, la version 11.0 et 11.10  utilise la même structure de fichier pour stocker les données. Ainsi la version 11.0 peut lire des fichiers écrits par la vers 11.10 (et vice-versa).

## ???

1. Démarrer un serveur PG avec l'image `postgres:11.0` et persister ses fichiers de données sur votre machine (voir Docker-Hub pour savoir comment faire). 

   1. Faites le nécessaire pour que l'image démarre.
   2. Vérifier bien que les fichiers de la base sont bien sur votre disque

2. Dans l'instance PG, créer une base de données (si besoin) et une table.

   1. Vous devez faire ceci sans installer le moindre client sur votre poste ! (vous devez directement passer par l'image, en utilisant l'utilitaire `psql`)

   2. Quelques commandes pour PostgreSQL

      ```bash
      psql -U <utilisateur>
      ```

      ```sql
      CREATE DATABASE test;
      \c test # Se connecter à la base "test"
      CREATE TABLE table_name (
         id int
      );
      \dt # Liste les tables
      \l  # Liste les databases
      ```

      

3. Stopper et supprimer votre container.

4. Démarrer, sur le même pointage de montage, l'image `postgres:11.1`

5. Vérifier que vous pouvez retrouver votre database ainsi que la table.

6. Refaire la même même opération pour revenir à l'image `postgres:11.0`

### Question

* Que venez-vous de faire (à l'étape 4) ?
  * Préciser des cas où cela peut être très utile ?

## Docker exec

1. Réaliser un backup de l'instance PG à l'aide de la commande `pg_dump -U postgres <dbName>`
   1. Une one-line-command qui permet de Gzip à la voler puis de stocker le résultat sur le host (utilisation de `| gzip >` )

2. Démarrer une nouvelle instance de PG et charger le dump précédemment réaliser dans cette nouvelle instance
   1. Vérifier que votre import s'est bien réaliser.
