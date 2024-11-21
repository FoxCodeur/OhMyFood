# OhMyFood
projet n°4 du cursus d'intégrateur

1. Initialisation du projet ohMyFood
    Initialiser un projet Node.js
    Ouvre un terminal dans ton dossier de projet et exécute la commande suivante: 
`npm init` ou `npm init -y` :

| Commande      | Description |---------------|--------------------------------------------------------------------------------|
| `npm init`    | Lance un guide interactif pour personnaliser le fichier `package.json`.        |
| `npm init -y` | Crée un fichier `package.json` avec des valeurs par défaut (utilisation rapide).|
   
    Installe Sass comme dépendance de ton projet :
    npm install --save-dev sass
    
2. l'arborescence

# OhMyFood

| Dossier/Fichier             | Description                                    |
| **OhMyFood/**               | Racine du projet                               |
| ├── **assets/**             | Contient les ressources CSS et images          |
| │   ├── **css/**            | Dossier pour le fichier CSS compilé            |
| │   │   └── `style.css`     | Fichier CSS généré après la compilation de Sass|
| │   └── **images/**         | Dossier pour les images                        |
| ├── **node_modules/**       | Dossier pour les modules Node.js installés     |
| ├── **restaurants/**        | Dossier pour les pages des restaurants         |
| ├── **sass/**               | Dossier principal pour tous les fichiers Sass  |
| │   ├── **base/**           | Styles de base (animations, reset, typographie)|
| │   │   ├── `_animations.scss` | Animations                                   |
| │   │   ├── `_reset.scss`  | Réinitialisation des styles par défaut         |
| │   │   ├── `_typographie.scss` | Styles de typographie                      |
| │   ├── **components/**     | Composants réutilisables                       |
| │   │   ├── `_button.scss`  | Styles des boutons                             |
| │   │   ├── `_card.scss`    | Styles des cartes                              |
| │   │   ├── `_form.scss`    | Styles des formulaires                         |
| │   ├── **layout/**         | Styles de mise en page                         |
| │   │   ├── `_footer.scss`  | Styles pour le pied de page                    |
| │   │   ├── `_header.scss`  | Styles pour l'en-tête                          |
| │   │   └── `_navigation.scss` | Styles pour la navigation                    |
| │   ├── **pages/**          | Styles spécifiques aux pages                   |
| │   │   ├── `_home.scss`    | Styles pour la page d'accueil                  |
| │   │   └── `_restaurant.scss` | Styles pour les pages des restaurants       |
| │   ├── **utils/**          | Utilitaires (fonctions, mixins, variables)      |
| │   │   ├── `_functions.scss` | Fonctions Sass                               |
| │   │   ├── `_mixins.scss`  | Mixins                                         |
| │   │   └── `_variables.scss` | Variables globales                           |
| │   └── `main.scss`         | Imports des styles Sass                        |
| ├── `index.html`            | Page d'accueil HTML                            |
| ├── `package.json`          | Fichier pour gérer les dépendances du projet   |
| ├── `package-lock.json`     | Fichier des versions des dépendances           |
| └── `README.md`             | Documentation du projet                        |


3. Configuration du préprocesseur Sass

    Dans ce projet, tu vas organiser ton code Sass de manière modulaire, avec
plusieurs fichiers partiels pour différents aspects du site (réinitialisation 
des styles, typographie, composants, etc.).

@use "./utils/variables";
@use "./utils/mixins";
@use "./utils/functions";
@use "./base/reset";
@use "./base/typographie";
@use "./base/animations";
@use "./components/button";
@use "./components/card";
@use "./components/form";
@use "./layout/header";
@use "./layout/navigation";
@use "./layout/footer";
@use "./pages/home";

4. Créer un script de compilation Sass

Maintenant, il faut configurer un script dans ton fichier package.json pour que Sass compile automatiquement les fichiers SCSS en CSS chaque fois qu'il y a une modification.
Dans le fichier package.json, ajoute ce script pour activer la commande sass --watch :

"scripts": {
  "sass:watch": "sass --watch sass/main.scss:assets/css/main.css"
}

Ce script compile sass/main.scss vers assets/css/main.css à chaque fois que tu effectues une modification.

5. Exécuter Sass en mode "watch"

Une fois que tu as configuré le script, ouvre ton terminal dans le répertoire de ton projet et exécute la commande suivante pour démarrer Sass en mode "watch" :

npm run sass:watch

6. Lier le CSS dans ton fichier HTML

Maintenant que le CSS est compilé, tu dois lier ce fichier dans index.html pour que les styles soient appliqués sur le site internet.

Dans ton index.html, ajoute la balise <link> pour inclure le fichier style.css :
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>OhMyFood</title>
    <link rel="stylesheet" href="assets/css/style.css">
</head>

7. Vérification

Maintenant, si tu modifies des fichiers SCSS, par exemple _home.scss dans le dossier sass/pages/, ils devraient être automatiquement compilés et appliqués sur le navigateur.

8. Maintenant que l'arborescence a été créé tu peux copier les deux dossiers images logo et restaurants dans asset/images.

----------------------------------------------------------------------------- 
9. intégration de la librairie fontawesome et ajout des deux font family, Shrikhand et Roboto. 
----------------------------------------------------------------------------

Les branches utilisé pour commiter le projet
    develop-ohmyfood

    Description :
    Cette branche est utilisée comme branche principale pour le développement actif du projet OhMyFood.
    Elle représente un état stable du projet, incluant les nouvelles fonctionnalités, les corrections de bugs, et les mises à jour en cours. C'est à partir de cette branche que d'autres branches spécifiques (fonctionnalités, fixes) sont créées.

    Utilisation :
        Base pour toutes les branches de fonctionnalité (par ex., feature/home-section).
        Fusion de toutes les branches terminées pour unifier le travail.
        Tests intensifs avant de fusionner dans main ou une branche de production.

    feature/home-section

    Description :
    Cette branche est spécifique à une fonctionnalité du projet : la section Home (page d'accueil). Elle sert à développer tout ce qui concerne cette partie, comme les styles SCSS, le HTML de la section, ou toute autre configuration.

    Utilisation :
        Ajouter, modifier ou améliorer les éléments spécifiques à la section d'accueil.
        Tester indépendamment cette fonctionnalité avant de la fusionner dans develop-ohmyfood.
        Référencer cette branche dans les commits pour identifier clairement que le travail concerne la section d'accueil.

    feature/home-section/version-tablet

    Description :
    Cette branche est un sous-dérivé de la branche feature/home-section, dédiée spécifiquement à l'adaptation responsive pour tablettes de la section Home.
    Cela permet de séparer les tâches liées aux différents écrans, facilitant le suivi des modifications et réduisant les risques de conflit dans le code.

    Utilisation :
        Implémenter les media queries et ajuster le CSS ou SCSS pour une version tablette (écrans entre 768px et 1024px par exemple).
        Tester uniquement les changements pour la version tablette, sans toucher aux autres versions (mobile ou desktop).
        Une fois terminé, fusionner cette branche dans feature/home-section, qui sera ensuite fusionnée dans develop-ohmyfood.


----------------------------------------------------------------------------
10. Implémentation de la page d'accueil "OhMyFood"
Structure du fichier index.html

Le fichier HTML de la page d'accueil est organisé de manière à favoriser une navigation claire et un design responsive, en suivant une approche mobile-first. Voici la structure principale de ce fichier :

    <header> :
        Contient le logo de l'application, placé dans un div avec la classe .header__logo.

    <main> :
        Composé de plusieurs sections qui structurent le contenu de la page d'accueil.

    Sections principales :
        <section class="location"> : Affiche un icône et la localisation actuelle.
        <section class="intro"> : Contient le titre principal, un sous-titre et un bouton pour explorer les restaurants.
        <section class="steps"> : Décrit le processus en trois étapes, avec des informations claires sur comment utiliser le service.
        <section class="restaurants"> : Affiche une liste de restaurants sous forme de cartes cliquables.

    <footer> :
        Contient le logo de l'application et une liste de liens de navigation, dont des liens vers des pages comme "Proposer un restaurant", "Mentions légales", etc.

Élément ajouté dans le <head>

Dans la section <head> du fichier, plusieurs éléments ont été ajoutés pour optimiser le chargement des ressources et garantir un affichage cohérent sur tous les appareils : 
<!-- Préconnexion pour optimiser le chargement des polices Google -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>

<!-- Polices Google : Shrikhand et Roboto -->
<link
    href="https://fonts.googleapis.com/css2?family=Shrikhand&family=Roboto:ital,wght@0,300;0,400;0,500;0,700;1,300;1,400;1,500;1,700&display=swap"
    rel="stylesheet">

<!-- Font Awesome pour les icônes -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.2.1/css/all.min.css"
    integrity="sha512-MV7K8+y+gLIBoVD59lQIYicR65iaqukzvf/nwasF0nqhPay5w/9lJmVM2hMDcnK1OnMGCdVK+iQrJ7lzPJQd1w=="
    crossorigin="anonymous" referrerpolicy="no-referrer">

<!-- Lien vers le fichier CSS compilé -->
<link rel="stylesheet" href="assets/css/main.css">

Application du style général sur le fichier index.html !
    Tout d'abord, il est nécessaire de créer des variables pour définir les différentes tailles de police utilisées sur le site. Ensuite, il faut définir les styles typographiques pour chaque balise impliqué dans des modifications, tels que les titres, les sous-titres et les paragraphes.

    Pour chaque niveau de titre et de paragraphe dans le fichier HTML, vous appliquerez les classes appropriées afin d'associer les polices et tailles de texte définies. Cela permet de garantir une typographie cohérente et bien structurée sur l'ensemble du site.  
    
    On nous a fournis des informations à propos des polices utilisés sur le site et on sait donc ceci: 

    Logo et titres : Shrikhand
    Texte : Roboto
    
J'ai crée deux variables:
    $font-logo: 'Shrikhand', cursive;
    $font-text: 'Roboto', sans-serif;
Ensuite on crée l'ensemble des mixins. (pour tous les cas de flexbox mais aussi les 4 boutons), et les mixins media queries.
 Les flexbox s'appliquent sur toute la page d'accueil.

 Notice de création des composants

Cette section détaille la création des composants pour le formulaire et les boutons de la page d'accueil.

    Formulaire de la section "Location"
    Implémentation d'un formulaire avec un champ de saisie (input) pour la recherche de ville, accompagné d'une icône de localisation.

    Boutons de la page d'accueil
        Un bouton d'ancre situé dans l'introduction, permettant une navigation rapide.
        Trois boutons supplémentaires intégrés dans la section "Steps".

Étapes de réalisation

    Étape 1 : Structure HTML
    Mise en place de la structure HTML pour le formulaire et les boutons.

    Étape 2 : Styles CSS
    Application des styles en utilisant des mixins, des variables, et des classes CSS pour harmoniser le design des boutons.

------------------------------------------------------------------------------------
Mise en place des pages restaurants.

