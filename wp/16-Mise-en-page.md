## Mise en page générale avec grid

L'utilisation de la propriété «**grid-template-areas**» permet de définir des **zones nommées** pour chaque élément de la **grille**. Cela **facilite la compréhension de la structure de la page** et **permet de réorganiser facilement les éléments** en modifiant simplement les noms des zones dans le code CSS.

l'ajout d'une marge entre les rangées avec «**row-gap**» permet de donner de l'espace entre les différents éléments de la page, ce qui est une bonne pratique pour améliorer la lisibilité et la clarté de la mise en page.

### Nous appliquerons une structure de grid sur les enfants de la balise body

- body (.site)
  - header (.site\_\_entete)
  - main (.site\_\_main)
  - footer (.site\_\_footer)

### Une grille générale sur le conteneur principal

```
.site {
  display: grid;
  grid-template-columns: auto;
  grid-template-areas:
    "header"
    "main"
    "footer";
  row-gap: 50px;
}
```

On a une seule colonne qui prend toute la largeur du «**viewport**»

> grid-template-columns: auto;

On situe les 3 grandes zone de la mise en pahe

> grid-template-areas:
> "header"
> "main"
> "footer";

On définit l'espace entre chacune des 3 zones: header, main et footer

> row-gap: 50px;

---

### On définit chacune des grandes zone: header, main et footer

```
.site__entete {
  grid-area: header;
  padding: 1rem clamp(1rem, 3vw, 20rem);
  background-color: antiquewhite;
}

.site__main {
  grid-area: main;
  overflow: hidden; /* Resolves issue with <pre> elements forcing full width. */
}

.site__footer {
  grid-area: footer;
  background-color: antiquewhite;
}
```

### Ajoutons maintenant une nouvelle zone «sidebar: header, main, footer et sidebar

```
.site__aside {
  grid-area: aside;
  background-color: rgb(47, 148, 210);
}
```

### Ajustons notre mise en page selon la largeur de l'écran

```
.site {
  display: grid;
  grid-template-columns: auto;
  grid-template-areas:
    "header"
    "aside"
    "main"
    "footer";
  row-gap: 50px;
  background-color: rgb(191 232 255);

  @media screen and (min-width: 1000px) {
    grid-template-columns: 20% auto;
    grid-template-areas:
      "header header"
      "aside main"
      ". main"
      "footer footer";
  }
}
```
