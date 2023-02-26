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

### Exemple: Entête d'une extension

```
<?php
/**
 *
 * @package Eddy test 1
 * @version 1.0.0
*/
/*
Plugin Name: eddy_test_1
Description: Une extension simple qui ajoute une boîte dans un contenu
Plugin URI: https://referenced.ca
Author: Eddy Martin
Author URI: https://github.com/eddytuto
Version: 1.0.0
*/
/*
La fonction add_shortcode( 'le raccourci' , 'la fonction de rappel')
add_shortcode permet d'associer une fonction de rappel à un raccourci.
Ce raccourci est une espèce de balise qui sera intégré dans le contenu d'une page ou d'un article par l'entremise de l'éditeur de Wordpress. Le raccourci dans le contenu sera intégré en utilisant les crochets [ raccourci ]
https://developer.wordpress.org/reference/functions/add_shortcode/
Voici différents exemple d'utilisation
[ raccourci couleur="red"]
[ raccourci] Contenu [/raccourci]

/* -------------------------------------- */
 */

function genere_html(){
 /////////////////////////////////////// HTML
 // Le conteneur d'une boîte
 $contenu =
 ."<div class='boite'>"
 . "<code>Auteur: " . get_the_author() . "</code>"
 . "<date>Date de publication: " . get_the_date() . "</date>"
 . "<h5>Adresse URL" . get_the_guid() . "</h5>"
 . "<h6>Catégorie: " . get_the_category() . "</h6>"
 . '</div> <!-- fin class="boite" -->';

 return $contenu;
}
add_shortcode('mon_html', 'genere_html');
```
