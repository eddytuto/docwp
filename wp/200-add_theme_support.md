# La fonction add_theme_support()

 la fonction **add_theme_support** est utilisée par les **développeurs de thèmes** pour déclarer que leur thème prend en charge certaines fonctionnalités spécifiques. 
 
 ### Cela permet:

**d'activer** diverses **fonctionnalités** intégrées dans WordPress, rendant ainsi le thème compatible avec ces fonctionnalités sans nécessiter de modifications supplémentaires du code de base de WordPress. Voici quelques exemples courants et leur utilité :

### Voici quelques exemples

#### add_theme_support( 'title-tag' )

Utilité: Permet à WordPress de gérer dynamiquement le titre des pages. Cela évite aux développeurs de devoir coder manuellement les balises <title> dans le fichier header.php.


#### add_theme_support( 'post-thumbnails' )

Utilité: Active la fonctionnalité des images à la une pour les articles et les pages. Les utilisateurs peuvent alors définir une image représentative pour chaque publication.

#### add_theme_support( 'custom-logo' )

Utilité: Permet aux utilisateurs de télécharger et de définir un logo personnalisé pour leur site via l'outil de personnalisation de WordPress.


#### add_theme_support( 'html5', array( 'search-form', 'comment-form', 'comment-list', 'gallery', 'caption' ) )

Utilité: Permet au thème d'utiliser des balises HTML5 pour les formulaires de recherche, les formulaires de commentaires, les listes de commentaires, les galeries et les légendes.

#### add_theme_support( 'custom-header' )

Utilité: Permet aux utilisateurs de définir une image d'en-tête personnalisée pour leur site, souvent affichée en haut des pages.


#### add_theme_support('custom-background')

La prise en charge de l'arrière-plan personnalisé à votre thème WordPress.

Le premier argument de la fonction **add_theme_support()** est **le type de fonctionnalité que vous souhaitez ajouter**, qui dans ce cas est **'custom-background'**. **Le deuxième argument est facultatif** et permet de définir **les options** pour la fonctionnalité. Dans ce cas, nous avons défini deux options à l'aide du tableau $args :

### Voici les paramètres possibles pour la fonction add_theme_support( 'custom-background' ) :

```
$defaults = array(
	'default-image'          => '',
	'default-preset'         => 'default', // 'default', 'fill', 'fit', 'repeat', 'custom'
	'default-position-x'     => 'left',    // 'left', 'center', 'right'
	'default-position-y'     => 'top',     // 'top', 'center', 'bottom'
	'default-size'           => 'auto',    // 'auto', 'contain', 'cover'
	'default-repeat'         => 'repeat',  // 'repeat-x', 'repeat-y', 'repeat', 'no-repeat'
	'default-attachment'     => 'scroll',  // 'scroll', 'fixed'
	'default-color'          => '',
	'wp-head-callback'       => '_custom_background_cb',
	'admin-head-callback'    => '',
	'admin-preview-callback' => '',
);
add_theme_support( 'custom-background', $defaults );
```

#### Ajouter la classe « custom-background » dans « body »

- `<body class="custom-background site"`

### Liens importants

- `https://developer.wordpress.org/reference%2Ffunctions%2Fadd_theme_support%2F/`
- `https://developer.wordpress.org/themes/functionality/custom-backgrounds/`
