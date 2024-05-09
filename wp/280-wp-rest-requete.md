# Exemples de requêtes REST API

- Récupérer un article avec ses champs personnalisés :
  - `GET /wp-json/wp/v2/posts/{post_id}`
  - Cette requête récupère un article spécifique avec l'ID {post_id} et inclut les champs personnalisés associés à cet article.

- Récupérer une liste d'articles avec des champs personnalisés :
  - `GET /wp-json/wp/v2/posts?filter[meta_key]={custom_field_key}&filter[meta_value]={custom_field_value}`
  - Cette requête récupère une liste d'articles filtrés par un champ personnalisé spécifique. 
  - Remplacez {custom_field_key} par la clé du champ personnalisé et {custom_field_value} par sa valeur.

- Récupérer une liste d'articles avec des champs personnalisés spécifiques inclus dans la réponse :
  - `GET /wp-json/wp/v2/posts?_embed&fields=id,title,meta`
  - Cette requête récupère une liste d'articles avec leurs champs id, title, et meta (champs personnalisés) inclus dans la réponse.


## Est-ce que  GET /wp-json/wp/v2/posts/{post_id} est équivalent à https://mondomaine/wp-json/wp/v2/posts/{post_id} 

  - Oui, exactement. Dans une requête HTTP, la partie avant le chemin relatif (dans ce cas, "/wp-json/wp/v2/posts/{post_id}") est l'URL de base, tandis que la partie après est le chemin relatif. L'URL de base est généralement l'adresse du site WordPress, comme "https://mondomaine". Lorsque vous envoyez une requête HTTP à un serveur, le client (comme votre navigateur web ou une application) utilise l'URL de base pour déterminer où envoyer la requête, et le serveur utilise le chemin relatif pour déterminer quelle ressource vous demandez.

  - Ainsi, si votre site WordPress est hébergé à l'adresse "https://mondomaine", alors :
    - GET /wp-json/wp/v2/posts/{post_id} est une requête relative qui demande à récupérer un article spécifique avec l'ID {post_id} via l'API REST de WordPress.
    - https://mondomaine/wp-json/wp/v2/posts/{post_id} est l'équivalent de cette requête, mais sous forme d'URL absolue.
    -   Dans les deux cas, la requête est envoyée au même serveur et le même résultat est attendu, à condition que le serveur réponde correctement aux requêtes de l'API REST WordPress.
 
 ## Exemple avec champs personnalisées

 ### GET /wp-json/wp/v2/posts?filter[meta_key]={temperature_max}&filter[meta_value]={35} comment faire en javascript pour récupérer les résultats de la requête

- Pour récupérer les résultats de la requête GET /wp-json/wp/v2/posts avec des filtres sur les champs personnalisés meta_key et meta_value, vous pouvez utiliser l'API Fetch en JavaScript. Voici comment vous pouvez le faire :

```
// Définir les valeurs des filtres
const meta_key = 'temperature_max';
const meta_value = 35;

// Construire l'URL de la requête avec les filtres
const url = `/wp-json/wp/v2/posts?filter[meta_key]=${meta_key}&filter[meta_value]=${meta_value}`;

// Utiliser Fetch pour envoyer la requête GET
fetch(url)
  .then(response => {
    // Vérifier si la réponse est OK (statut 200)
    if (!response.ok) {
      throw new Error('Erreur lors de la récupération des données');
    }
    // Convertir la réponse en JSON
    return response.json();
  })
  .then(data => {
    // Manipuler les données récupérées
    console.log('Résultats de la requête :', data);
  })
  .catch(error => {
    console.error('Erreur :', error);
  });
```

Ce script envoie une requête **GET** à l'URL construite avec les filtres **meta_key** et **meta_value**. Une fois que la réponse est reçue, le code vérifie si la réponse est OK (statut 200) et la convertit en JSON. Enfin, les données JSON sont affichées dans la console ou manipulées selon vos besoins.

Assurez-vous d'exécuter ce code depuis un environnement JavaScript qui a accès à l'API REST de votre site WordPress et qui peut atteindre l'URL de l'API.

### Comment extraire et afficher à partir de la requête précédente le champ personnalisé « ville »

Si vous souhaitez extraire et afficher le champ personnalisé "ville" à partir des résultats de votre requête précédente, vous devez parcourir les données récupérées pour chaque article et extraire la valeur du champ personnalisé "ville" pour chacun d'eux.

#### Voici comment vous pouvez le faire en ajustant le code précédent :
```
// Définir les valeurs des filtres
const meta_key = 'temperature_max';
const meta_value = 35;

// Construire l'URL de la requête avec les filtres
const url = `/wp-json/wp/v2/posts?filter[meta_key]=${meta_key}&filter[meta_value]=${meta_value}`;

// Utiliser Fetch pour envoyer la requête GET
fetch(url)
  .then(response => {
    // Vérifier si la réponse est OK (statut 200)
    if (!response.ok) {
      throw new Error('Erreur lors de la récupération des données');
    }
    // Convertir la réponse en JSON
    return response.json();
  })
  .then(data => {
    // Parcourir les articles et extraire le champ personnalisé "ville"
    data.forEach(post => {
      // Vérifier si le champ personnalisé "ville" existe
      if (post.meta && post.meta.ville) {
        // Afficher la valeur du champ personnalisé "ville"
        console.log('Ville :', post.meta.ville);
      } else {
        console.log('Champ personnalisé "ville" non trouvé pour l\'article avec l\'ID :', post.id);
      }
    });
  })
  .catch(error => {
    console.error('Erreur :', error);
  });
```

Dans ce code, nous parcourons chaque article retourné par la requête et vérifions si le champ personnalisé "ville" est présent dans les données de l'article (post.meta.ville). Si c'est le cas, nous affichons la valeur du champ "ville". Si le champ "ville" n'est pas trouvé pour un article particulier, un message est affiché indiquant que le champ n'a pas été trouvé pour cet article.

#### voici une requête qui permettrait d'extraire les villes qui ont une temperature_max situé entre 35 et 45 degrée

Pour extraire les villes qui ont une temperature_max située entre 35 et 45 degrés, vous pouvez utiliser la requête suivante :


``GET /wp-json/wp/v2/posts?filter[meta_key]=temperature_max&filter[meta_value][min]=35&filter[meta_value][max]=45&fields=meta``

#### Explication de la requête :

- ***filter[meta_key]=temperature_max*** : Spécifie le champ personnalisé à filtrer, dans ce cas, temperature_max.
- ***filter[meta_value][min]=35*** : Spécifie la valeur minimale du champ personnalisé, dans ce cas, 35 degrés.
- ***filter[meta_value][max]=45*** : Spécifie la valeur maximale du champ personnalisé, dans ce cas, 45 degrés.
- ***fields=meta*** : Spécifie que seuls les champs personnalisés doivent être inclus dans les résultats.
- Cette requête récupérera les articles qui ont une temperature_max entre 35 et 45 degrés et inclura uniquement les champs personnalisés dans les résultats. 
- Assurez-vous que ***temperature_max*** est la **clé** correcte du champ personnalisé contenant les températures maximales dans vos articles. Si la clé réelle est différente, remplacez-la dans la requête.

- N'oubliez pas d'adapter cette requête à votre propre configuration WordPress, en utilisant l'URL de votre site WordPress comme base pour l'API REST.

#### Recherche: Une requête rest api qui permettrai d'extraire tous les article contenants  une chaîne de caractères spécifiée en paramètre

Pour extraire tous les articles contenant une chaîne de caractères spécifiée en paramètre, vous pouvez utiliser la requête suivante :

``GET /wp-json/wp/v2/posts?search={votre_chaine_de_caractères}``


- ***{votre_chaine_de_caractères}*** est la chaîne de caractères que vous souhaitez rechercher dans les articles.
- Cette requête récupérera tous les articles qui contiennent la chaîne de caractères spécifiée dans leur contenu, leur titre ou tout autre champ texte indexé par la recherche de votre site WordPress.

- Assurez-vous de remplacer {votre_chaine_de_caractères} par la chaîne de caractères que vous souhaitez rechercher.

