# Peupler la base de données WP

Insérer le code suivant dans creer_categories_id.php
Ce fichier  doit être sauvegardé dans la racine de votre structure Wordpress.
Elle sera exécutée avec `http:localhost/4w4/creer_categories_id.php`
~~~
<?php
// Charger WordPress
require('wp-load.php');

// Définir les noms des catégories
$categories = array(
    'Aventure',
    'Culturel',
    'Repos',
    'Intime',
    'Sportif',
    'Économique',
    'Luxueux',
    'Paysage',
    'Pleine nature',
);

// Ajouter les catégories à WordPress et récupérer les IDs
$category_ids = array();
foreach ($categories as $category_name) {
    $category_id = $wpdb->get_var("SELECT term_id FROM $wpdb->terms WHERE name = '$category_name'");
    
    if (!$category_id) {
        $wpdb->insert(
            $wpdb->terms,
            array('name' => $category_name, 'slug' => sanitize_title($category_name)),
            array('%s', '%s')
        );

        $category_id = $wpdb->insert_id;
        
        // Assigner la catégorie à la table term_taxonomy
        $wpdb->insert(
            $wpdb->term_taxonomy,
            array('term_id' => $category_id, 'taxonomy' => 'category'),
            array('%d', '%s')
        );
        
        echo "La catégorie '$category_name' a été créée avec l'ID : $category_id<br>";
    } else {
        echo "La catégorie '$category_name' existe déjà avec l'ID : $category_id<br>";
    }

    $category_ids[$category_name] = $category_id;
}

// Afficher les résultats
echo 'Catégories et leurs ID :<br>';
foreach ($category_ids as $category_name => $category_id) {
    echo "$category_name : $category_id<br>";
}
?> 
~~~

### Insérer des articles

Insérer des articles directement dans la table wp_posts de la base de données WordPress via une requête SQL peut être risqué et n'est généralement pas recommandé, car cela peut entraîner des problèmes d'intégrité de la base de données et des erreurs de format.

Cependant, vous pouvez utiliser l'interface de programmation (API) de WordPress pour ajouter des articles de manière sécurisée. Si vous avez accès à l'environnement WordPress, vous pouvez créer un script personnalisé et l'exécuter via le navigateur ou en ligne de commande.

Voici un exemple de script PHP qui utilise l'API WordPress pour ajouter des articles :

Insérer le code suivant dans insert_article.php
Ce fichier  doit être sauvegardé dans la racine de votre structure Wordpress.
Elle sera exécutée avec `http:localhost/4w4/insert_article.php`

~~~
<?php
// Charger WordPress
require('wp-load.php');

// Définir les données des articles
$articles = array(
    // Articles pour la catégorie "Aventure"
    array(
        'post_title' => 'Queenstown, Nouvelle-Zélande',
        'post_content' => 'Queenstown, surnommée la "Capitale de l\'Aventure", est nichée entre des montagnes escarpées et les rives scintillantes du lac Wakatipu...',
        'post_status' => 'publish',
        'post_type' => 'post',
        'post_category' => array(2), // Remplacez 1 par l'ID de la catégorie "Aventure"
    ),
    // Ajouter d'autres articles de la même manière...
    array(
        'post_title' => 'Interlaken, Suisse',
        'post_content' => 'Située entre les lacs de Brienz et de Thoune, Interlaken est un paradis d\'aventure entouré par les majestueuses Alpes suisses. Les amateurs de sensations fortes peuvent s\'essayer au parapente au-dessus des sommets, au canyoning dans les gorges glaciaires ou au saut en parachute avec vue sur l\'Eiger, le Mönch et la Jungfrau. Les sports nautiques sur les lacs alpins et les excursions en téléphérique vers des sommets enneigés offrent une expérience complète. Interlaken est le point de départ idéal pour explorer la région de l\'Oberland bernois.',
        'post_status' => 'publish',
        'post_type' => 'post',
        'post_category' => array(2), // Remplacez 1 par l'ID de la catégorie "Aventure"
    ),
    array(
        'post_title' => 'Costa Rica',
        'post_content' => 'Le Costa Rica, joyau d\'aventures en Amérique centrale, offre une biodiversité étonnante dans un écrin de forêts tropicales. Les aventuriers peuvent s\'engager dans des tyroliennes à travers la canopée, explorer des volcans actifs comme l\'Arenal, et surfer sur les vagues de la côte pacifique. Les sentiers de la réserve de Monteverde mènent à des ponts suspendus offrant des vues spectaculaires sur la canopée. Les amateurs de rafting peuvent affronter les rapides du Pacuare. Le Costa Rica propose une aventure à chaque coin de rue, du Pacifique à la mer des Caraïbes.',
        'post_status' => 'publish',
        'post_type' => 'post',
        'post_category' => array(2), // Remplacez 1 par l'ID de la catégorie "Aventure"
    ),
    array(
        'post_title' => 'Patagonie, Argentine',
        'post_content' => 'La Patagonie argentine, terre de vastes étendues sauvages, offre une aventure brute. Le parc national des Glaciers abrite le célèbre glacier Perito Moreno, où les audacieux peuvent s\'engager dans une excursion de trekking glaciaire. Les montagnes du parc national Nahuel Huapi proposent des randonnées épiques avec des vues imprenables sur les lacs alpins. La région offre également des possibilités de kayak sur des lacs cristallins et des ascensions de sommets majestueux comme le Fitz Roy.',
        'post_status' => 'publish',
        'post_type' => 'post',
        'post_category' => array(2), // Remplacez 1 par l'ID de la catégorie "Aventure"
    ),
    array(
        'post_title' => 'Chamonix, France',
        'post_content' => 'Chamonix, au pied du Mont Blanc, est le paradis des alpinistes et des amateurs de sports extrêmes. Les skieurs peuvent dévaler les pentes de la Vallée Blanche, tandis que les grimpeurs défient les parois rocheuses des Aiguilles de Chamonix. Les amateurs de sensations fortes peuvent s\'essayer au parapente au-dessus des sommets enneigés ou au saut en base jump depuis l\'Aiguille du Midi. Les sentiers de randonnée offrent des vues à couper le souffle sur les Alpes françaises.',
        'post_status' => 'publish',
        'post_type' => 'post',
        'post_category' => array(2), // Remplacez 1 par l'ID de la catégorie "Aventure"
    ),
    array(
        'post_title' => 'Mont Fuji, Japon',
        'post_content' => 'Le Mont Fuji, icône sacrée du Japon, offre une aventure unique entre spiritualité et exploration. Les alpinistes peuvent entreprendre l\'ascension nocturne pour atteindre le sommet au lever du soleil, une expérience spirituelle profonde. Les sentiers autour du mont Fuji mènent à des points de vue panoramiques sur la campagne japonaise. Les lacs voisins, comme le lac Kawaguchi, offrent des croisières paisibles avec le majestueux Fuji en toile de fond.',
        'post_status' => 'publish',
        'post_type' => 'post',
        'post_category' => array(2), // Remplacez 1 par l'ID de la catégorie "Aventure"
    ),
    array(
        'post_title' => 'Banff National Park, Canada',
        'post_content' => 'Le Banff National Park, joyau des Rocheuses canadiennes, est un terrain de jeu pour les amateurs d\'aventure. Les pistes de ski de renommée mondiale à Lake Louise et Sunshine Village attirent les passionnés de sports d\'hiver. Les sentiers de randonnée, comme le Plain of Six Glaciers, offrent des panoramas sur les sommets enneigés. Les activités nautiques sur le lac Moraine et le lac Louise ajoutent une dimension d\'aventure à la beauté naturelle du parc.',
        'post_status' => 'publish',
        'post_type' => 'post',
        'post_category' => array(2), // Remplacez 1 par l'ID de la catégorie "Aventure"
    ),
    array(
        'post_title' => 'Torres del Paine, Chili',
        'post_content' => 'Les Torres del Paine au Chili sont une icône de la Patagonie, offrant une aventure au cœur de paysages spectaculaires. Les randonneurs peuvent parcourir le célèbre circuit du W, passant devant des glaciers, des lacs turquoise et des pics granitiques. Les kayakers peuvent naviguer sur les eaux gelées du lac Grey, tandis que les grimpeurs peuvent s\'attaquer aux sommets imposants des Cuernos del Paine.',
        'post_status' => 'publish',
        'post_type' => 'post',
        'post_category' => array(2), // Remplacez 1 par l'ID de la catégorie "Aventure"
    ),
    array(
        'post_title' => 'Santorin, Grèce',
        'post_content' => 'Santorin, au-delà de ses couchers de soleil romantiques, offre une aventure unique. Les randonneurs peuvent explorer les sentiers côtiers de la caldera, révélant des vues panoramiques sur les villages blancs perchés. Les explorateurs sous-marins peuvent plonger dans les eaux cristallines pour découvrir les vestiges de l\'Atlantide antique, tandis que les amateurs de vent peuvent naviguer autour de l\'île en catamaran.',
        'post_status' => 'publish',
        'post_type' => 'post',
        'post_category' => array(2), // Remplacez 1 par l'ID de la catégorie "Aventure"
    ),
    array(
        'post_title' => 'Yangshuo, Chine',
        'post_content' => 'Yangshuo, avec ses pics karstiques émergeant de la rivière Li, est une toile de fond époustouflante pour une aventure en Chine. Les cyclistes peuvent sillonner les sentiers de campagne entre les rizières et les formations rocheuses. Les croisières sur la rivière Li offrent des panoramas à couper le souffle, tandis que les amateurs d\'escalade peuvent défier les parois karstiques emblématiques.',
        'post_status' => 'publish',
        'post_type' => 'post',
        'post_category' => array(2), // Remplacez 1 par l'ID de la catégorie "Aventure"
    ),
);

// Ajouter les articles à la base de données
foreach ($articles as $article) {
    wp_insert_post($article);
}

echo 'Articles ajoutés avec succès.';
~~~


