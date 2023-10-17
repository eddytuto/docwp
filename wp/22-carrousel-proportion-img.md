## Optimiser l'affichage des images du carrousel

1. Utiliser de grandes images au dessus de 1000px x 1000px
2. La galerie affichera une version réduite des images du carrousel « thumbnail ou medium »
3. Le carrousel contiendra les **images sources téléversée** et non l'image transformée par wordpress. Ex: l'**image thumbnail** est: **mon_image-150x150.jpg**, **l'image source est mon_image.jpg**.
4. Pour intégrer les **images sources** dans le carrousel on **retirera** la sous chaîne **« -150x150 »** du nom de fichier.

### La grandeur de la boîte modale s'adaptera à l'image

- L'**objectif** sera de **maintenir le rapport hauteur/largeur de l'image** tout en adaptant la **taille de la boîte modale** pour qu'elle s'adapte à la taille de l'image sans la **couper** et/ou la **déformer**.
- L'adaptation sera générée **dynamiquement** avec **Javascript**

### La stratégie à utiliser pour optimiser l'affichages des images du carrousel

> La stratégie pour résoudre le problème d'ajustement de la boîte modale à l'image qu'elle contient et à la dimension de la fenêtre du navigateur implique plusieurs paramètres.
> Tout d'abord, il est important de récupérer la **largeur** et la **hauteur** de l'**image** ainsi que la **largeur** et la **hauteur** de la **fenêtre du navigateur**, car elles détermineront la taille de la boîte modale.

> Il est important de noter que la **taille de la fenêtre du navigateur peut varier** d'un utilisateur à l'autre et en fonction de l'appareil utilisé (ordinateur de bureau, tablette, téléphone mobile, etc.). Par conséquent, il est important que l'affichage soit aussi précis sur tous les appareils.

> Une fois que toutes ces dimensions sont récupérées, il faut calculer la **largeur** et la **hauteur** de la **boîte modale** en fonction de la largeur et la hauteur de l'image et la largeur et la hauteur de la fenêtre du navigateur. On peut utiliser différentes formules pour ce calcul en fonction des contraintes spécifiques du projet. Enfin, la position de la boîte modale doit être définie pour qu'elle soit **centrée au milieu** de la fenêtre du navigateur.

### Les fonctions qui seront utilisées pour ce traitement

Voici une liste de fonctions qui peuvent être utiles pour adapter une boîte modale au contenu qu'elle contient :

1. `Element.offsetWidth` et `Element.offsetHeight`: ces propriétés retournent la largeur et la hauteur de l'élément, y compris les bordures et le padding.

2. `Element.style.width` et `Element.style.height`: ces propriétés permettent de définir la largeur et la hauteur d'un élément en CSS.

3. `Element.naturalWidth` et `Element.naturalHeight`: ces propriétés retournent la largeur et la hauteur de l'image originale, sans tenir compte des redimensionnements éventuels.

4. `window.innerWidth` et `window.innerHeight`: ces propriétés retournent respectivement la largeur et la hauteur de la fenêtre du navigateur.

5. `Math.round()`: cette fonction permet d'arrondir un nombre à l'entier le plus proche.

6. `clamp()`: cette fonction CSS permet de limiter une valeur à un intervalle donné. Par exemple : `width: clamp(200px, 50%, 500px)` permet de définir une largeur qui sera comprise entre 200 pixels et 500 pixels, en fonction de la largeur disponible.

7. `Element.style.top` et `Element.style.left`: ces propriétés permettent de définir la position d'un élément en CSS.

8. `Element.getBoundingClientRect()`: cette méthode retourne un objet avec les coordonnées et les dimensions de l'élément, par rapport à la fenêtre du navigateur.

### Les étapes à suivre

1. Récupérer la largeur et la hauteur de l'image à afficher dans la boîte modale, ainsi que la largeur du carrousel et la hauteur de la boîte modale elle-même.
2. Récupérer également la largeur et la hauteur de la fenêtre du navigateur.
3. Calculer la largeur et la hauteur souhaitées pour la boîte modale en fonction de la largeur de l'image et de la largeur de la fenêtre du navigateur. Il est important de maintenir le ratio de l'image pour éviter toute distorsion.
4. Adapter la taille de la boîte modale en conséquence, en utilisant soit la propriété `clamp()` en CSS, soit en définissant la largeur et la hauteur directement en pixels.
5. Centrer la boîte modale horizontalement et verticalement par rapport à la fenêtre du navigateur.

> Il est important de mettre à jour la taille de la boîte modale en cas de changement de taille de la fenêtre du navigateur. Cette mise à jour peut être effectuée en utilisant un événement "resize" en JavaScript.
