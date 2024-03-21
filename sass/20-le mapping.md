# Le mapping
En Sass, un "mapping" fait référence à une structure de données qui associe des clés à des valeurs. Plus précisément, il s'agit d'une collection de paires clé-valeur où chaque clé est associée à une valeur spécifique.

Dans Sass, les mappings sont souvent utilisés pour stocker des jeux de propriétés CSS, ce qui permet une gestion plus efficace et modulaire du style. Par exemple, vous pourriez utiliser un mapping pour stocker des ensembles de couleurs, des tailles de police, des valeurs d'espacement, etc.

### Exemples

```
// Définition d'un mapping pour les couleurs
$colors: (
  primary: #007bff,
  secondary: #6c757d,
  success: #28a745,
  danger: #dc3545
);

// Utilisation du mapping pour définir les styles
.button {
  background-color: map-get($colors, primary);
  color: white;
  padding: 10px 20px;
  border: none;
}
```

### Exemple pour maintenir une palette de couleur


Ce mapping définit des variables de couleur en utilisant l'espace colorimétrique HSL (Hue, Saturation, Lightness) pour représenter différentes nuances de couleurs. Ces variables de couleur sont organisées de manière logique et cohérente, ce qui facilite leur utilisation dans le code Sass pour maintenir une palette de couleurs cohérente et personnalisable.

```
$--clr-bleu-pale    : hsl(220, 100%, 85%);
$--clr-bleu-leger  : hsl(220, 100%, 60%);
$--clr-bleu-moyen  : hsl(220, 100%, 30%);    
$--clr-bleu-fonce  : hsl(220, 100%, 15%);


$--clr-orange-pale: hsl(40, 100%, 85%);
$--clr-orange-leger  : hsl(40, 100%, 50%);
$--clr-orange-moyen  : hsl(40, 100%, 30%);
$--clr-orange-fonce  : hsl(40, 100%, 15%);

$--clr-rouge-pale: hsl(10, 100%, 85%);
$--clr-rouge-leger  : hsl(10, 100%, 50%);
$--clr-rouge-moyen  : hsl(10, 100%, 30%);
$--clr-rouge-fonce  : hsl(10, 100%, 15%);

$--clr-vert-pale: hsl(70, 100%, 85%);
$--clr-vert-leger  : hsl(70, 100%, 50%);
$--clr-vert-moyen  : hsl(70, 100%, 30%);
$--clr-vert-fonce  : hsl(70, 100%, 15%);
```

### La boucle @each

En Sass, vous pouvez parcourir une structure map avec une boucle @each de la manière suivante :

Supposons que vous ayez une map définie comme ceci :


```
$colors: (
  primary: #ff0000,
  secondary: #00ff00,
  tertiary: #0000ff
);
```

Vous pouvez parcourir cette map avec une boucle @each de cette manière :

```
@each $key, $value in $colors {
  // Utilisez $key et $value dans le corps de la boucle
  .#{$key} {
    color: $value;
  }
}
```
Dans cet exemple, `$key` représente la clé de chaque paire clé-valeur dans la map, tandis que `$value` représente la valeur associée à chaque clé. À l'intérieur du corps de la boucle, vous pouvez utiliser ces variables pour appliquer des styles ou effectuer d'autres opérations.

Voici comment cela fonctionne :

Pour chaque paire clé-valeur dans la map `$colors`, Sass assigne la clé à `$key` et la valeur à `$value`.
À chaque itération de la boucle, Sass génère un `sélecteur` CSS avec la classe correspondant à la clé de la map et applique la couleur correspondante.
Cela vous permet de générer rapidement des styles CSS en fonction des valeurs de la map, ce qui peut être utile pour maintenir une palette de couleurs cohérente dans votre feuille de style.



### Organisation des couleurs

primaire, secondaire, ternaire et vert sont des catégories de couleurs.
Chaque catégorie contient quatre niveaux de couleurs, désignés par les clés 100, 200, 300 et 400.
Pour chaque niveau de couleur, la valeur correspond à une variable Sass qui représente la couleur spécifique dans le système de couleurs défini ailleurs dans votre code.
Cela permet d'organiser les couleurs par catégorie et par niveau, ce qui rend plus facile la gestion et la réutilisation des couleurs dans votre feuille de style Sass.

```
$defaut: (
    primaire : (
        100: $--clr-bleu-pale,
        200: $--clr-bleu-leger,
        300: $--clr-bleu-moyen,
        400: $--clr-bleu-fonce
    ),
    secondaire : (
        100: $--clr-orange-pale,
        200: $--clr-orange-leger,
        300: $--clr-orange-moyen,
        400: $--clr-orange-fonce
    ),
    ternaire : (
        100: $--clr-rouge-pale,
        200: $--clr-rouge-leger,
        300: $--clr-rouge-moyen,
        400: $--clr-rouge-fonce
    ),
    vert : (
        100: $--clr-vert-pale,
        200: $--clr-vert-leger,
        300: $--clr-vert-moyen,
        400: $--clr-vert-fonce
    )
);
```

### Création de classes de couleurs de façon dynamique

```
@each $nom, $couleurs in $defaut {
@each $valeur, $couleur in $couleurs {
    .clr-#{$nom}-#{$valeur} {
        color : #{$couleur};
       
    }
        .bck-#{$nom}-#{$valeur} {
      
        background-color:  #{$couleur} ;
    }
}
}
```


Cette boucle imbriquée parcourt le mapping `$defaut` qui contient plusieurs catégories de couleurs, chaque catégorie ayant plusieurs niveaux de couleurs associés à des valeurs spécifiques. Voici comment la boucle fonctionne :

`La première boucle @each` parcourt les paires clé-valeur du mapping `$defaut`. À chaque itération, `$nom` contient le nom de la catégorie de couleur (par exemple, primaire, secondaire, etc.), et `$couleurs` contient un sous-mapping qui associe les niveaux de couleur à leurs valeurs.

À l'intérieur de la première boucle, `une deuxième boucle @each` parcourt les paires clé-valeur du sous-mapping `$couleurs`. À chaque itération, `$valeur` contient la valeur du niveau de couleur (par exemple, 100, 200, etc.), et `$couleur` contient la couleur correspondante.

À chaque itération des deux boucles, deux sélecteurs CSS sont générés :

`.clr-#{$nom}-#{$valeur}` : Ce sélecteur crée une classe CSS avec le nom de la catégorie de couleur et le niveau de couleur. Par exemple, si $nom est primaire et `$valeur` est 100, le sélecteur deviendra .clr-primaire-100.
`.bck-#{$nom}-#{$valeur}` : Ce sélecteur crée une classe CSS pour le fond avec le nom de la catégorie de couleur et le niveau de couleur. Par exemple, si $nom est primaire et `$valeur` est 100, le sélecteur deviendra .bck-primaire-100.
Les propriétés CSS color et background-color sont alors définies avec la valeur de couleur correspondante, extraite du mapping `$defaut`.

Cette boucle imbriquée génère des classes CSS pour chaque combinaison de catégorie de couleur et de niveau de couleur, ce qui permet d'appliquer facilement des couleurs à différents éléments de votre interface.


### Technique pour créer des agencements de couleurs

```
$agencement-couleur :(
    primaire: ($--clr-bleu-fonce, ($--clr-bleu-pale, $--clr-bleu-leger)),
    secondaire: ($--clr-orange-fonce, $--clr-orange-pale),
    ternaire: ($--clr-rouge-fonce, $--clr-rouge-pale),
    vert: ($--clr-vert-fonce, $--clr-vert-pale)
);
```

### Mixin


Un mixin en Sass est un bloc réutilisable de code qui peut contenir des déclarations de style, des directives de contrôle de flux et même d'autres mixins. Les mixins sont définis à l'aide de la directive @mixin suivie du nom du mixin et de ses paramètres, le cas échéant. Voici comment définir un mixin en Sass :



### @mixin couleur-agencement($clr,$bck)

Ce mixin prend deux arguments :

`$clr` : la couleur du texte.
`$bck` : l'agencement de couleurs, qui peut être une seule couleur ou une liste de couleurs pour un dégradé.
En fonction de la longueur de la liste `$bck`, le mixin détermine s'il doit appliquer une couleur de fond unie ou un dégradé.

Si la longueur de la liste `$bck` est égale à 1, cela signifie qu'il n'y a qu'une seule couleur, donc le mixin applique cette couleur comme couleur de fond (background-color).
Sinon, s'il y a plus d'une couleur dans la liste `$bck`, cela signifie qu'il y a un dégradé, donc le mixin crée un dégradé linéaire avec ces couleurs comme arrière-plan (background-image).
Voici comment vous pourriez utiliser ce mixin dans votre feuille de style :

```
@mixin couleur-agencement($clr,$bck){
    color: $clr;
    @if(list.length($bck)==1){
        background-color: $bck;
    }   @else {
        background-image: linear-gradient(90deg, $bck);
    }   
}
```
### @use 'sass:list'
Ajouter @use 'sass:list' sur la première ligne de votre fichier


### boucle utilisant le mixin



```
@each $valeur, $clr in $agencement-couleur {
    .clr-agencement-#{$valeur} {
        @include couleur-agencement($clr...);
    }
} 
```

Dans cette boucle @each, vous parcourez chaque paire de valeurs dans votre agencement de couleurs. Chaque paire consiste en une clé (comme "primaire", "secondaire", etc.) et une valeur qui est une liste de couleurs.

Pour chaque itération de la boucle, vous générez une règle de style avec une classe .clr-agencement-{clé} et utilisez le mixin couleur-agencement pour appliquer les couleurs appropriées à cette classe.

Voici ce que fait chaque partie de cette boucle :

@each $valeur, `$clr` in `$agencement-couleur` { ... }: Cette boucle parcourt chaque paire clé-valeur dans votre liste `$agencement-couleur`.

.clr-agencement-#{`$valeur`} { ... }: Pour chaque paire, une classe est générée avec le préfixe .clr-agencement- suivi de la clé correspondante.

@include couleur-agencement(`$clr`...);: Vous incluez ensuite le mixin couleur-agencement en lui passant la liste de couleurs `$clr` comme argument. La syntaxe ... permet de déballer les éléments de la liste comme des arguments individuels pour le mixin.

Ainsi, cette boucle générera une série de règles de style pour chaque agencement de couleurs, appliquant les couleurs correspondantes à chaque classe générée.


