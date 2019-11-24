# AgenceImmobiliere

Projet d'agence immobilière sous Symfony 4.3.8 pour apprendre à utiliser l'outil. 
Le site permettra à un client de parcourir les biens présentés d'une agence en fonction de ses attentes et pourra alors contacter l'agence pour demander des informations à propos de celui-ci.
Une partie back-office pour l'administrateur lui permettra d'ajouter, modifier ou encore effacer des biens mais encore ajouter une image à celui-ci.

## Installation

Après avoir effectuer une récupération locale des fichiers, il faudra effectuer plusieurs étapes pour permettre au projet de fonctionner :
- Installer les gestionnaires de dépendances : [composer](https://getcomposer.org/download/) ainsi que [yarn](https://yarnpkg.com/fr/docs/install#windows-stable) ou [npm](https://www.npmjs.com/) (au choix).
- Installer le package Symfony Encore
- Installer également **maildev** pour la réception des emails lors du développement.

```
composer install
yarn install
composer require encore
yarn add maildev
```

Une fois les outils installés, il faudra lancer ces commandes pour pouvoir accéder au site.
- Le serveur web locale de Symfony 
- Lance l'environnement de développement de Webpack
- Permet de recevoir et de lire les emails pour le développement

```
php bin/console server:run
yarn run dev-server
maildev
```

## Base de données
Pour ce projet, une base de données MySQL a été choisie. Il faudra donc la créer sous le nom "agenceimmo"
Il faudra également penser à changer, si nécessaire, les identifiants de connexion à la base de données dans le fichier .env à la racine du projet en suivant le modèle mysql://**user**:**password**@**adresse**/agenceimmo. Il est possible de changer le nom de la base de données.
Une fois cette base de données créée, il faudra initialiser les champs dans celle-ci via les commandes suivantes :
```
php bin/console make:migration
php bin/console doctrine:migrations:migrate
```

La structure de la base de données est désormais prête, il est maintenant nécessaire d'hydrater celle-ci. 
Des biens aléatoires vont être crées et un compte administrateur sera également ajouté (email: **admin@admin.fr** & mot de passe: **admin**)
Pour cela, il faut utiliser la commande suivante
```
php bin/console doctrine:fixtures:load
```

> Vivien Frébourg