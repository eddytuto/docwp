## Les images à la une (post thumbnail)
> Wordpress permet d'intégrer les images de différentes façons:
- A partir du **customizer**:
  - Sous forme css à partir de la propriété background-image. On ajoute l'option dans function.php **add_theme_support('custom-background');**
  - `<body class="custom-background site">`
  - Sous d'une balise <img>. On ajoute l'option dans functions.php **add_theme_support('custom-logo')**
- Sous forme d'images intégrés directement dans les blocs Gutenberg de Wordpress
  - **Image individuelle**
  - **Galerie d'images**
- Sous forme d'image « mise-en-avant »
  - `the_post_thumbnail();`

### Les post thumbnail
- Ce sont les images-mise-en-avant qui peuvent être dimensionnée en plusieurs grandeur.
- Pour pouvoir intégré une image mise en avant, il faut ajouter une option dans functions.php
  - `add_theme_support( 'post-thumbnails' );`
  - Cet ajout rendra disponible **Image mis en avant** sur l'interface de droite de l'éditeur de wp 
- Pour utiliser l'image en avant dans un modèle nous  utiliseront la fonction
  - `the_post_thumbnail();`
  - Cette fonction permet d'afficher différents formats de l'image à la une définie dans un article ou une page

### Les dimensions par défaut des images « thumbnail »
- `the_post_thumbnail( 'thumbnail' );     // Thumbnail (150 x 150 hard cropped)`
- `the_post_thumbnail( 'medium' );        // Medium resolution (300 x 300 max height 300px)`
- `the_post_thumbnail( 'medium_large' );  // Medium Large (added in WP 4.4) resolution (768 x 0 infinite height)`
- `the_post_thumbnail( 'large' );         // Large resolution (1024 x 1024 max height 1024px)`
- `the_post_thumbnail( 'full' );          // Full resolution (original size uploaded)`

## Références
- https://developer.wordpress.org/themes/functionality/featured-images-post-thumbnails/
- https://developer.wordpress.org/reference/functions/the_post_thumbnail/

