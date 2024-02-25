### Modification de la requête principale de WP

> L'affichage d'une page d'un site Wordpress ce fait à partir d'une requête https qui permettra d'extraire un contenu ciblé de la base de données et d'exécuter un modèle spécifique régis par le diagramme d'exécution d'un template: **https://developer.wordpress.org/themes/basics/template-hierarchy/**. La requête principale de WP est créée par la requête https. La requête principal est une requête mySQL segmenté à l'intérieur de l'objet WP_query. Une fois créée cette requête principale peut être adapté pour modifier l'extration des données

### A quoi sert le hook « pre_get_posts »

> Le hook pre_get_posts est utilisé dans WordPress pour modifier la requête principale de récupération avant qu'elles ne soient exécutées dans la base de données. Ce hook permet aux développeurs de personnaliser les résultats de la requête principale en modifiant les paramètres de la requête avant son exécution.

### L'utilisation du hook pre_get_posts peut être utile pour :

- Modifier le nombre de publications récupérées
- Modifier l'ordre de tri des publications
- Exclure ou inclure des publications basées sur certains critères
- Modifier les paramètres de pagination

### Utilisation pour la page d'accueil

Par exemple, si un développeur souhaite afficher seulement les publications de la catégorie "Nouvelle" sur la page d'accueil, il peut utiliser le **hook pre_get_posts** pour modifier la requête de récupération de publications et inclure uniquement les publications de cette catégorie.

### Cette modification doit se faire dans function.php

```
/**
 * Modifie la requete principale de Wordpress avant qu'elle soit exécuté
 * le hook « pre_get_posts » se manifeste juste avant d'exécuter la requête principal
 * Dépendant de la condition initiale on peut filtrer un type particulier de requête
 * Dans ce cas çi nous filtrons la requête de la page d'accueil
 * @param WP_query  $query la requête principal de WP
 */
function cidweb_modifie_requete_principal( $query ) {
if ( $query->is_home() && $query->is_main_query() && ! is_admin() ) {
  $query->set( 'category_name', 'note4w4' );
  $query->set( 'orderby', 'title' );
  $query->set( 'order', 'ASC' );
  }
 }
 add_action( 'pre_get_posts', 'cidweb_modifie_requete_principal' );
```
