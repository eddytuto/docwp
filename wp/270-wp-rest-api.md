## REST API de WORDPRESS

Est une interface de programmation qui permet d'interagir avec la **base de données** de WordPress en utilisant des requêtes **_HTTP_**.

### Les caractéristiques

- Voici certaines des **caractéristiques clés** de la **REST API de WordPress** :

- **Accès aux données** : La WP REST API vous permet d'accéder à divers types de données sur votre site WordPress, notamment les articles, les pages, les commentaires, les utilisateurs, les médias, les catégories, les balises, les types de contenu personnalisés, etc.

- **Formats de réponse** : Les données sont généralement **renvoyées au format JSON** (JavaScript Object Notation), ce qui les rend faciles à traiter et à utiliser dans des applications Web, des applications mobiles et d'autres services.

- Prise en charge de **l'authentification** : La WP REST API prend en charge divers **mécanismes d'authentification** pour sécuriser l'accès aux données, notamment les **jetons d'authentification**, les identifiants de base, OAuth, etc.

- **Points de terminaison (endpoints)** : Les points de terminaison de l'API REST correspondent aux différents types de données que vous pouvez manipuler. Chaque type de données a ses propres points de terminaison, et vous pouvez effectuer des opérations **CRUD (Create, Read, Update, Delete)** sur ces données.

- **Personnalisation des points de terminaison** : Vous pouvez créer des points de terminaison personnalisés pour exposer des données personnalisées ou des fonctionnalités spécifiques de votre site. Cela se fait généralement en développant des plugins WordPress.

- **Simplicité d'utilisation** : L'API REST de WordPress est relativement simple à utiliser et à comprendre, même pour les développeurs qui ne sont pas experts en WordPress.

- **Documentation intégrée** : La documentation de l'API REST est accessible sur votre propre site WordPress. Vous pouvez consulter la documentation en accédant à l'URL de base de votre site suivi de /wp-json, par exemple **https://votresite.com/wp-json**. La documentation répertorie les points de terminaison disponibles et fournit des informations sur la manière d'effectuer des requêtes.

- **Utilisations variées** : La WP REST API est utilisée pour créer des thèmes WordPress personnalisés, développer des applications mobiles qui se connectent à un site WordPress, automatiser des tâches telles que la publication d'articles, intégrer des données WordPress dans d'autres systèmes, etc.

- **Évolutivité** : Vous pouvez développer des applications complexes en utilisant l'API REST de WordPress, ce qui en fait un outil puissant pour des projets de différentes tailles.

En résumé, la REST API de WordPress offre un moyen flexible et puissant d'accéder et de manipuler les données de votre site WordPress, ce qui la rend extrêmement utile pour les développeurs cherchant à étendre les fonctionnalités de WordPress ou à créer des expériences personnalisées pour les utilisateurs.

### Les premiers pas

- Assurez-vous que **l'API REST est activée** : Par défaut, l'API REST de WordPress est activée. Vous pouvez vérifier cela en vous connectant à l'interface d'administration de WordPress « wp-admin », en allant dans "Réglages" > "Lecture" et en vous assurant que l'option "Autoriser les moteurs de recherche à indexer ce site" est cochée. Cela active l'API REST pour la plupart des fonctionnalités par défaut.

- Tester une première requête REST sur votre navigateur:
  - `https://gftnth00.mywhc.ca/tim50/wp-json/wp/v2/posts?categories=3`
  - `https://gftnth00.mywhc.ca/tim50` Est un site wordpress contenant des destinations de voyages
  - `wp-json/wp/v2/posts` : C'est le point de terminaison pour les articles. Il indique à l'API de WordPress que vous souhaitez obtenir une liste des articles. Vous pouvez également remplacer posts par d'autres types de données comme pages pour obtenir la liste des pages.
  - `?categories=3` : Permet d'extraire les articles de catégorie « 3 »

### Résultats renvoyés

Voici une description des grandes lignes de la structure JSON renvoyée par la requête à l'URL https://gftnth00.mywhc.ca/tim50/wp-json/wp/v2/posts?categories=3 :
La **structure JSON** renvoyée est une **collection d'objets**, chaque objet représentant un **article** de votre site WordPress qui appartient à la catégorie avec l'ID 3. Voici les principales parties de cette structure JSON :

- `id` : C'est l'identifiant unique de l'article.
- `date` : La date de publication de l'article.
- `date_gmt` : La date de publication en temps universel coordonné (UTC).
- `guid` : Un identifiant global unique pour l'article.
- `modified` : La date de la dernière modification de l'article.
- `modified_gmt` : La date de la dernière modification en temps universel coordonné (UTC).
- `slug` : Le slug de l'article, qui est généralement basé sur le titre.
- `status` : Le statut de l'article (par exemple, "publish" pour un article publié).
- `type` : Le type de contenu (généralement "post" pour un article).
- `link` : Le lien URL de l'article.
- `title` : Un objet contenant le titre de l'article dans différentes versions, notamment le titre brut (non formaté) et le titre formaté pour l'affichage.
- `content` : Un objet contenant le contenu de l'article, y compris le contenu brut et le contenu formaté.
- `excerpt` : Un extrait de l'article.
- `author` : Les détails de l'auteur de l'article, notamment l'identifiant de l'auteur, le nom et d'autres informations.
- `featured_media` : Les détails du média en vedette associé à l'article, s'il y en a un.
- `categories` : Les catégories auxquelles l'article est associé. C'est un tableau d'objets contenant des détails sur chaque catégorie.
- `tags` : Les balises associées à l'article. C'est un tableau d'objets contenant des détails sur chaque balise.
- `comment_status` : Le statut des commentaires pour l'article (par exemple, "open" pour autoriser les commentaires).
- `ping_status` : Le statut de ping pour l'article.
- `format` : Le format de l'article, le cas échéant.

### création d'un plugin pour extraire une liste de cours

Développons un plugin dans le dossier **« voyage »** qui contiendra:

- le fichier **voyage.php** dans la racine du dossier **voyage**
- le dossier **js** qui contiendra **voyage.js** permettant d'extraire les résultats de la **structure JSON**
- le fichier **style.css**

#### Voici le fichier voyage.php

```<?php
/**
 * Package Cours
 * Version 1.0.0
 */
/*
Plugin name: Voyage
Plugin uri: https://github.com/eddytuto
Version: 1.0.0
Description: Permet d'afficher les destinations qui répondent à certains critères
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
$version_js = filemtime(plugin_dir_path(__FILE__) . "js/voyage.js");
wp_enqueue_style(   'em_plugin_voyage_css',
                     plugin_dir_url(__FILE__) . "style.css",
                     array(),
                     $version_css);

wp_enqueue_script(  'em_plugin_voyage_js',
                    plugin_dir_url(__FILE__) ."js/voyage.js",
                    array(),
                    $version_js,
                    true);
}
add_action('wp_enqueue_scripts', 'eddym_enqueue');
/* Création de la liste des destinations en HTML */
function creation_destinations(){
    $contenu = '<button class="bouton__ouvrir">Ouvrir</button>
    <div class="destination">
    </div>';
    return $contenu;
}

add_shortcode('em_destination', 'creation_destinations');
```

### Voici le fichier voyage.js

```
(function () {
  // URL de l'API REST de WordPress
  var url = "https://gftnth00.mywhc.ca/tim50/wp-json/wp/v2/posts?categories=3";

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

### Adaptation de la requête : https://gftnth00.mywhc.ca/tim50/wp-json/wp/v2/posts?categories=3

Par défaut, l'API REST limite le nombre d'articles renvoyés par page à 10. Pour obtenir tous les articles, y compris les 16 manquants, vous devrez paginer les résultats de la requête.

Pour paginer les résultats et récupérer tous les articles, vous pouvez utiliser le paramètre per_page dans la requête pour spécifier le nombre d'articles à renvoyer par page. Voici comment vous pouvez le faire :

https://gftnth00.mywhc.ca/eddy/wp-json/wp/v2/posts?categories=3&per_page=26

### Comment appeler un « shortcode » à partir d'un modèle

Dans WordPress, vous pouvez appeler un shortcode directement à partir du code d'un modèle tel que front-page.php en utilisant la fonction **_do_shortcode()_**. Voici comment vous pouvez l'utiliser dans votre code :

```
<?php
// Appel du shortcode directement dans le fichier front-page.php
echo do_shortcode('[votre_shortcode]');
?>
```

Remplacez **votre_shortcode** par le **nom de votre shortcode**. Cela exécutera le shortcode et affichera son résultat à l'endroit où vous l'avez placé dans votre fichier **front-page.php**.

### Pour récupérer la bonne adresse adresse d'une image

$image_url = wp_get_attachment_image_url( $image_id, 'full' );

**Pour trouver l'ID d'une image** sur WordPress, vous pouvez suivre ces étapes :

- Dans l'éditeur d'articles/pages : Si vous avez ajouté l'image à un article ou à une page via l'éditeur visuel de WordPress, vous pouvez accéder à l'article ou à la page en mode édition, cliquer sur l'image et voir les détails de l'image dans le panneau de droite. L'ID de l'image sera affiché dans l'URL de la page de modification de l'image.
- Dans la bibliothèque des médias : Accédez à "Médias" dans le menu de votre tableau de bord WordPress, puis cliquez sur "Bibliothèque". Trouvez l'image que vous recherchez dans la liste des médias. Lorsque vous survolez l'image, un lien "Modifier" apparaîtra. Cliquez sur ce lien pour ouvrir la page de modification de l'image où vous pourrez voir l'ID de l'image dans l'URL.
- Dans le code source : Si vous avez accès au code source de votre site WordPress, vous pouvez également trouver l'ID de l'image en inspectant le code HTML de la page où l'image est affichée. Cherchez l'attribut id de l'élément <img> correspondant à l'image. L'ID sera généralement une chaîne de chiffres, par exemple id="attachment_123".
