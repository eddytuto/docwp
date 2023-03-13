## add_theme_support('custom-background');

la prise en charge de l'arrière-plan personnalisé à votre thème WordPress.

Le premier argument de la fonction add_theme_support() est le type de fonctionnalité que vous souhaitez ajouter, qui dans ce cas est 'custom-background'. Le deuxième argument est facultatif et permet de définir les options pour la fonctionnalité. Dans ce cas, nous avons défini deux options à l'aide du tableau $args :

### Voici les paramètres possibles pour la fonction add_theme_support( 'custom-background' ) :

**default-color** : la couleur d'arrière-plan par défaut en l'absence d'image personnalisée. La valeur par défaut est #ffffff (blanc).
**default-image** : l'image d'arrière-plan par défaut en l'absence de personnalisation. Aucune image n'est définie par défaut.
**default-repeat** : la façon dont l'image d'arrière-plan par défaut est répétée. Les valeurs possibles sont repeat (répéter horizontalement et verticalement), repeat-x (répéter horizontalement) ou repeat-y (répéter verticalement). La valeur par défaut est repeat.
**default-position-x **: la position horizontale de l'image d'arrière-plan par défaut. Les valeurs possibles sont left, center ou right. La valeur par défaut est left.
**default-position-y** : la position verticale de l'image d'arrière-plan par défaut. Les valeurs possibles sont top, center ou bottom. La valeur par défaut est top.
**default-size** : la taille de l'image d'arrière-plan par défaut. Les valeurs possibles sont auto (taille originale), contain (ajuster la taille pour que l'image tienne entièrement dans l'élément parent) ou cover (ajuster la taille pour que l'image remplisse l'élément parent sans se déformer). La valeur par défaut est auto.
