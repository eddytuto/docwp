### Le fichier header.php

- Le fichier header.php dans un thème WordPress est utilisé pour définir la structure de l'en-tête de votre site.
- Il contient généralement des éléments tels que le titre du site, le logo, la navigation, etc.
- Il est généralement appelé en début de chaque page de votre site, via la fonction **get_header()** dans les fichiers modèle (page.php, single.php, etc.).
- Il est donc un des fichiers les plus important pour la mise en forme de votre site.
- Il permet de définir l'apparence de l'en-tête de chaque page de votre site, et de donner une identité visuelle à votre site.

---

### Quelque fonctions utiles pour le template header.php

- **wp_head()**: Cette fonction permet d'ajouter des scripts et des styles au head de votre site WordPress.
- **bloginfo()** : Cette fonction permet d'afficher des informations sur votre site WordPress, telles que le titre, la description, l'url, etc.
- **the_custom_logo()** : Cette fonction permet d'afficher le logo de votre site WordPress personnalisé, si celui-ci a été configuré.
- **wp_nav_menu()** : Cette fonction permet d'afficher un menu de navigation pour votre site WordPress, en utilisant les menus créés dans l'administration.

### La fonction bloginfo()

- Cette fonction permet de récupérer l'information définie dans le tableau de bord: Réglage/général
- https://developer.wordpress.org/reference/functions/bloginfo/
- Cette fonction permettra d'intégrer dynamiquement le titre du site, la description générale et l'URL d'accès


### La fonction wp_head() 
- Est une fonction clé dans WordPress utilisée pour ajouter des scripts, des balises <meta>, des styles CSS et d'autres éléments dans la section <head> de votre thème WordPress. Cette fonction est généralement appelée dans le fichier header.php de votre thème WordPress et est essentielle pour le bon fonctionnement de nombreux plugins et fonctionnalités.

### Voici ce que fait concrètement la fonction wp_head() :

- Inclusion des balises <meta> : La fonction wp_head() inclut automatiquement certaines balises <meta> nécessaires pour optimiser le référencement (SEO) de votre site, telles que les balises de description, l'encodage des caractères, etc.

- Inclusion des styles CSS : Les feuilles de style (CSS) nécessaires pour le bon fonctionnement de votre thème et de vos plugins sont ajoutées grâce à wp_head(). Ces styles peuvent inclure des styles par défaut de WordPress ainsi que des styles spécifiques à votre thème ou à vos plugins.

- Inclusion des scripts JavaScript : Certains scripts JavaScript sont également ajoutés à l'aide de wp_head(). Cela peut inclure des scripts pour le chargement asynchrone, le suivi des analyses, les fonctionnalités spécifiques du thème ou des plugins, etc.

- Prise en charge des fonctionnalités de plugins : De nombreux plugins WordPress utilisent wp_head() pour ajouter des fonctionnalités spécifiques à la section <head> du site. Par exemple, des plugins de gestion des balises, des plugins de réseaux sociaux, des plugins de suivi d'activité, etc., peuvent ajouter des balises et des scripts via cette fonction.

- Personnalisation avancée : Les développeurs de thèmes et de plugins peuvent également utiliser wp_head() pour ajouter des éléments personnalisés à la section <head> en utilisant des hooks WordPress comme wp_head.

### comment retirer les variables css de couleur « `wp--preset--` »

- https://webgaku.net/wordpress/global-styles-inline-css/#:~:text=Add%20the%20following%20code%20to%20functions.php%20of%20the,are%20using.%20add_action%28%27wp_enqueue_scripts%27%2C%20%27remove_global_styles%27%29%3B%20function%20remove_global_styles%28%29%7B%20wp_dequeue_style%28%27global-styles%27%29%3B%20%7D

- Dans le fichier functions.php ajoutez le code suivant pour retirer le `css global`utiliser par les « `block theme` »
- add_action( 'wp_enqueue_scripts', 'remove_global_styles' );
function remove_global_styles(){
    wp_dequeue_style( 'global-styles' );
}