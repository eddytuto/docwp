# Fusionner deux dépôts ensemble

Pour intégrer les dépôts **tp2** et **carrousel** dans un seul dépôt à l'intérieur de **wp-content** sous les chemins **wp-content/themes/tp2** et **wp-content/plugins/carrousel**, vous pouvez utiliser les **sous-modules Git**. 
Voici les étapes détaillées :

## Étapes pour intégrer les dépôts comme sous-modules


### Créer le dépôt principal :

- Dans le dossier **wp-content** créer un dépôt
- `git init`

### Ajouter les sous-modules :

- Ajoutez les dépôts existants tp2 et carrousel en tant que sous-modules dans les chemins spécifiés.
- **Ajouter le thème en tant que sous-module**
- `git submodule add https://github.com/utilisateur/theme-tp2.git wp-content/themes/tp2`
- **Ajouter le plugin en tant que sous-module**
- `git submodule add https://github.com/utilisateur/plugin-carrousel.git wp-content/plugins/carrousel`

### Initialiser et mettre à jour les sous-modules :

Initialisez les sous-modules et mettez-les à jour pour qu'ils pointent vers le bon commit.

- `git submodule init`
- `git submodule update`

### Valider les modifications :

Validez les changements dans le dépôt principal pour inclure les références aux sous-modules.

- `git add .`
- `git commit -m` 
- "Ajout des sous-modules pour le thème tp2 et le plugin carrousel"

### Gestion des sous-modules
- Cloner le dépôt avec les sous-modules :
- Lors du clonage du dépôt principal, assurez-vous d'inclure les sous-modules.
- `git clone --recurse-submodules https://github.com/utilisateur/4w4-wp-content.git`
  
### Mettre à jour les sous-modules :
- Pour mettre à jour les sous-modules à leurs dernières versions, utilisez :
- `git submodule update --remote`
- Exemple de structure de répertoires après l'ajout des sous-modules


wp/

├── wp-content/

    ├── themes/

        └── tp2/        # Sous-module pour le thème tp2

    └── plugins/

        └── carrousel/  # Sous-module pour le plugin carrousel

└── .gitmodules         # Fichier de configuration des sous-modules


### Configuration du fichier .gitmodules

Le fichier .gitmodules dans le dépôt principal ressemblera à ceci :

- [submodule "wp-content/themes/tp2"]
  - path = wp-content/themes/tp2
  - url = https://github.com/utilisateur/theme-tp2.git
- [submodule "wp-content/plugins/carrousel"]
  - path = wp-content/plugins/carrousel
  - url = https://github.com/utilisateur/plugin-carrousel.git

En suivant ces étapes, vous aurez intégré les dépôts tp2 et carrousel dans votre dépôt principal, chacun situé dans les sous-répertoires appropriés à l'intérieur de wp-content. Les sous-modules permettent une gestion modulaire et indépendante de chaque composant tout en les rendant facilement accessibles au sein du projet principal.


## Le Fichier .gitignore

### Ignorer tous les dossiers sauf themes/tp2 et plugins/carrousel
/*/
!wp-content/
wp-content/*/
!wp-content/themes/
wp-content/themes/*/
!wp-content/themes/tp2/

!wp-content/plugins/
wp-content/plugins/*/
!wp-content/plugins/carrousel/

### Ne pas ignorer les fichiers .gitignore et readme.md à la racine
!.gitignore
!readme.md


### Explications des règles .gitignore :

- /*/ : Ignore tous les dossiers à la racine du dépôt.
- !wp-content/ : N'ignore pas le dossier wp-content.
- wp-content/*/ : Ignore tous les sous-dossiers de wp-content.
- !wp-content/themes/ : N'ignore pas le dossier themes à l'intérieur de wp-content.
- wp-content/themes/*/ : Ignore tous les sous-dossiers de themes.
- !wp-content/themes/tp2/ : N'ignore pas le dossier tp2 à l'intérieur de wp-content/themes.
- !wp-content/plugins/ : N'ignore pas le dossier plugins à l'intérieur de wp-content.
- wp-content/plugins/*/ : Ignore tous les sous-dossiers de plugins.
- !wp-content/plugins/carrousel/ : N'ignore pas le dossier carrousel à l'intérieur de wp-content/plugins.
- !.gitignore et !readme.md : N'ignore pas les fichiers .gitignore et readme.md à la racine du dépôt.

Avec ce fichier .gitignore, seuls les dossiers wp-content/themes/tp2 et wp-content/plugins/carrousel seront suivis dans Git, et tout le reste sera ignoré. Cela assure que votre dépôt principal contiendra uniquement les sous-dépôts désirés et les fichiers importants tels que .gitignore et readme.md.
