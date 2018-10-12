# WP-New

Ce dépôt est pour la création du projet WordPress.

> La description des étapes a été inspiré de la [formation d'O'clock](https://oclock.io) avec des modifiactions personnel.

## Description des étapes

### Etape 1 - Composer

Après l'importation du dépôt, faire un : `composer install`

Afin d'installer WordPress!

### Etape 2 - PhpMyAdmin

Créer la base de donnée.

### Etape 3 - WP-config.php

Copier le fichier `wp-config-sample.php` en le renommant `wp-config.php` et y saisir les informations concernant la base de donnée (Nom de la bdd, user, password).

De plus, [récupérer le salt](https://api.wordpress.org/secret-key/1.1/salt/) et le saisir sur ce fichier.

Modifier l'adresse du site :

```
define( 'WP_CONTENT_URL', 'http://monurl.local/module' );
define( 'WP_CONTENT_DIR', dirname( ABSPATH ) . '/module' );
```

### Etape 4 - Droits des fichiers/dossiers

`<user>` : Votre utilisateur courant

à la racine du projet :

**sur Linux :**
```
sudo chown -R <user>:www-data .
sudo find . -type f -exec chmod 664 {} +
sudo find . -type d -exec chmod 775 {} +
``` 
De plus, il faut modifier également le fichier `.htaccess` en ne donnant aucun droit à apache l'empêchant ainsi d'être modifié avec : `sudo chown <user>:<user> .htaccess`


### Etape 5 - Lancer votre WordPress

Vous pouvez lancer l'installer de WordPress.

Celui-ci va initier votre base de données et tout ce qui suit. Sélectionner la langue, les paramètres et penser à empêcher l'indexation du site, le temps de la conception du projet. Il pourra être activé plus tard.

**Dans réglages->Général :**

Modifier *Adresse web du site(URL)* sans **WP**

### Informations

#### A - Plugins & themes

Pour le téléchargement de **plugins** ou de **themes**, il est **important** de renseigner le fichier `composer.json` au niveau de *require*. 
Dans ce dépôt, ceci est un exemple :
```
    "wpackagist-theme/twentyseventeen": "*",
    "wpackagist-theme/hueman": "*",
    "wpackagist-plugin/jetpack": "^6.1"
```
plus d'informations sur [https://wpackagist.org](https://wpackagist.org/)

#### B - La suite

Ce dépôt est évolutif pendant la formation