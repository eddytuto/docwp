# Sass

## Sass définition:
- Sass (Syntactically Awesome Stylesheets) est un préprocesseur CSS qui étend la syntaxe du langage CSS en y ajoutant des fonctionnalités telles que les 
    - variables, 
    - les règles imbriquées, 
    - les mixins, 
    - les imports, 
    - les opérations mathématiques, etc. 
    - L'objectif principal de Sass est de rendre le processus de développement CSS plus efficace, plus organisé et plus maintenable.

## Caractéristiques clés de Sass :

    - Variables : Sass permet de définir des variables pour stocker des valeurs réutilisables. Cela facilite la gestion des couleurs, des tailles de police et d'autres propriétés à travers le code.

    scss

$couleurPrincipale: #3498db;

body {
  color: $couleurPrincipale;
}

## Règles imbriquées : Les sélecteurs CSS peuvent être imbriqués pour refléter la hiérarchie du HTML, rendant le code plus lisible et évitant la répétition.

scss

nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;

    li { display: inline-block; }
  }
}

## Mixins : Les mixins permettent de définir des ensembles de propriétés et de les réutiliser dans plusieurs endroits du code.

scss

@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
  -moz-border-radius: $radius;
  border-radius: $radius;
}

button {
  @include border-radius(5px);
}

Imports : Sass offre la possibilité d'importer des fichiers Sass dans d'autres fichiers, permettant ainsi de mieux organiser le code en modules.

scss

// _variables.scss
$couleurPrincipale: #3498db;

// main.scss
@import 'variables';

body {
  color: $couleurPrincipale;
}

## Opérations mathématiques : Sass permet d'effectuer des opérations mathématiques directement dans le code CSS.

scss

    $largeur: 100%;
    $colonnes: 3;

    .colonne {
      width: $largeur / $colonnes;
    }

Sass offre ces fonctionnalités pour améliorer la lisibilité, la maintenabilité et la réutilisabilité du code CSS. Une fois le code écrit en Sass, il est généralement compilé en CSS standard pour être utilisé dans les navigateurs web. Le fichier Sass peut avoir l'extension .sass ou .scss, mais la syntaxe la plus couramment utilisée est .scss, qui est plus proche de la syntaxe CSS standard.
