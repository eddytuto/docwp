[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://github.com/codespaces/new?hide_repo_select=true&ref=main&repo=0000000&machine=premiumLinux&devcontainer_path=.devcontainer%2Fdevcontainer.json&location=WestUs2)

## Les extensions Wordpress

> Une extension WordPress, également connue sous le nom de **plugin** WordPress, est un logiciel tiers qui peut être ajouté à un site Web WordPress existant pour ajouter des **fonctionnalités supplémentaires** ou **modifier son comportement**. Les extensions peuvent être utilisées pour ajouter des fonctionnalités telles que des **formulaires de contact**, des **galeries** d'images, des fonctionnalités de **commerce électronique**, des **fonctionnalités de réseaux sociaux** et bien plus encore.

> Les extensions sont souvent développées par des tiers et sont disponibles gratuitement ou moyennant des frais sur le répertoire d'extensions officiel de WordPress ou sur des sites tiers. Les extensions sont facilement installées et activées depuis le tableau de bord de WordPress, et elles peuvent être désactivées ou supprimées à tout moment si nécessaire.

---

### Choisir une extension

- L'extension est **indépendante du thème**.
- L'extension peut être très **simple quelques lignes de codes** ou très complexe **plusieurs milliers de lignes de code**.

  - Par exemple **woocommerce** est une extension permettant de développer un site de **e-com** sur **Wordpress**. Cette extension **dépasse Wordpress** en terme de **nombre de lignes**. Wordpress en contient autour **380000** et woocommerce **500000**
  - ***https://woocommerce.com/***

---

### Comment choisir une extension:

- Elle doit avoir été **testé et validé par la communauté WP**
- Elle doit se trouver dans le **répertoire** des extensions de wordpress.org
- Avant d'installer une extension vérifier quelques **statistiques** et **commentaires**:
  - Nombre d'installations actives
  - Niveau de l'appréciation des utilisateurs

---

### Type d'extensions

> Il existe plusieurs types d'extensions et on trouve des extensions dans plusieurs domaines d'applications. En voici quelques exemples:

- **Sécurité:**
  - https://wordpress.org/plugins/search/security/
- **Sauvegarde de sécurité et redéploiement**
  - https://wordpress.org/plugins/search/backup/
  - https://www.akeeba.com/products/akeeba-backup-wordpress.html
- **Gestion des champs personnalisés**
  - https://wordpress.org/plugins/search/custom+field/
  - La bonne version de ACF
  - Advanced Custom Fields – WordPress plugin | WordPress.org
- **Création de formulaire**
  - https://wordpress.org/plugins/search/form/
- C**ourriel et news letters**
  - https://wordpress.org/plugins/search/email/
- **Sondage quiz**
  - https://wordpress.org/plugins/search/survey/

---

### La structure d'une extension

> Une extension WordPress est généralement structurée comme suit :

- **Fichier principal** : Il s'agit du fichier principal de l'extension, qui définit le nom, la description, la version et les autres informations de base de l'extension.

- **Fichier d'initialisation** : Ce fichier est responsable de l'initialisation de l'extension et de l'enregistrement des fonctions de l'extension.

- **Dossier "includes"** : Ce dossier contient les fichiers PHP qui fournissent les fonctionnalités principales de l'extension.

- **Dossier "assets"** : Ce dossier contient les fichiers tels que les images, les styles CSS et les scripts JavaScript qui sont utilisés par l'extension.

- **Fichier de configuration** : Ce fichier permet à l'utilisateur de personnaliser les paramètres de l'extension.

- **Fichier de traduction** : Ce fichier contient les traductions de l'extension dans différentes langues.

- **Fichier de licence** : Ce fichier contient les informations sur la licence de l'extension.
- **https://wordpress.org/plugins/**

---

### Peut-on trouver des extensions d'un seul fichier?

> Oui, il est possible de créer une extension WordPress qui se compose d'un seul fichier. Cela est particulièrement utile pour des extensions simples qui fournissent des fonctionnalités très spécifiques ou pour des extensions destinées à un usage personnel.

> Cependant, il est important de noter que cette méthode de développement n'est pas recommandée pour des extensions plus complexes ou destinées à une utilisation plus générale. En effet, une extension plus complexe pourrait nécessiter plusieurs fichiers pour une meilleure organisation et une meilleure maintenance du code.

> De plus, les extensions les plus courantes sur le répertoire d'extensions officiel de WordPress sont généralement plus élaborées et fournissent un meilleur support à long terme, une documentation complète, des mises à jour de sécurité, et d'autres avantages pour les utilisateurs. Il est donc recommandé de suivre les meilleures pratiques de développement des extensions WordPress pour créer des extensions de qualité et maintenables à long terme.

---

### Concevoir une extension

- Toutes les extensions WP se trouvent dans le dossier content/plugin
- Chaque extension est préférablement contenu dans un dossier qui permettra d'organiser l'extension en sous-dossiers
- Le nom du **programme principale** de l'extension **doit être le même** que celui du **dossier parent**
- **L'entête du fichier principale** d'une extension ressemble à l'entête du fichier **style.css**
- Le guide du développeur de Wordpress
  - > https://developer.wordpress.org/plugins/
- Description de l'entête d'une extension
  - > https://developer.wordpress.org/plugins/plugin-basics/header-requirements/

---

### Voici un exemple d'une extension en un seul fichier

> Voici un exemple très simple d'une extension WordPress en un seul fichier qui ajoute un shortcode pour afficher un message personnalisé sur une page ou un article :

```
<?php
/**
 * Plugin Name: Mon Extension Simple
 * Description: Ajoute un shortcode pour afficher un message personnalisé.
 * Version: 1.0.0
 * Author: Moi-même
 * Author URI: https://monsite.com/
 */

function mon_shortcode() {
    return 'Bonjour, ceci est un message personnalisé.';
}
add_shortcode( 'mon_message', 'mon_shortcode' );
?>
```

---

### Exemple: Extension simple

> add_shortcode( 'le raccourci' , 'la fonction de rappel')

- un peut comme add_action(), add_filter() ou en js comme add_event_listener()
- add_shortcode est une fonction qui permet d'associer une fonction de rappel à un raccourci.
- Ce raccourci est une espèce de balise qui sera intégré dans le contenu d'une page ou d'un article par l'entremise de l'éditeur de Wordpress. Le raccourci dans le contenu sera intégré en utilisant les crochets [ raccourci ]
- https://developer.wordpress.org/reference/functions/add_shortcode/
- Voici différents exemple d'utilisation
- [ raccourci couleur="red"]
- [ raccourci] Contenu [/raccourci]

```
<?php
/**
 *
 * @package Eddy test 1
 * @version 1.0.0
*/
/*
Plugin Name: boite simple
Description: Une extension simple qui ajoute une boîte dans un contenu
Plugin URI: https://referenced.ca
Author: Eddy Martin
Author URI: https://github.com/eddytuto
Version: 1.0.0
*/
/*

function genere_html(){
 /////////////////////////////////////// HTML
 // Le conteneur d'une boîte
 
    $contenu = '<button class="bouton__ouvrir">Ouvrir</button>
    <div class="carrousel">
    <button class="carrousel__x">X</button>
    <figure class="carrousel__figure"></figure>
    <form class="carrousel__form"></form>
    </div>';
    return $contenu;

 return $contenu;
}
add_shortcode('mon_html', 'genere_html');
```

### Création de l'extension carrousel

> Création de la galerie

- L'extension permettra d'afficher **une à une les images agrandies d'une galerie**.
- La galerie sera créée à partir d'**un bloc « Gallery » de l'éditeur Guthenberg de Wordpress**
- À partir de l'éditeur à l'intérieur du bloc «**gallery**»
- Pour sélectionner la galerie il faut **cliquer entre deux images**
- Sélectionner « **avancée** » ensuite « **class CSS additionnelle** »
- Entrer la class addtionnelle « **galerie** »

> La structure de dossier de l'extension

- L'extension est contenu dans un dossier « carrousel »
- carrousel (le dossier principal de l'extension)
  - js (le dossier du code javascript)
  - sass (le dossier des fichiers scss)
  - style.css (le fichier css compilé par Sass)
  - carrousel.php (le fichier principal de l'extension qui doit avoir le même nom que le dossier principal )

> Le fichier carrousel.php

- L'entête du fichier doit contenir une **description** de l'extension
- Cette description ressemble à la description du **fichier style.css d'un thème**
- La description est un commentaire situé entre /\*\* ... \*/
- Voici les principales propriétés que doit contenir la description
  - **Plugin name: Carrousel**
  - **Author: Eddy Martin**
  - **Plugin URI: https://github.com/eddytuto**
  - **Description: Permet d'afficher une à une les images d'une galerie guthenberg**
  - **Version: 1.0.0**

> carrousel.php: inclusion du fichier **style.css** et du fichier **carrousel.js**

- Comme pour un thème il faut inclure les fichier .css et .js.
- Nous utiliserons les fonctions:
  - **filemtime()** // retourne en milliseconde le temps de la dernière sauvegarde
  - **plugin_dir_path()** // retourne le chemin du répertoire du plugin
  - **\_\_FILE\_\_** // une constante contenant le chemin du fichier en train de s'exécuter
  - **wp_enqueue_style()** // Intègre le link:css dans la page
  - **wp_enqueue_script()** // intègre le script dans la page
  - **wp_enqueue_scripts** // le hook qui permettra d'enfiler le css et le script

> carrousel.php: Évaluation des numéros de version des fichier .css et .js

- $version_css = filemtime(plugin_dir_path( **\_\_FILE\_\_** ) . "style.css");
- $version_js = filemtime(plugin_dir_path(**\_\_FILE\_\_**) . "js/carrousel.js");

> carrousel.php: Enfilement des **fichiers .css et .js** dans la page du site

```
    wp_enqueue_style(   'em_plugin_carrousel_css',
                     plugin_dir_url(__FILE__) . "style.css",
                     array(),
                     $version_css);

    wp_enqueue_script(  'em_plugin_carrousel_js',
                    plugin_dir_url(__FILE__) ."js/carrousel.js",
                    array(),
                    $version_js,
                    true);
```

> carrousel.php: **la fonction de rappel** pour executer les **fonctions d'enfilement**

- **add_action('wp_enqueue_scripts', 'eddym_enqueue');**

> carrousel.php: Création de la boîte qui contiendra le carrousel

- **function creation_carrousel()**
- Le code HTML à retourner

```
<button class="bouton__ouvrir">Ouvrir</button>
    <div class="carrousel">
    <button class="bouton__x">X</button>
    <figure class="carrousel__figure"></figure>
    <form class="carrousel__form"></form>
    </div>';
```

- **add_shortcode('em_carrousel', 'creation_carrousel');**

> **Création du fichier carrousel.js**

- **Les étapes** pour créer un carrousel d'image
- **L'étape 1** récupère la galerie d'images et l'image de plus haute résolution en utilisant les sélecteurs CSS querySelector et querySelectorAll.

- **L'étape 2** récupère les éléments HTML nécessaires pour créer la boîte modale du carrousel, tels que l'élément figure et le bouton de fermeture.

- **L'étape 3** parcourt les images de la galerie pour les ajouter au carrousel en créant dynamiquement les éléments DOM nécessaires à l'aide de createElement, en récupérant l'adresse http de l'image dans l'attribut "src" et en l'ajoutant à la figure.

- Ensuite, **des radio boutons sont créés dynamiquement** pour permettre à l'utilisateur de naviguer entre les images. Les radio boutons sont également liés à l'événement mousedown pour permettre à l'utilisateur de cliquer dessus et de faire apparaître l'image correspondante dans le carrousel.

- Enfin, **l'étape 4** gère l'ouverture et la fermeture de la boîte modale du carrousel en ajoutant ou en supprimant la classe **carrousel--ouvrir** à l'élément HTML correspondant **lorsqu'un bouton est cliqué**.

### Les étapes de développement du carrousel

- Ouvrir la boîte modale « carrousel » avec un bouton temporaire
- Fermer la boîte modale avec le « bouton\_\_x » du carrousel
- l'ouverture de la boîte modale se fait en ajoutant la classe « carrousel--activer »
- La fermeture de la boîte modale se fait en retirant la classe « carrousel--activer »
- La boîte modale est animé avec la transformation « scale » on applique une transition à la propriété « transform »
