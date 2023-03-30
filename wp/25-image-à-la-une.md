## Les images à la une
> Wordpress permet d'intégrer les images de différentes façons:
- Sous forme de css background-image:
  - Dans function.php **add_theme_support('custom-background');**
  - `<body class="custom-background site">`
  - Dans functions.php **add_theme_support('custom-logo')**
- Sous forme d'images intégrés directement dans les blocs Gutenberg de Wordpress
  - **Image individuelle**
  - **Galerie d'images**
- Sous forme d'image « mise-en-avant »
  - `the_post_thumbnail();`

### Les post thumbnail
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

