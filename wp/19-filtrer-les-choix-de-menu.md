## alterner la structure de menu de Wordpress

> Voici une liste de quelques hooks utiles qui peuvent être utilisés pour modifier la structure de menu dans WordPress :

- wp_nav_menu - Ce hook est appelé lorsque le menu est généré, avant que le HTML ne soit renvoyé. Vous pouvez l'utiliser pour modifier la sortie HTML du menu.

- wp_nav_menu_items - Ce hook est appelé lorsque les éléments de menu sont générés, avant que le HTML ne soit renvoyé. Vous pouvez l'utiliser pour modifier les éléments de menu, comme leur nom, leur URL, leur classe CSS, etc.

- wp_nav_menu_objects - Ce hook est appelé lorsque les objets de menu sont récupérés à partir de la base de données, avant que le HTML ne soit renvoyé. Vous pouvez l'utiliser pour modifier les propriétés des objets de menu, telles que leur nom, leur URL, leur classe CSS, etc.

- nav_menu_css_class - Ce hook est appelé lorsqu'une classe CSS est générée pour un élément de menu. Vous pouvez l'utiliser pour ajouter ou supprimer des classes CSS pour les éléments de menu.

- nav_menu_link_attributes - Ce hook est appelé lorsqu'un attribut d'élément de lien HTML est généré pour un élément de menu. Vous pouvez l'utiliser pour ajouter ou supprimer des attributs HTML pour les éléments de menu.

- nav_menu_item_title - Ce hook est appelé lorsqu'un titre d'élément de menu est généré. Vous pouvez l'utiliser pour modifier le titre de l'élément de menu.

- wp_setup_nav_menu_item - Ce hook est appelé lorsqu'un objet de menu est créé pour un élément de menu. Vous pouvez l'utiliser pour modifier les propriétés de l'objet de menu.

- wp_edit_nav_menu_walker - Ce hook est appelé lorsqu'un éditeur de menu est utilisé pour éditer un menu. Vous pouvez l'utiliser pour personnaliser l'apparence et le comportement de l'éditeur de menu.

> Ces hooks peuvent être utilisés pour personnaliser et altérer la structure des menus WordPress en fonction de vos besoins spécifiques.

### Filtrer les choix d'un menu spécifique

> Pour filtrer les choix offerts par un menu spécifique en raccourcissant le nombre de caractères de chacun des choix, vous pouvez utiliser la fonction **wp_trim_words de WordPress**. Voici un exemple de code que vous pouvez utiliser pour cela :

```
function custom_menu_item_title($title, $item, $args, $depth) {
    // Remplacer 'nom_de_votre_menu' par l'identifiant de votre menu
    if($args->theme_location == 'cours') {
// Modifier la longueur du titre en fonction de vos besoins
$title = wp_trim_words($title, 3, ' ... ');
}
return $title;
}
add_filter('nav_menu_item_title', 'custom_menu_item_title', 10, 4);
```

> Dans ce code, nous utilisons le filtre **nav_menu_item_title** pour modifier le titre de chaque élément de menu. Nous vérifions d'abord si le menu est **le menu spécifique que nous voulons modifier** en utilisant **$args->theme_location == 'cours'**. Si c'est le cas, nous utilisons la fonction **wp_trim_words** pour raccourcir le titre à la longueur désirée.

> Assurez-vous de remplacer 'cours' par l'identifiant de votre menu et de modifier la longueur du titre en fonction de vos besoins.

> Enfin, vous pouvez ajouter ce code dans votre fichier **functions.php** de votre thème WordPress pour filtrer les choix de menu spécifiques. Les choix de menu seront maintenant raccourcis à la longueur désirée pour le menu spécifique en question.

### exemple en utilisant le hook **wp_nav_menu_objects**

```
function igc31w_filtre_choix_menu($obj_menu, $arg){
//echo "/////////////////  obj_menu";
// var_dump($obj_menu);
//  echo "/////////////////  arg";
//var_dump($arg);
// die();
    if ($arg->menu == "cours"){
        foreach($obj_menu as $cle => $value)
        {
            //  print_r($value);
            $value->title = substr($value->title,7);
            $value->title = wp_trim_words($value->title,3,"...");
            //echo $value->title . '<br>';
        }
    }
   return $obj_menu;
}
add_filter("wp_nav_menu_objects","igc31w_filtre_choix_menu", 10,2);
```
