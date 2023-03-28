## Les champs personnalisées

### Définitions

- Est une **structure de données** dans WordPress qui permet de stocker des **informations supplémentaires** pour les articles et les pages.
- Plus précisément, les champs personnalisés sont stockés en tant que paires **clé-valeur** dans la table de la base de données de WordPress appelée « **postmeta** ».
- Cette table stocke les **métadonnées** pour chaque article et page WordPress, y compris **les champs personnalisés**.
- Lorsque vous créez un **champ personnalisé**, vous lui donnez un **nom** et vous spécifiez la **valeur à stocker**.
- WordPress stocke ensuite cette information dans la table "**postmeta**" en utilisant la **clé** (nom) que vous avez spécifiée et la **valeur** que vous avez attribuée.
- Cette **structure de données** permet aux développeurs de stocker des informations supplémentaires pour chaque publication et page WordPress, offrant ainsi une grande flexibilité en matière de personnalisation de contenu pour les sites WordPress.


### La base de données de wordpress
https://codex.wordpress.org/images/2/25/WP4.4.2-ERD.png

### Les types de données

Voici une liste de types d'informations que vous pouvez stocker dans des champs personnalisés WordPress :

- **Texte** : vous pouvez stocker du texte tel que des titres, des descriptions, des adresses, des numéros de téléphone, etc.
- **Liens** : vous pouvez stocker des URL de pages web, de fichiers ou d'images externes, ou des liens internes vers d'autres pages WordPress.
- **Images** : vous pouvez stocker des images telles que des photos, des logos, des bannières, etc.
- **Vidéos** : vous pouvez stocker des vidéos intégrées à partir de sites comme YouTube ou Vimeo.
- **Dates** : vous pouvez stocker des dates telles que des dates de publication, des dates d'événements, etc.
- **Nombres** : vous pouvez stocker des nombres tels que des prix, des quantités, des âges, etc.
- **Options** : vous pouvez stocker des options telles que des listes déroulantes, des cases à cocher, des boutons radio, etc.
- **Code HTML** : vous pouvez stocker du code HTML pour des éléments tels que des boutons, des tableaux, des listes, etc.

### La structure de la table wp_postmeta est la suivante:

| meta_id | post_id | meta_key | meta_value |
| ------- | ------- | -------- | ---------- |
| 1       | 100     | field_1  | value_1    |
| 2       | 100     | field_2  | value_2    |
| 3       | 101     | field_1  | value_3    |
| 4       | 101     | field_2  | value_4    |

**meta_id** : identifiant unique de chaque enregistrement dans la table.
**post_id** : identifiant de la publication ou de la page à laquelle les métadonnées sont associées.
**meta_key** : le nom du champ personnalisé créé à l'aide d'ACF.
**meta_value** : la valeur stockée dans le champ personnalisé.

### Extraction avec une requête mySQL

- Pour extraire la valeur d'un champ personnalisé à partir de sa clé (meta key) et d'un post ID spécifique, vous pouvez utiliser la requête SQL suivante :
- `SELECT meta_value FROM wp_postmeta WHERE meta_key = 'nom_de_la_cle' AND post_id = 'id_du_post';`
  Cette requête récupère la valeur (**meta_value**) du champ personnalisé correspondant à la clé (**meta_key**) '**nom_de_la_cle**' et au post ID (**post_id**) '**id_du_post**' dans la table **wp_postmeta** de la base de données WordPress.

### L'extension ACF « Advanced Custom Fields »

- Le plugin le plus populaire des développeurs de thème
- Permet aux utilisateurs de créer des champs personnalisés pour leurs pages, articles et autres types de contenu.
- Permet aux utilisateurs de personnaliser leur contenu en ajoutant des champs pour les images, les vidéos, les liens, les boutons, les boîtes de sélection, les cases à cocher, les champs de texte et bien plus encore.
- L'interface utilisateur d'ACF est facile à utiliser, avec une interface de type glisser-déposer pour ajouter des champs personnalisés à vos pages et articles WordPress.
- En utilisant ACF, les utilisateurs peuvent créer des champs personnalisés sans avoir à écrire de **code personnalisé**, ce qui rend le processus de création de champs personnalisés plus simple et plus rapide.
- ACF dispose également d'une **bibliothèque** de champs personnalisés préconstruits que les utilisateurs peuvent utiliser pour créer des types de champs personnalisés tels que des **cartes Google Maps**, **des choix de couleurs**, des **tableaux**, des **galeries d'images** et bien plus encore.
- Les utilisateurs peuvent également créer leurs propres types de champs personnalisés en utilisant les API d'ACF.

### Exemple d'utilisation

- `<h2><?php the_field('enseignant'); ?></h2>`

### Ressources utiles pour ACF

- Documentation : https://www.advancedcustomfields.com/resources/
- Installer l'extension: https://wordpress.org/plugins/advanced-custom-fields/
- Les premiers pas: https://www.advancedcustomfields.com/resources/getting-started-with-acf/
- Vidéo d'intro à ACF: https://www.youtube.com/watch?v=eMCOE9x5mCc
- Vidéo en français: https://www.youtube.com/watch?v=8yJqolGqWf0
