# Pour restructurer vos dépôts Git selon la structure que vous souhaitez, vous pouvez suivre ces étapes :

content/
├── plugin/         # Plugin WordPress
├── theme/          # Thème WordPress
└── .git/           # Dépôt Git pour le dossier content


1. Créez un nouveau dépôt Git pour le dossier content :
Allez dans le dossier racine de votre installation WordPress.
Initialisez un nouveau dépôt Git avec la commande suivante :

cd chemin/vers/votre/installation/wordpress/content
git init content
2. Déplacez les dossiers theme et plugin dans le nouveau dépôt content :
Déplacez les dossiers theme et plugin dans le dossier content.

mv content/theme content/plugin content

content/
├── plugin/         # Plugin WordPress
├── theme/          # Thème WordPress
└── .git/           # Dépôt Git pour le dossier content
Assurez-vous de pousser les modifications vers votre dépôt distant après avoir effectué ces étapes, si nécessaire. Si vous avez déjà du code ou des modifications dans vos anciens dépôts tp2 et carrousel, assurez-vous de les sauvegarder ou de les transférer vers le nouveau dépôt content avant de supprimer les anciens dépôts Git.

## Comment récupérer tous les anciens commit des dépôt tp2 et carrousel vers le dépôt content ?

Pour récupérer tous les anciens commits des dépôts tp2 et carrousel vers le dépôt content, vous pouvez suivre ces étapes :

1. Ajoutez les anciens dépôts comme références distantes :
Tout d'abord, assurez-vous que vous avez accès aux anciens dépôts tp2 et carrousel.
Dans le dossier content, ajoutez les anciens dépôts comme références distantes.

git remote add tp2 /chemin/vers/tp2
git remote add carrousel /chemin/vers/carrousel

2. Récupérez les branches et les commits depuis les dépôts distants :
Récupérez toutes les branches et les commits des dépôts tp2 et carrousel.

git fetch tp2
git fetch carrousel
3. Fusionnez les branches souhaitées dans votre dépôt content :
Une fois que vous avez récupéré les branches, vous pouvez fusionner les branches que vous souhaitez conserver dans votre dépôt content. Assurez-vous d'effectuer ces fusions dans des branches distinctes ou dans des emplacements appropriés de votre dépôt content pour éviter tout écrasement de code existant.Par exemple, pour fusionner la branche principale master du dépôt tp2 dans une branche tp2-master de votre dépôt content :

git checkout -b tp2-master tp2/master
Répétez cette étape pour toutes les branches que vous souhaitez fusionner depuis les dépôts tp2 et carrousel.
4. Répétez le processus pour tous les autres commits ou branches nécessaires :
Si vous avez d'autres branches ou commits dans les dépôts tp2 et carrousel que vous souhaitez récupérer, répétez les étapes 2 et 3 pour ces branches ou commits.
Une fois que vous avez terminé, vous aurez récupéré tous les anciens commits des dépôts tp2 et carrousel vers votre dépôt content. Assurez-vous de tester et de vérifier que tout fonctionne correctement après avoir effectué ces opérations.


## Dans le dépôt content  j'aimerais ajouter un .gitignore pour garder uniquement  le thème/tp2 et plugin/carrousel en ignorant les autres fichiers ou autres dossiers dans  content

Pour ignorer tous les fichiers et dossiers à l'exception de theme/tp2 et plugin/carrousel dans votre dépôt content, vous pouvez créer un fichier .gitignore avec les règles appropriées. Voici comment vous pouvez le faire :

Créez un fichier .gitignore dans le dossier content de votre dépôt :

cd chemin/vers/votre/depot/content
.gitignore
Ajoutez les règles suivantes :

# Ignorer tous les fichiers et dossiers sauf theme/tp2 et plugin/carrousel
*
!theme/tp2/
!plugin/carrousel/
# Ne pas ignorer les fichiers .gitignore eux-mêmes
!.gitignore

Ces règles indiquent à Git d'ignorer tous les fichiers et dossiers (*) sauf theme/tp2/ et plugin/carrousel/. Les lignes commençant par ! excluent les fichiers ou dossiers spécifiés de l'ignorance.

Enregistrez et fermez le fichier .gitignore.
Après avoir ajouté ce fichier .gitignore, Git ignorera tous les fichiers et dossiers dans le dossier content, sauf ceux spécifiés dans les règles. Cela permettra de garder votre dépôt content propre et de ne suivre que les modifications dans les dossiers theme/tp2 et plugin/carrousel.