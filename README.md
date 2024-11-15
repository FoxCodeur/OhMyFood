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

| Dossier/Fichier             | Description                                                        |
|-----------------------------|-------------------------------------------------------------------------------|
| **OhMyFood/**               | Racine du projet                               |
| ├── **assets/**             | Contient les ressources CSS et images          |
| │   ├── **css/**            | Dossier pour le fichier CSS compilé            |
| │   │   └── `style.css`     | Fichier CSS généré après la compilation de Sass|
| │   └── **images/**         | Dossier pour les images                        |
| ├── **node_modules/**       | Dossier pour les modules Node.js installés     |
| ├── **restaurants/**        | Dossier pour les pages des restaurants         |
| ├── **sass/**               | Dossier principal pour tous les fichiers Sass  |
| │   ├── **bases/**          | Styles de base (variables, mixins, etc.)                         |
| │   │   ├── `_reset.scss`   | Réinitialisation des styles par défaut         |
| │   │   ├── `_typographie.scss` | Styles de typographie                      |
| │   │   ├── `_variables.scss` | Fichier de variables                         |
| │   │   └── `_mixins.scss`  | Fichier de mixins                              |
| │   ├── **components/**     | les composants réutilisables                   |
| │   │   ├── `_navigation.scss` | Styles pour la navigation (navbar, menu...) |
| │   │   └── `_button.scss`  | Styles des boutons                             |
| │   ├── **layout/**         | Styles de mise en page                         |
| │   │   ├── `_header.scss`  | Styles pour l'en-tête                          |
| │   │   ├── `_footer.scss`  | Styles pour le pied de page                    |
| │   │   ├── `_forms.scss`   | Styles pour les formulaires                    |
| │   │   └── ...             | Autres styles de mise en page                  |
| │   ├── **pages/**          | Styles spécifiques aux pages                   |
| │   │   ├── `_home.scss`    | Styles pour la page d'accueil                  |
| │   │   ├── `_restaurant.scss` | Styles pour les pages des restaurants       |
| │   │   └── ...             | Autres pages                                   |
| │   ├── **utils/**          | Utilitaires (fonctions, mixins, etc.)          |
| │   │   ├── `_functions.scss` | Fonctions Sass                               |
| │   │   ├── `_mixins.scss`  | Mixins                                         |
| │   │   └── `_variables.scss` | Variables globales                           |
| │   └── `main.scss`         | imports des styles Sass                        |
| ├── `index.html`            | Page d'accueil HTML                            |
| ├── `package.json`          | Fichier pour gérer les dépendances du projet   |
| ├── `package-lock.json`     | les vers des dépendances                       |
| └── `README.md`             | Documentation du projet                        |

3. Configuration du préprocesseur Sass

    Dans ce projet, tu vas organiser ton code Sass de manière modulaire, avec
plusieurs fichiers partiels pour différents aspects du site (réinitialisation 
des styles, typographie, composants, etc.).

    @use "base/_reset";
    @use "base/typographie";
    @use "components/navigation";
    @use "layout/header";
    @use "layout/footer";
    @use "layout/forms";
    @use "pages/home";
    @use "utils/functions";
    @use "utils/mixins";
    @use "utils/variables";

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

Maintenant que ton CSS est compilé, tu dois lier ce fichier dans index.html pour que les styles soient appliqués sur le site internet.

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

Application du style sur le fichier index.html !
    Tout d'abord, il est nécessaire de créer des variables pour définir les différentes tailles de police utilisées sur le site. Ensuite, il faut définir les styles typographiques pour chaque balise impliqué dans des modifications, tels que les titres, les sous-titres et les paragraphes.

Pour chaque niveau de titre et de paragraphe dans le fichier HTML, vous appliquerez les classes appropriées afin d'associer les polices et tailles de texte définies. Cela permet de garantir une typographie cohérente et bien structurée sur l'ensemble du site.  
On nous a donné des informations à propos des polices utilisés sur le site eton sait donc ceci: 

    Logo et titres : Shrikhand
    Texte : Roboto
    
J'ai crée deux variables:
    $font-logo: 'Shrikhand', cursive;
    $font-text: 'Roboto', sans-serif;
Ensuite on crée l'ensemble des mixins.
 Celles qui utilisent flexbox et on les appliquent sur toute la page d'accueil. 
 Celles qui vont être appliquées sur les cards et le bouton explorer nos restaurant. (le bouton commander sur les autres pages)
