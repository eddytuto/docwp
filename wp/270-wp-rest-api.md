## REST API de WORDPRESS

### Les caractéristiques

###### La REST API de WordPress (WP REST API) est une interface de programmation qui permet d'interagir avec les données de votre site WordPress en utilisant des requêtes HTTP. Voici certaines des caractéristiques clés de la REST API de WordPress :

- Accès aux données : La WP REST API vous permet d'accéder à divers types de données sur votre site WordPress, notamment les articles, les pages, les commentaires, les utilisateurs, les médias, les catégories, les balises, les types de contenu personnalisés, etc.

- Formats de réponse : Les données sont généralement renvoyées au format JSON (JavaScript Object Notation), ce qui les rend faciles à traiter et à utiliser dans des applications Web, des applications mobiles et d'autres services.

- Prise en charge de l'authentification : La WP REST API prend en charge divers mécanismes d'authentification pour sécuriser l'accès aux données, notamment les jetons d'authentification, les identifiants de base, OAuth, etc.

- Points de terminaison (endpoints) : Les points de terminaison de l'API REST correspondent aux différents types de données que vous pouvez manipuler. Chaque type de données a ses propres points de terminaison, et vous pouvez effectuer des opérations CRUD (Create, Read, Update, Delete) sur ces données.

- Personnalisation des points de terminaison : Vous pouvez créer des points de terminaison personnalisés pour exposer des données personnalisées ou des fonctionnalités spécifiques de votre site. Cela se fait généralement en développant des plugins WordPress.

- Simplicité d'utilisation : L'API REST de WordPress est relativement simple à utiliser et à comprendre, même pour les développeurs qui ne sont pas experts en WordPress.

- Documentation intégrée : La documentation de l'API REST est accessible sur votre propre site WordPress. Vous pouvez consulter la documentation en accédant à l'URL de base de votre site suivi de /wp-json, par exemple https://votresite.com/wp-json. La documentation répertorie les points de terminaison disponibles et fournit des informations sur la manière d'effectuer des requêtes.

- Utilisations variées : La WP REST API est utilisée pour créer des thèmes WordPress personnalisés, développer des applications mobiles qui se connectent à un site WordPress, automatiser des tâches telles que la publication d'articles, intégrer des données WordPress dans d'autres systèmes, etc.

- Évolutivité : Vous pouvez développer des applications complexes en utilisant l'API REST de WordPress, ce qui en fait un outil puissant pour des projets de différentes tailles.

En résumé, la REST API de WordPress offre un moyen flexible et puissant d'accéder et de manipuler les données de votre site WordPress, ce qui la rend extrêmement utile pour les développeurs cherchant à étendre les fonctionnalités de WordPress ou à créer des expériences personnalisées pour les utilisateurs.

### Les premiers pas

- Assurez-vous que l'API REST est activée : Par défaut, l'API REST de WordPress est activée. Vous pouvez vérifier cela en vous connectant à l'interface d'administration de WordPress « wp-admin », en allant dans "Réglages" > "Lecture" et en vous assurant que l'option "Autoriser les moteurs de recherche à indexer ce site" est cochée. Cela active l'API REST pour la plupart des fonctionnalités par défaut.

- Tester une première requête REST sur votre navigateur:
  - `https://gftnth00.mywhc.ca/eddy/wp-json/wp/v2/posts?categories=3`
  - `https://gftnth00.mywhc.ca/eddy` Est un site wordpress test contenant la description des cours du TIM
  - `wp-json/wp/v2/posts` : C'est le point de terminaison pour les articles. Il indique à l'API de WordPress que vous souhaitez obtenir une liste des articles. Vous pouvez également remplacer posts par d'autres types de données comme pages pour obtenir la liste des pages.
  - `?categories=3` : Permet d'extraire les articles de catégorie « cours » « 5 » étant le ID de la catégorie « cours »

### Résultats renvoyés

voici une description des grandes lignes de la structure JSON renvoyée par la requête à l'URL https://gftnth00.mywhc.ca/eddy/wp-json/wp/v2/posts?categories=3 :
La structure JSON renvoyée est une collection d'objets, chaque objet représentant un article de votre site WordPress qui appartient à la catégorie avec l'ID 5. Voici les principales parties de cette structure JSON :

- id : C'est l'identifiant unique de l'article.
- date : La date de publication de l'article.
- date_gmt : La date de publication en temps universel coordonné (UTC).
- guid : Un identifiant global unique pour l'article.
- modified : La date de la dernière modification de l'article.
- modified_gmt : La date de la dernière modification en temps universel coordonné (UTC).
- slug : Le slug de l'article, qui est généralement basé sur le titre.
- status : Le statut de l'article (par exemple, "publish" pour un article publié).
- type : Le type de contenu (généralement "post" pour un article).
- link : Le lien URL de l'article.
- title : Un objet contenant le titre de l'article dans différentes versions, notamment le titre brut (non formaté) et le titre formaté pour l'affichage.
- content : Un objet contenant le contenu de l'article, y compris le contenu brut et le contenu formaté.
- excerpt : Un extrait de l'article.
- author : Les détails de l'auteur de l'article, notamment l'identifiant de l'auteur, le nom et d'autres informations.
- featured_media : Les détails du média en vedette associé à l'article, s'il y en a un.
- categories : Les catégories auxquelles l'article est associé. C'est un tableau d'objets contenant des détails sur chaque catégorie.
- tags : Les balises associées à l'article. C'est un tableau d'objets contenant des détails sur chaque balise.
- comment_status : Le statut des commentaires pour l'article (par exemple, "open" pour autoriser les commentaires).
- ping_status : Le statut de ping pour l'article.
- format : Le format de l'article, le cas échéant.

### création d'un plugin pour extraire une liste de cours

Développons un plugin dans le dossier «cours» qui contiendra:

- le fichier cours.php dans la racine du dossier cours
- le dossier js qui contiendra cours.js permettant d'extraire les résultats de la structure JSON
- le fichier style.css

#### Voici le fichier cours.php

```<?php
/**
 * Package Cours
 * Version 1.0.0
 */
/*
Plugin name: Cours
Plugin uri: https://github.com/eddytuto
Version: 1.0.0
Description: Permet d'afficher les cours du TIM
*/
function eddym_enqueue()
{
// filemtime // retourne en milliseconde le temps de la dernière modification
// plugin_dir_path // retourne le chemin du répertoire du plugin
// __FILE__ // le fichier en train de s'exécuter
// wp_enqueue_style() // Intègre le link:css dans la page
// wp_enqueue_script() // intègre le script dans la page
// wp_enqueue_scripts // le hook

$version_css = filemtime(plugin_dir_path( __FILE__ ) . "style.css");
$version_js = filemtime(plugin_dir_path(__FILE__) . "js/cours.js");
wp_enqueue_style(   'em_plugin_carrousel_css',
                     plugin_dir_url(__FILE__) . "style.css",
                     array(),
                     $version_css);

wp_enqueue_script(  'em_plugin_carrousel_js',
                    plugin_dir_url(__FILE__) ."js/cours.js",
                    array(),
                    $version_js,
                    true);
}
add_action('wp_enqueue_scripts', 'eddym_enqueue');
/* Création de la liste de cours en HTML */
function creation_cours(){
    $contenu = '<button class="bouton__ouvrir">Ouvrir</button>
    <div class="cours">
    </div>';
    return $contenu;
}

add_shortcode('em_cours', 'creation_cours');
```

### Voici le fichier cours.js

```
(function () {
  // URL de l'API REST de WordPress
  var url = "https://gftnth00.mywhc.ca/eddy/wp-json/wp/v2/posts?categories=3";

  // Effectuer la requête HTTP en utilisant fetch()
  fetch(url)
    .then(function (response) {
      // Vérifier si la réponse est OK (statut HTTP 200)
      if (!response.ok) {
        throw new Error(
          "La requête a échoué avec le statut " + response.status
        );
      }

      // Analyser la réponse JSON
      return response.json();
      console.log(response.json());
    })
    .then(function (data) {
      // La variable "data" contient la réponse JSON
      console.log(data);

      // Maintenant, vous pouvez traiter les données comme vous le souhaitez
      // Par exemple, extraire les titres des articles comme dans l'exemple précédent
      data.forEach(function (article) {
        var titre = article.title.rendered;
        console.log(titre);
      });
    })
    .catch(function (error) {
      // Gérer les erreurs
      console.error("Erreur lors de la récupération des données :", error);
    });
})();
```

### Adaptation de la requête : https://gftnth00.mywhc.ca/eddy/wp-json/wp/v2/posts?categories=3

Par défaut, l'API REST limite le nombre d'articles renvoyés par page à 10. Pour obtenir tous les articles, y compris les 16 manquants, vous devrez paginer les résultats de la requête.

Pour paginer les résultats et récupérer tous les articles, vous pouvez utiliser le paramètre per_page dans la requête pour spécifier le nombre d'articles à renvoyer par page. Voici comment vous pouvez le faire :

https://gftnth00.mywhc.ca/eddy/wp-json/wp/v2/posts?categories=3&per_page=26
