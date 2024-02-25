## Fonctionnalité de recherche

> WordPress offre une fonctionnalité de recherche intégrée qui permet aux utilisateurs de rechercher du contenu sur votre site Web en saisissant des mots clés dans un champ de recherche. Pour ajouter une barre de recherche à votre site WordPress, vous pouvez utiliser un widget de recherche WordPress ou ajouter une fonction de recherche à votre thème WordPress.

---

### la fonction get_search_form()

> Cette fonction **get_search_form()** affichera la barre de recherche par défaut de WordPress. Si vous souhaitez personnaliser la mise en page ou le style de la barre de recherche, vous pouvez modifier le fichier de modèle de recherche de votre thème WordPress en utilisant les balises HTML et CSS appropriées.

---

### Le template searchform.php

> Le fichier **searchform.php** est un modèle de formulaire de recherche dans WordPress qui est utilisé pour afficher la barre de recherche sur votre site web. Ce fichier est utilisé par la fonction get_search_form() pour afficher le formulaire de recherche.
> Le modèle searchform.php par défaut de WordPress est généralement situé dans le répertoire /wp-includes/ du thème utilisé, mais il peut être modifié en le copiant dans votre thème et en le personnalisant selon vos besoins.

---

### Le formulaire de recherche personnalisé

```
<?php
/* Formulaire de recherche personnalisée */
?>
<form class="recherche" role="search" method="get"  action="<?php echo esc_url( home_url( '/' ) ); ?>">
  <label>
    <input class="recherche__input" type="search" class="search-field" placeholder="Search..." value="<?php echo get_search_query(); ?>" name="s" />
  </label>
  <button class="recherche__bouton" type="submit" class="search-submit">
    <span class="recherche__icone">&#x1F50D;</span>
  </button>
</form>
```

---

### search.php

> Le fichier search.php est un fichier de modèle de thème WordPress qui est utilisé pour afficher les résultats de recherche de votre site. Lorsqu'un utilisateur effectue une recherche sur votre site, WordPress utilise le fichier search.php pour générer la page de résultats de recherche correspondante.

> Le fichier search.php définit la structure de la page de résultats de recherche et les éléments qui y sont affichés, tels que le titre de la page, l'extrait du contenu de chaque résultat de recherche et le lien vers la page correspondante. Il peut également inclure des boucles de contenu ou des éléments de navigation, comme des liens vers des pages précédentes ou suivantes des résultats de recherche.

> Le fichier search.php est un fichier de modèle optionnel dans WordPress, ce qui signifie qu'il n'est pas nécessairement présent dans tous les thèmes. Si un thème ne contient pas de fichier search.php, WordPress utilisera le fichier index.php par défaut pour afficher les résultats de recherche.

---

### Un exemple du modèle search.php

```
<?php
/**
 * Modèle de recherche
 */
?>

<?php
get_header();
?>
<main class="site__main">

<section class="recherche__section">
   <?php
   if (have_posts()):
      while(have_posts()): the_post(); ?>
      <article>
         <h5><a href="<?php the_permalink(); ?>"> <?php the_title(); ?></a></h5>
         <?php echo wp_trim_words(get_the_excerpt(), 60) ?>
         <hr>
      </article>
      <?php endwhile; ?>
   <?php endif; ?>
</section>
</main>
<?php
get_footer();
```
