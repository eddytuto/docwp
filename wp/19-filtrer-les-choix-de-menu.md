## Filtrer les choix d'un menu spécifique

> Pour filtrer les choix offerts par un menu spécifique en raccourcissant le nombre de caractères de chacun des choix, vous pouvez utiliser la fonction wp_trim_words de WordPress. Voici un exemple de code que vous pouvez utiliser pour cela :

function custom_menu_item_title($title, $item, $args, $depth) {
    // Remplacer 'nom_de_votre_menu' par l'identifiant de votre menu
    if($args->theme_location == 'nom_de_votre_menu') {
// Modifier la longueur du titre en fonction de vos besoins
$title = wp_trim_words($title, 3, ' ... ');
}
return $title;
}
add_filter('nav_menu_item_title', 'custom_menu_item_title', 10, 4);

Dans ce code, nous utilisons le filtre nav_menu_item_title pour modifier le titre de chaque élément de menu. Nous vérifions d'abord si le menu est le menu spécifique que nous voulons modifier en utilisant $args->theme_location == 'nom_de_votre_menu'. Si c'est le cas, nous utilisons la fonction wp_trim_words pour raccourcir le titre à la longueur désirée.

Assurez-vous de remplacer 'nom_de_votre_menu' par l'identifiant de votre menu et de modifier la longueur du titre en fonction de vos besoins.

Enfin, vous pouvez ajouter ce code dans votre fichier functions.php de votre thème WordPress pour filtrer les choix de menu spécifiques. Les choix de menu seront maintenant raccourcis à la longueur désirée pour le menu spécifique en question.
