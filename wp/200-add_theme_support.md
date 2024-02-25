## add_theme_support('custom-background');

la prise en charge de l'arrière-plan personnalisé à votre thème WordPress.

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

### Ajouter la classe « custom-background » dans « body »

- `<body class="custom-background site"`

### Liens importants

- `https://developer.wordpress.org/reference%2Ffunctions%2Fadd_theme_support%2F/`
- `https://developer.wordpress.org/themes/functionality/custom-backgrounds/`
