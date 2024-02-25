## La classe WP_Query()

> La classe WP_Query est une classe de WordPress qui permet de récupérer des publications (articles, pages, types de publications personnalisés, etc.) en fonction de divers critères, tels que les catégories, les balises, les dates, les auteurs, etc.

> Elle est utilisée pour effectuer des requêtes personnalisées sur la base de données WordPress. Avec WP_Query, vous pouvez spécifier un certain nombre de paramètres pour personnaliser la recherche de publications, tels que le type de publication, les catégories, les balises, la date de publication, l'auteur, l'ordre de tri, la pagination, etc.

> WP_Query est utilisé dans de nombreux contextes dans WordPress, tels que la création de modèles personnalisés, la création de pages d'archives, la création de widgets personnalisés, etc.

> En résumé, la classe WP_Query est une fonctionnalité très puissante et flexible de WordPress qui vous permet de récupérer des publications de manière personnalisée, en fonction de critères spécifiques que vous définissez.

### Voici une liste des arguments que l'on peut utiliser avec WP_Query pour personnaliser la recherche de publications :

- post_type : Permet de spécifier le type de publication à récupérer (article, page, etc.) ou un type de publication personnalisé.
- posts_per_page : Permet de spécifier le nombre de publications à afficher par page.
- category_name : Permet de spécifier la catégorie à récupérer en utilisant son slug.
- tag : Permet de spécifier le tag à récupérer en utilisant son slug.
- author : Permet de spécifier l'auteur à récupérer en utilisant son ID.
- post\_\_in : Permet de spécifier une liste d'IDs de publications à récupérer.
- post\_\_not_in : Permet de spécifier une liste d'IDs de publications à exclure.
- orderby : Permet de spécifier le champ selon lequel les publications doivent être triées.
- order : Permet de spécifier l'ordre de tri (ascendant ou descendant).
- paged : Permet de spécifier le numéro de la page à afficher.
- meta_key : Permet de spécifier la clé d'un champ personnalisé à utiliser pour trier les publications.
- meta_value : Permet de spécifier la valeur du champ personnalisé à utiliser pour trier les publications.
- meta_query : Permet de spécifier une requête personnalisée pour les champs personnalisés.
- date_query : Permet de spécifier une requête personnalisée pour les dates de publication.
- tax_query : Permet de spécifier une requête personnalisée pour les catégories et les tags.

### Liste des principales fonctions utilisées avec WP_Query

> Voici une liste des fonctions couramment utilisées avec WP_Query pour récupérer et afficher des publications personnalisées :

- new WP_Query() : Crée une nouvelle instance de la classe WP_Query pour effectuer la recherche de publications.

- have_posts() : Retourne true si des publications sont disponibles dans la boucle de recherche, sinon false.

- the_post() : Définit la publication suivante disponible dans la boucle de recherche pour être utilisée avec les fonctions de template WordPress.

- get_posts() : Récupère un tableau d'objets de publications personnalisées.

- wp_reset_query() : Réinitialise la requête précédente après l'utilisation de WP_Query.

- wp_reset_postdata() : Réinitialise la publication précédente après l'utilisation de the_post.

- get_the_title() : Récupère le titre de la publication actuelle dans la boucle de recherche.

- the_title() : Affiche le titre de la publication actuelle dans la boucle de recherche.

- the_content() : Affiche le contenu de la publication actuelle dans la boucle de recherche.

- the_permalink() : Affiche l'URL de la publication actuelle dans la boucle de recherche.

- the_post_thumbnail() : Affiche l'image vedette de la publication actuelle dans la boucle de recherche.

- get_the_category() : Récupère les catégories de la publication actuelle dans la boucle de recherche.

- the_category() : Affiche les catégories de la publication actuelle dans la boucle de recherche.

- the_tags() : Affiche les tags de la publication actuelle dans la boucle de recherche.

- comments_template() : Affiche le formulaire de commentaire pour la publication actuelle dans la boucle de recherche.

- En utilisant ces fonctions, il est possible de personnaliser l'affichage des publications personnalisées avec une grande flexibilité pour répondre aux besoins spécifiques de votre site.

### Un exemple d'utilisation dans category.php

```
main class="site__main">
   <section class="blocflex">
      <?php
      $category = get_queried_object();
      $args = array(
         'category_name' => $category->slug,
         'orderby' => 'title',
         'order' => 'ASC'
      );
      $query = new WP_Query( $args );
      if ( $query->have_posts() ) :
         while ( $query->have_posts() ) : $query->the_post(); ?>
            <article>
               <h2><a href="<?php the_permalink(); ?>"> <?= get_the_title(); ?></a></h2>
               <p><?= wp_trim_words(get_the_excerpt(), 15) ?></p>
            </article>
         <?php endwhile; ?>
      <?php endif;
      wp_reset_postdata();?>
   </section>
</main>
```

---

### Est-ce qu'il faudrait aventagé l'utilisation de « pre_get_posts » plutôt que créé uune nouvelle instance de WP_Query() pour créer une nouvelle requête

Dans la plupart des cas, il est préférable d'utiliser pre_get_posts plutôt que de créer une nouvelle instance de WP_Query() pour modifier la requête principale de WordPress.

L'utilisation de pre_get_posts permet de modifier la requête principale avant que WordPress ne l'exécute. Cela signifie que WordPress chargera uniquement les éléments qui correspondent aux critères de la requête modifiée, plutôt que de charger tous les éléments et de les filtrer par la suite. Cela peut rendre votre site plus rapide et améliorer ses performances.

D'autre part, l'utilisation d'une nouvelle instance de WP_Query() crée une deuxième requête qui charge tous les éléments avant de les filtrer. Cela peut ralentir votre site et rendre le chargement de la page plus long.

Cependant, il peut y avoir des situations où vous avez besoin de créer une nouvelle instance de WP_Query(), par exemple si vous voulez afficher des éléments spécifiques qui ne sont pas inclus dans la requête principale, ou si vous voulez paginer les résultats d'une manière différente de celle par défaut. Dans ce cas, vous pouvez créer une nouvelle instance de WP_Query() en utilisant les paramètres appropriés.

En résumé, l'utilisation de pre_get_posts est généralement préférable pour modifier la requête principale de WordPress, car cela peut améliorer les performances de votre site. Cependant, il peut y avoir des situations où vous devez créer une nouvelle instance de WP_Query() pour des besoins spécifiques.

### Référence

- https://developer.wordpress.org/reference/classes/wp_query/
