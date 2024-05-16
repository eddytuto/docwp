# Configuration de la galerie Gutenberg

Si l'option de choisir la résolution de l'image n'est pas disponible dans votre éditeur Gutenberg, cela peut être dû à plusieurs raisons, notamment des différences dans les configurations de votre thème ou des plugins installés. Voici quelques étapes pour activer cette option :

1. Vérifier les Paramètres de Média dans WordPress
Accédez à vos réglages médias :
Allez dans le tableau de bord WordPress.
Naviguez vers Réglages > Médias.
Assurez-vous que les tailles de médias sont correctement définies (miniature, moyenne, grande).
2. Utiliser un Plugin pour une Galerie Avancée
Certaines fonctionnalités avancées de gestion d'images peuvent nécessiter l'utilisation d'un plugin. Voici quelques plugins populaires qui peuvent vous aider :

- Envira Gallery :
 - Installez et activez le plugin Envira Gallery.
 - Créez une nouvelle galerie et vous aurez des options pour choisir la résolution des images.

- NextGEN Gallery :
 - Installez et activez le plugin NextGEN Gallery.
 - Créez une galerie et configurez les options d'affichage des images.
 3. Vérifier la Configuration du Thème

### Certains thèmes peuvent personnaliser ou restreindre les options disponibles dans Gutenberg. Pour vérifier cela :

#### Passer à un Thème par Défaut :
- Changez temporairement votre thème actuel pour un thème par défaut comme Twenty Twenty-One.
- Créez une nouvelle galerie et voyez si l'option de résolution d'image apparaît.

#### Ajouter du Code Personnalisé
Si vous êtes à l'aise avec l'ajout de code personnalisé, vous pouvez ajouter une fonctionnalité pour permettre le choix de la résolution dans les galeries :

#### Ajouter du code dans le fichier functions.php de votre thème enfant :

```
function custom_image_size_for_gallery( $sizes ) {

    return array_merge( $sizes, array(

        'thumbnail' => __('Thumbnail'),

        'medium'    => __('Medium'),

        'large'     => __('Large'),

        'full'      => __('Full Size'),

    ));
}

add_filter( 'image_size_names_choose', 'custom_image_size_for_gallery' );
```

#### Vérifier les Paramètres de Gutenberg
Parfois, les options peuvent être masquées dans l'interface utilisateur. Pour vous assurer que tout est bien configuré :

#### Installer le Plugin Gutenberg :
Si vous utilisez l'éditeur par défaut sans le plugin Gutenberg, installez et activez le plugin Gutenberg depuis le dépôt de plugins WordPress.
Cela peut débloquer certaines fonctionnalités supplémentaires.

#### Conclusion
En suivant ces étapes, vous devriez être en mesure d'activer l'option de choisir la résolution des images dans une galerie sur votre site WordPress utilisant Gutenberg. Si après avoir essayé toutes ces options, le problème persiste, il pourrait être utile de contacter le support de votre thème ou de consulter la documentation des plugins utilisés.