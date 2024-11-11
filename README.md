# OhMyFood
projet n°4 du cursus d'intégrateur

1. Initialisation du projet ohMyFood
    Initialiser un projet Node.js
    Ouvre un terminal dans ton dossier de projet et exécute la commande suivante: 
Voici un tableau comparatif des commandes `npm init` et `npm init -y` :

| Commande      | Description |---------------|--------------------------------------------------------------------------------|
| `npm init`    | Lance un guide interactif pour personnaliser le fichier `package.json`.        |
| `npm init -y` | Crée un fichier `package.json` avec des valeurs par défaut (utilisation rapide).|
   
    Installe Sass comme dépendance de ton projet :
    npm install --save-dev sass
    
2. arborescence du projet

    Voici la structure du projet :
# Structure du projet OhMyFood

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

3. Configuration de Sass

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

Maintenant, tu peux configurer un script dans ton fichier package.json pour que Sass compile automatiquement tes fichiers SCSS en CSS chaque fois qu'il y a une modification.
Ajouter un script de compilation Sass

Dans le fichier package.json, ajoute ce script pour activer la commande sass --watch :

"scripts": {
  "sass:watch": "sass --watch sass/main.scss:assets/css/style.css"
}

Ce script compile sass/main.scss vers assets/css/style.css à chaque fois que tu effectues une modification.

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

Maintenant, si tu modifies des fichiers SCSS, par exemple _home.scss dans le dossier sass/pages/, ils devraient être automatiquement compilés et appliqués sur ton site.

-------------------------------------------------------------------------------
