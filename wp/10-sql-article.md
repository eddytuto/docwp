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
