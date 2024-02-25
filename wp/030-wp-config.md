#### Le fichier wp-config.php

- Ce fichier est créé lors de l'**installation initiale de Wordpress**
- Le fichier** wp-config-sample.php** peut être utilisé pour créer nous même le fichier wp-config.php
- **wp-config.php** est un fichier de configuration **de la base de données de WordPress**.
- Il contient les informations de **connexion** à la base de données, telles que le nom d'utilisateur, le mot de passe et le nom de la base de données.
- Contient des paramètres de configuration tels que la **région** et les **clés de sécurité**.
- Il est utilisé pour se **connecter** à la base de données lorsque WordPress est exécuté et pour stocker les données nécessaires au fonctionnement du site.
- Il est important de protéger ce fichier car il contient des **informations sensibles**.

#### Voici quelques paramètres que vous pouvez configurer dans le fichier wp-config.php pour améliorer votre processus de développement sous WordPress :

- Activez le **mode de débogage** en définissant la constante WP_DEBUG sur true :

  - `define( 'WP_DEBUG', true );`
  - Cela affichera les **erreurs** et les **avertissements** dans votre site en développement, ce qui peut être utile pour identifier et corriger les problèmes.

- Désactivez l'éditeur de thème et de plugin en définissant la constante DISALLOW_FILE_EDIT sur true :
  - `define( 'DISALLOW_FILE_EDIT', true );`
  - Cela **empêchera** les utilisateurs de **modifier** les fichiers de votre thème ou de vos plugins via l'interface d'administration de WordPress. Cela peut être utile pour éviter les modifications non intentionnelles pendant le développement.

### configuration des révisions automatiques

- Lorsque vous modifiez un post dans WordPress, une révision de ce post est automatiquement créée pour chaque modification effectuée.
- Si vous souhaitez empêcher la création de ces révisions, vous pouvez ajouter le code suivant à votre fichier **wp-config.php** :

`define( 'WP_POST_REVISIONS', false );`

- Cette ligne de code **désactive** la fonctionnalité de révision de WordPress, empêchant ainsi la création de révisions de post chaque fois que vous modifiez un post existant.
- Notez que cela **ne supprime pas les révisions existantes** pour les posts existants, mais empêchera simplement la création de nouvelles révisions pour les posts existants et futurs.

- Il est également possible de **limiter le nombre de révisions** créées pour chaque post en utilisant la fonction **define()** avec un **nombre entier au lieu de false**. Par exemple, si vous souhaitez limiter le nombre de révisions à 3 :

`define( 'WP_POST_REVISIONS', 3 );`
Cela limitera le nombre de révisions à 3 pour chaque post dans votre site WordPress.

### Pour supprimer les révisions existantes dans WP

- `DELETE FROM wp_posts WHERE post_type = 'revision'`
