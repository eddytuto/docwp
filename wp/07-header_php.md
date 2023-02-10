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
