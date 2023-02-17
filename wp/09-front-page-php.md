## Le modèle front-page.php

### Extraire le début d'un article

> wp_trim_words(get_the_excerpt(), 15)

- Est utilisée pour afficher une version raccourcie (ou "extrait") d'un article dans WordPress.
- Cet extrait est limité à 15 mots en utilisant la fonction **wp_trim_words()**.

- L'avantage de cette instruction est qu'elle permet de limiter l'affichage de l'article à un nombre de mots spécifique, ce qui peut être utile pour présenter un aperçu de l'article à l'utilisateur sans trop en révéler. Cela peut être particulièrement utile dans les pages d'archives ou les pages de recherche où plusieurs articles sont affichés.

- L'utilisation de la fonction **get_the_excerpt()** récupère le contenu de l'extrait de l'article, qui est généralement un **résumé** de l'article, et la fonction **wp_trim_words()** permet de limiter le nombre de mots à afficher. Cette instruction est simple et rapide à mettre en place, ce qui peut être utile pour les développeurs qui cherchent à ajouter des extraits à leurs thèmes WordPress.

### Disposition des blocs de résumé d'article

#### Deux approches:

- Par flexbox
- Par grid

### L'approche flexbox

```
.blocflex {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;

  article {
    flex: 1 0 300px;
    border: 1px solid #aaa;
    padding: 5px;
    margin: 10px;
  }
}
```

### L'approche grid

```
.blocflex {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  // Cette déclaration sera meilleur quand min() sera mieux supporté
  // grid-template-columns: repeat(auto-fill, minmax(min(200px, 100%), 1fr));
  gap: 2rem;
  margin: 2rem;

  article {
    border: 1px solid #aaa;
    padding: 1rem;
  }
}
```

### Si vous voulez ajouter un box shadow original à vos blocs

- https://getcssscan.com/css-box-shadow-examples
