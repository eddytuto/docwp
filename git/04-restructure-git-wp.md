# Fusionner quatre dépôts ensemble

Pour intégrer les dépôts **tp2**, **carrousel**, **voyage**, **les_posts** dans un seul dépôt à l'intérieur de **wp-content** sous les chemins:
- **wp-content** // le dépôt principal
- **wp-content/themes/tp2** // _sous-module_
- **wp-content/plugins/carrousel** // _sous-module_
- **wp-content/plugins/voyage** // _sous-module_
- **wp-content/plugins/les_posts**, // _sous-module_.

**Voici les étapes détaillées**:

## Étapes pour intégrer les dépôts comme sous-modules

### Créer le dépôt principal :

```IMPORTANT``` **Surtout**, ne réaliser aucune des commandes suivantes sur votre dossier **wp-content** actuel mais plutôt sur une **copie** de ce dossier.
Nous allons premièrement créer un dossier vide **\_wp-content** .
Une fois que **\_wp-content** contiendra l'équivalent du dossier **wp-content** nous échangerons les noms de ces deux dossiers. Créer aussi les deux dossiers vide **_wp-content/themes** et **_wp-content/plugins**

- Dans le dossier **\_wp-content** créer un dépôt
- `git init`

### Ajouter les sous-modules :

Pour réaliser les commandes suivantes, sur Github, vous devez fusionner avec **pull request** votre branche terminal à la branche **main**.

- Ajoutez les dépôts existants tp2 et carrousel et toutes autres extensions qu'on voudrait récupérer en tant que sous-modules dans les chemins spécifiés.
- **Ajouter le thème en tant que sous-module**
- `git submodule add https://github.com/eddytuto/4w4-2024-gr2 themes/tp2`
- **Ajouter le plugin en tant que sous-module**
- `git submodule add https://github.com/eddytuto/carrousel-2024-gr2 plugins/carrousel`

### Initialiser et mettre à jour les sous-modules :

Initialisez les sous-modules et mettez-les à jour pour qu'ils pointent vers le bon commit.
Ces commandes sont exécutées à partir de **_wp-content**
Cependant, si vous ajoutez un nouveau sous-module à votre dépôt avec **git submodule add**, vous n'avez **pas besoin d'exécuter git submodule init**  et **git submodule update** pour ce sous-module spécifique, car la commande add l'initialise automatiquement. Mais si quelqu'un d'autre clone votre dépôt, il devra exécuter git submodule init et git submodule update pour obtenir le sous-module.

- `git submodule init` // est exécutée une seule fois
- `git submodule update` // pour chaque ajout de nouveaux submodules on exécutera cette commande

### Valider les modifications :

Validez les changements dans le dépôt principal pour inclure les références aux sous-modules.

- `git add .`
- `git commit -m`


- Exemple de structure de répertoires après l'ajout des sous-modules

wp/

├── wp-content/

    ├── themes/

        └── tp2/        # Sous-module pour le thème tp2

    └── plugins/

        └── carrousel/  # Sous-module pour le plugin carrousel

└── .gitmodules # Fichier de configuration des sous-modules

### Configuration du fichier .gitmodules

Le fichier .gitmodules dans le dépôt principal ressemblera à ceci :
```
[submodule "plugins/carrousel"]
	path = plugins/carrousel
	url = https://github.com/eddytuto/carrousel-2024-gr1
[submodule "themes/tp2"]
	path = themes/tp2
	url = https://github.com/eddytuto/4w4-2024-gr1
```

En suivant ces étapes, vous aurez intégré les dépôts tp2 et carrousel dans votre dépôt principal, chacun situé dans les sous-répertoires appropriés à l'intérieur de wp-content. Les sous-modules permettent une gestion modulaire et indépendante de chaque composant tout en les rendant facilement accessibles au sein du projet principal.

## Le Fichier .gitignore

### Ignorer tous les dossiers sauf themes/tp2 et plugins/carrousel

```
/*/
!wp-content/
wp-content/*/
!wp-content/themes/
wp-content/themes/*/
!wp-content/themes/tp2/
!wp-content/plugins/
wp-content/plugins/*/
!wp-content/plugins/carrousel/
// Ne pas ignorer les fichiers .gitignore et readme.md à la racine
!.gitignore
!readme.md
```

### Explications des règles .gitignore :

- /\*/ : Ignore tous les dossiers à la racine du dépôt.
- !wp-content/ : N'ignore pas le dossier wp-content.
- wp-content/\*/ : Ignore tous les sous-dossiers de wp-content.
- !wp-content/themes/ : N'ignore pas le dossier themes à l'intérieur de wp-content.
- wp-content/themes/\*/ : Ignore tous les sous-dossiers de themes.
- !wp-content/themes/tp2/ : N'ignore pas le dossier tp2 à l'intérieur de wp-content/themes.
- !wp-content/plugins/ : N'ignore pas le dossier plugins à l'intérieur de wp-content.
- wp-content/plugins/\*/ : Ignore tous les sous-dossiers de plugins.
- !wp-content/plugins/carrousel/ : N'ignore pas le dossier carrousel à l'intérieur de wp-content/plugins.
- !.gitignore et !readme.md : N'ignore pas les fichiers .gitignore et readme.md à la racine du dépôt.

Avec ce fichier .gitignore, seuls les dossiers wp-content/themes/tp2 et wp-content/plugins/carrousel seront suivis dans Git, et tout le reste sera ignoré. Cela assure que votre dépôt principal contiendra uniquement les sous-dépôts désirés et les fichiers importants tels que .gitignore et readme.md.

## Réaliser un commit sur la structure générale « wp-content »

Pour réaliser un commit sur la structure générale après avoir effectué des modifications dans les sous-dépôts **tp2** et **carrousel**, vous devez suivre quelques étapes pour vous assurer que les changements dans les sous-dépôts sont bien intégrés et référencés correctement dans le dépôt principal **wp-content**. Voici le processus détaillé :

### Étapes à suivre :

#### Naviguer dans le sous-dépôt et valider  les changements :

- Supposons que vous avez fait des modifications dans le sous-dépôt tp2. Naviguez dans le répertoire de ce sous-dépôt et valider les changements.
- cd wp-content/themes/tp2
- `git add .`
- `git commit -m "Description des modifications effectuées dans tp2"`
- Pousser les changements vers le dépôt distant du sous-dépôt :
- `git push 4w4 tp2` // Assurez-vous de spécifier la branche correcte

#### Revenir au dépôt principal et mettre à jour la référence du sous-dépôt :

- Retournez dans le dépôt principal et mettez à jour la référence du sous-dépôt tp2.
- cd ../../../ # Remontez au répertoire racine du dépôt principal
- `git add --all`
- Valider les changements dans le dépôt principal :
- Validez les changements dans le dépôt principal pour inclure la nouvelle référence du sous-dépôt.
- `git commit -m "Mettre à jour la référence du sous-dépôt tp2"`
- Pousser les changements vers le dépôt distant principal :
- `git push 4w4 main`


### Note sur les sous-dépôts :

- Les sous-modules Git enregistrent des références spécifiques à des commits dans les sous-dépôts.
- Cela signifie que lorsque vous mettez à jour un sous-module, vous pointez le dépôt principal vers un commit spécifique dans le sous-dépôt.
- Assurez-vous toujours que les sous-dépôts sont à jour avec les derniers commits avant de faire des validations dans le dépôt principal. Ce qui veut dire qu'il faut faire des add et commit dans chacun de nos sous-module avant d'executer une validation dans le dépôt principal.

### git log

Lorsque vous exécutez la commande git log à partir du dépôt principal, vous verrez l'historique des commits du dépôt principal lui-même. Cet historique inclut tous les commits effectués directement dans le dépôt principal, y compris ceux qui mettent à jour les références des sous-modules (par exemple, lorsque vous avez fait des changements dans tp2 ou carrousel et que vous avez mis à jour leurs références dans le dépôt principal).
