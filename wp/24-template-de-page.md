## Template de page
> Cette structure de thème permet d'associer un modèle à une page. Cette association est visible quand on édite la page à partir de l'éditeur de contenu de Wordpress. L'interface à droite de la zone contenu nous permet de choisir un model parmi plusieurs modèles affiché dans une liste déroulate.

## Le nom du template
- Le nom du fichier **template de page** doit nécessairement débuter avec le mot « **template-** »
- Le deuxième mot du nom doit correspondre au nom qui s'affichera dans la liste déroulate de l'éditeur de contenu
  - `template-evenement.php` 

## Entete du template de page
- Pour que le template de page soit considéré, il faut que l'entête du fichier contienne une directive sous forme d'un commentaire qui contiendra le nom du template.  Par exemple pour le fichier **template-evenement.php**, c'est le mot « **evenement** » qui sera visible dans la liste déroulante.
```
<?php
/**
 * Template name: Evenement
 *
 */
?>
```
### Le code du template de page 
```
<?php get_header(); ?>
<main class="site__main">
<?php
if ( have_posts() ) : the_post(); ?>
<h1><?= get_the_title(); ?></h1>
<?php the_content();?>
<p>L'adresse de l'evénement<?php the_field('adresse'); ?></p>
<p>La date et l'heure de l'événement<?php the_field('date_et_heure_de_levenement'); ?></p>     
<?php endif;?>
</main><!-- #main -->
<?php
get_footer();
```