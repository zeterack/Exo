# Exercise 7 - Docker Compose Stack

## Architecture

Cette stack Docker Compose contient :

- **2 sites WordPress** (ports 8080 et 8088)
- **2 bases MySQL distinctes** avec persistance des données
- **1 PHPMyAdmin** (port 8090) configuré pour les 2 bases MySQL
- **1 site Nginx personnalisé** (port 8091) avec HTML intégré

## Services et Ports

| Service | Port | Description |
|---------|------|-------------|
| WordPress 1 | 8080 | Premier site WordPress |
| WordPress 2 | 8088 | Deuxième site WordPress |
| PHPMyAdmin | 8090 | Interface d'administration MySQL |
| Site Custom | 8091 | Page HTML personnalisée |
| MySQL 1 | 3306 | Base de données pour WordPress 1 |
| MySQL 2 | 3307 | Base de données pour WordPress 2 |

## Configuration MySQL

### Base de données 1 (WordPress 1)
- **Host**: mysql1:3306
- **Root Password**: rootpass123
- **Database**: wordpress1
- **User**: wpuser1
- **Password**: wppass123

### Base de données 2 (WordPress 2)
- **Host**: mysql2:3306
- **Root Password**: rootpass456
- **Database**: wordpress2
- **User**: wpuser2
- **Password**: wppass456

## Utilisation

### Démarrer la stack complète
```bash
docker-compose up -d
```

### Arrêter la stack
```bash
docker-compose down
```

### Arrêter et supprimer les volumes (⚠️ Supprime les données)
```bash
docker-compose down -v
```

### Voir les logs
```bash
docker-compose logs -f
```

### Rebuilder le service Nginx personnalisé
```bash
docker-compose build custom_nginx
docker-compose up -d custom_nginx
```

## Accès aux services

Une fois la stack démarrée, accédez aux services via :

- **WordPress 1**: http://localhost:8080
- **WordPress 2**: http://localhost:8088
- **PHPMyAdmin**: http://localhost:8090
- **Site personnalisé**: http://localhost:8091

## PHPMyAdmin - Connexions

PHPMyAdmin est pré-configuré avec les deux serveurs MySQL :

1. **Serveur 1** (mysql1)
   - Utilisateur: `root`
   - Mot de passe: `rootpass123`

2. **Serveur 2** (mysql2)
   - Utilisateur: `root`
   - Mot de passe: `rootpass456`

## Persistance des données

Les données MySQL sont persistées dans des volumes Docker :
- `mysql1_data` : Données du premier serveur MySQL
- `mysql2_data` : Données du deuxième serveur MySQL
- `wordpress1_data` : Fichiers du premier WordPress
- `wordpress2_data` : Fichiers du deuxième WordPress

## Structure des fichiers

```
exo7/
├── docker-compose.yml
├── nginx-custom/
│   ├── Dockerfile
│   └── html/
│       └── index.html
└── README.md
```

## Remarques

- Les deux instances MySQL sont complètement indépendantes
- Les données sont persistées même après redémarrage des conteneurs
- Le site Nginx personnalisé a ses fichiers HTML intégrés à l'image (pas de volumes)
- Tous les services sont connectés via un réseau bridge dédié
