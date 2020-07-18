# Landing Page - Feel the Music

Voici votre nouveau projet. Vous avez été engagez pour reproduire le layout Figma d'un site concurrent de Spotify.

Votre designer vous à envoyé le design en screenshot. A vous de le reproduire en HTML.

## Consignes

* Soyez le plus fidèle possible au modèle
* Chaque page doit contenir le même header et footer. Pour le moment il faudra les réaliser en dur sur chaque page. 
  * **Le header**: doit contenir le logo et le titre à gauche. Le menu est sur la droite.
  * **Le footer**: un menu à gauche vers d'autres pages (href="#") et à droite les liens sociaux.
* Il vous faut 3 pages: 
  * **index.html**: la page d'accueil
    * Il faut le portrait de la femme
    * A sa droite doit se trouver le titre d'accroche, le sous-titre et le bouton pour arriver sur la page "comments.html"
  * **discover.html**: la page qui présente le produit. Cette page est un peu plus libre.
    * Affichez quelques pochettes d'album que vous aimez
    * Placez un texte d'accroche
  * **comments.html**: la page avec les commentaires et la possibilités d'en rajouter.
    * Affichez un formulaire avec 2 champs ("auteur" et "comment")
    * Placez un bouton pour envoyez votre formulaire.
    * Affichez les commentaires récupérés par l'API (voir plus bas) 
* Il vous faut une feuille de style **"style.css"**
* Il vous faut une page **"scripts.js"**
  * Il vous faut réaliser un système de commentaire léger. 
  * Suivez les consignes des exercices Javascript de cette semaine pour y arriver.
  * Utilisez l'API suivante: `https://quotes-light-api.herokuapp.com/api/comments/`

## Screenshot

### index.html

![index](../../Img/index.png)

### discover.html

![discover](../../Img/discover.png)

### comments.html

![comments](../../Img/comment.png)

## Petit hack pour répéter son header/footer sur plusieurs pages

Alors, ceci est une méthode un peu laborieuse pour arriver à créer une page avec votre header/footer tout seul et pour ensuite le répéter sur toutes vos pages. Cela vous permettra de ne pas avoir à modifier toutes vos pages si vous avez besoin d'éffectuer un changement dans votre header/footer.

Nous allons utiliser une `iframe`. C'est une sorte de fenêtre sur votre page qui affiche une autre page. 

1. Créez votre page `index.html`
2. Créez votre page `header.html`/`footer.html`
3. Créez votre feuille de style `style.css`
4. Créez votre feuille de style `header.css`/`footer.css`(optionnel)
5. Placez le code suivant dans votre page `index.html` là où vous voulez que votre header/footer apparaisse: `<iframe src="header.html" seamless></iframe>`
6. Placez le code suivant dans votre `style.css`: `iframe[seamless]{border: 0; width: 100%;}`
7. Tadaamm! Vous avez votre header qui s'affiche.

### Petite précision

Cette méthode est plus un hack qu'une bonne pratique. On n'a pas encore vu les outils nécessaire quant à la réalisation de composant réutilisable. Du coup, il faut un petit peu trafiquer le code pour arriver à nos fins.

#### Le style de header/footer

Même si votre header/footer s'affiche sur votre page index sur laquelle vous avez lié votre feuille de style, elle est tout de même considérer comme une autre page. N'oubliez donc pas  de lier votre feuille de style dans header/footer aussi. Pour ce faire, vous pouvez utiliser la fonction `@import`de CSS pour importer votre feuille de style dans la feuille de style de header/footer.

```css
@import "style.css";
```

#### Le background-color de body

Il est également possible que votre header/footer s'affiche en prenant en compte le background-color définit dans votre feuille de style principale et du coup vous aurez un gros bloc de cette couleur qui se place par dessus certains éléments sur votre page. Pour ce faire précisez dans la feuille de style de header/footer que le background-color doit être transparent. `body{background-color: transparent;}`

#### Les liens

Si vous avez des liens dans votre header/footer, ceux-ci vont s'ouvrir dans votre iframe par défaut. Pour changer cela il faut ajouter un attribut `target:_top` à vos liens.

### Exemple d'utilisation

`index.html`

```html
<head>
  <title>Soundwave</title>
  <link rel="stylesheet" href="./css/style.css">
</head>
<body>
  <iframe src="header.html" seamless></iframe>
  <main>
    <img src="./assets/Girl.png" alt="girl" class="girl">
  </main>
</body>
```

`header.html`

```html
<link rel="stylesheet" href="./css/header.css">
<header>
  <div class="title">
    <a href="index.html" target="_top">
      <img src="./assets/Logo.png" alt="logo">
      <span>Soundwave</span>
    </a>
  </div>
  <nav>
    <a class="nav" href="discover.html" target="_top">Discover</a>
    <a class="nav" href="comments.html" target="_top">Comments</a>
  </nav>
</header>
```

`header.css`

```css
@import "style.css";

body{
  background-color: transparent;
}
```
