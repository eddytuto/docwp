## Les « template-parts »

Un **template-part** est un fragment de code HTML et PHP réutilisables qui sont inclus dans plusieurs fichiers de modèles différents.

Le dossier "template-parts" stocke généralement des extraits de code. En fait, il peut contenir tout type de code que vous souhaitez réutiliser, y compris du code **JavaScript, du code CSS, etc.**

**L'objectif principal du dossier** "template-parts" est de permettre aux développeurs de stocker **des extraits de code réutilisables** et de les inclure dans les fichiers de modèle sans avoir à les copier-coller dans chaque fichier. Cela permet de rendre le **code plus modulaire**, plus **facile à maintenir** et **plus facile à lire**, car les extraits de code sont stockés dans des fichiers séparés avec des noms significatifs.

Par conséquent, les extraits de code stockés dans le dossier "template-parts" peuvent être appelés à partir de n'importe quel fichier de modèle en utilisant la fonction **get_template_part().** Cette fonction charge automatiquement le fichier correspondant à partir du dossier "template-parts" et l'inclut dans le fichier de modèle.

### La fonction get_template_part()

est une **fonction intégrée de WordPress** qui **permet d'inclure un fichier de modèle stocké dans le dossier "template-parts"** d'un thème WordPress. Elle prend deux arguments :

**Le premier argument** est le nom de la **partie du modèle à inclure**. Il doit correspondre au nom du fichier de modèle, sans l'extension de fichier .php et sans le préfixe template-parts/. Par exemple, si le fichier de modèle se trouve dans le dossier "template-parts" et s'appelle header.php, le premier argument doit être header.

**Le deuxième argument est facultatif** et permet de spécifier une chaîne de texte à utiliser comme préfixe ou suffixe pour le nom du fichier de modèle. Par exemple, si le deuxième argument est **'small'**, WordPress va chercher un fichier de modèle appelé **header-small.php** dans le dossier **"template-parts"**.

### Exemples

`<?php get_template_part( 'template-parts/entete' ); ?>`

> permettrait d'inclure le fichier **template-parts/entete.php**

`<?php get_template_part( 'template-parts/categorie', cours ); ?>`

> permettrait d'inclure le fichier **template-parts/categorie-cours.php
> **
> Le fichier **categorie-cours.php** contiendrait en partie:

```
<article>
    <h5><a href="<?php the_permalink(); ?>"> <?= $sigle; ?></a></h5>
    <h6><?= $grand_titre; ?></h6>
    <p><?= wp_trim_words(get_the_excerpt(), 15) ?></p>
    <h6><?= $duree; ?></h6>
</article>
```
