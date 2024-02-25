## SQL pour insérer plusieurs articles dans la base de données

En somme, l'utilisation d'une requête d'insertion à valeurs multiples est une technique efficace pour insérer plusieurs enregistrements dans une table de base de données en une seule requête, offrant des avantages en termes de temps, de maintenance, de sécurité, d'intégrité des données et de performance.

### Insertion par AUTO_INCREMENT

Lors de la création de la table "wp_posts", il est courant de définir le champ "ID" comme étant de type "INT" avec la clause "AUTO_INCREMENT". Cela signifie que chaque fois qu'un nouvel enregistrement est inséré dans la table, MySQL génère automatiquement un nouvel ID unique pour cet enregistrement.

Par conséquent, si votre table "wp_posts" a été créée avec la clause "AUTO_INCREMENT" pour le champ "ID", vous n'avez pas besoin de spécifier l'ID lors de l'insertion d'un nouvel enregistrement dans la table. En laissant le champ "ID" vide dans la requête d'insertion, MySQL ajustera automatiquement l'ID en utilisant le numéro suivant disponible dans la séquence d'ID.

Par exemple, si votre table "wp_posts" a été créée avec la clause "AUTO_INCREMENT" pour le champ "ID", vous pouvez utiliser la requête d'insertion suivante pour insérer un nouvel enregistrement dans la table, sans spécifier l'ID :

### Exemple de requête INSERT

Par exemple, si votre table "wp_posts" a été créée avec la clause "AUTO_INCREMENT" pour le champ "ID", vous pouvez utiliser la requête d'insertion suivante pour insérer un nouvel enregistrement dans la table, sans spécifier l'ID :

```
INSERT INTO wp_posts (post_author, post_title, post_content, post_status, post_type)
VALUES (1, 'Titre de l\'article', 'Description du cours', 'publish', 'post'),
VALUES (1, 'Titre de l\'article', 'Description du cours', 'publish', 'post');
```

Dans cette requête, le champ "ID" n'est pas spécifié, mais MySQL générera automatiquement un nouvel ID unique pour le nouvel enregistrement.

### sur Visual Code «VSD» pour alterner entre wrap et no-wrap

> [alt]-z

---

### Faire le ménage de la table wp_posts

- Supprimer les révisions d'articles :
  > DELETE FROM wp_posts WHERE post_type = 'revision';
- Supprimer les articles dans la corbeille :
  > DELETE FROM wp_posts WHERE post_type = 'post' AND post_status = 'trash';
- Supprimer les commentaires dans la corbeille :
  > DELETE FROM wp_comments WHERE comment_approved = 'trash';
- Supprimer les commentaires considérés comme spam :
  > DELETE FROM wp_comments WHERE comment_approved = 'spam';
- Supprimer les commentaires non associés à un article :
  > DELETE FROM wp_comments WHERE comment_post_ID = 0;
- Supprimer les données de suivi des liens (pingbacks et trackbacks) :
  > DELETE FROM wp_comments WHERE comment_type = 'pingback';
  > DELETE FROM wp_comments WHERE comment_type = 'trackback';
- Supprimer les métadonnées inutilisées :
  > DELETE FROM wp_postmeta WHERE meta_key = '' OR meta_value = '';
- Optimiser la table des commentaires :
  > OPTIMIZE TABLE wp_comments;
- Notez que ces requêtes doivent être exécutées avec prudence, car elles suppriment définitivement des données de la base de données. Il est recommandé de faire une sauvegarde de la base de données avant de les exécuter.

### En ce qui concerne la gestion des catégories en Wordpress

> Il est fortement recommandé de gérer les catégories d'articles et la taxonomie en général à travers l'interface d'administration de WordPress plutôt que de faire des changements directement dans PHPMyAdmin. Voici quelques raisons pour lesquelles il est préférable d'utiliser l'interface d'administration :

- **Interface utilisateur conviviale** : WordPress offre une interface utilisateur conviviale pour gérer les catégories d'articles et la taxonomie en général. Vous pouvez facilement ajouter, modifier ou supprimer des catégories et des termes de taxonomie en utilisant les options disponibles dans l'interface.

- **Intégration avec le thème et les plugins** : Si vous gérez les catégories d'articles et la taxonomie à travers l'interface de WordPress, cela garantit que tous les thèmes et plugins que vous utilisez sur votre site fonctionneront correctement. En effet, certains thèmes et plugins peuvent utiliser les catégories ou les termes de taxonomie dans leur fonctionnement, et les supprimer directement depuis PHPMyAdmin peut provoquer des erreurs.

- **Vérification des erreurs** : En utilisant l'interface d'administration de WordPress, vous pouvez vérifier les erreurs et les avertissements concernant la gestion des catégories et de la taxonomie. Si vous faites des modifications directement dans PHPMyAdmin, vous risquez de causer des erreurs qui peuvent être difficiles à identifier et à résoudre.

- **En résumé**, il est préférable d'utiliser l'interface d'administration de WordPress pour gérer les catégories d'articles et la taxonomie en général. Cela garantit que votre site fonctionnera correctement et évitera les erreurs potentielles.
