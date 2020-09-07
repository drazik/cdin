# TD introduction

Dans ce TD, nous allons créer la structure HTML d'un blog constitué de trois
pages :

* Une page d'accueil listant des articles
* Une page qui liste les articles par auteur
* Une page d'article

Le but est d'utiliser au mieux les balises HTML afin de décrire la structure de
ces deux pages avec la bonne sémantiques.

Les maquettes sont visibles sur https://www.figma.com/file/cEgyaw22dkpsr7RbDttNgA/Blog?node-id=0%3A1

Vous devrez créer un compte sur Figma pour pouvoir inspecter les maquettes
(gratuit, sans publicité).

## Vérification de l'environnement

### Le navigateur web

Nous allons utiliser des navigateurs récents pour tester nos pages web.
Vérifiez que vous avez les navigateurs suivants, ou installez-les si besoin :

* Firefox https://www.mozilla.org/fr/firefox/new/
* Chrome https://www.google.com/intl/fr_fr/chrome/

### L'éditeur de texte

Pour écrire du HTML, nous avons besoin d'un éditeur de texte. Théoriquement, un
bloc-note suffit. Mais nous allons utiliser un éditeur spécialisé pour le code
(pas que HTML), qui va nous fournir des fonctionnalités comme de la coloration
syntaxique, de l'indentation automatique, etc...

Je vous suggère d'utiliser [Visual Studio
Code](https://code.visualstudio.com/). Toutefois, si vous avez déjà une
préférence pour un autre éditeur de code, gardez-le. N'importe quel éditeur
fera l'affaire.

## Page d'accueil

### Étape 1 : mise en place

Créez un dossier sur votre machine dans lequel vous mettrez les fichier de
votre site web. Par exemple, un dossier `site-web`. Dans ce dossier, créez un
fichier `index.html`.

Ouvrez le fichier `index.html` dans votre éditeur de code. Copiez-collez la
structure de base d'une page web que nous avons vu pendant le cours.

Ouvrez la page dans votre navigateur (vous pouvez double-cliquer sur le fichier
dans votre explorateur de fichier, il devrait s'ouvrir dans votre navigateur
par défaut).

### Étape 2 : code HTML du header

En premier lieu, nous allons créer le code HTML du header de la page.

IMAGE du header

Dans ce header, on trouve trois éléments :

* Un titre ("Watch my blog")
* Un paragraphe ("My thoughts...")
* Un menu de navigation (avec deux liens : "Home" et "By author")


### Etape 3 : code HTML du footer

Dans l'ordre visuel de la page, l'étape suivante serait logiquement la zone de
contenu principal. Mais nous allons d'abord écrire le code du footer, de
manière à avoir tous les éléments communs à toutes les pages. Nous nous
occuperons des éléments spécifiques à chaque page par la suite.

IMAGE du footer

Le footer est composé de deux éléments :

* Un paragraphe de copyright
* Un menu de navigation (avec deux liens : "Home" et "By author")

### Etape 4 : code HTML du contenu

Le contenu de la page d'accueil est une liste d'articles. Il y a en tout 9
éléments. Je vous conseille de n'en écrire qu'un seul au début, que vous
pourrez copier/coller lorsque celui-ci sera terminé.

IMAGE d'un item

Chaque élément est un lien, dans lequel se trouve :

* une image
* un titre
* un paragraphe de résumé
* l'image et le nom de l'auteur
* le temps de lecture


## Page de liste par auteur

### Etape 1 : mise en place

Créez un fichier `by-author.html`. Copiez-collez le code de la page
`index.html` dans ce fichier, de manière à partir sur la même base.

### Etape 2 : code du contenu de la page

Cette page est quasi similaire à la page d'accueil. La seule différence est
l'ajout d'un header dans la zone de contenu principal.

Dans ce header, on trouve les informations sur l'auteur des articles :

* Son nom
* Sa description
* Les liens vers ses réseaux sociaux (twitter, facebook)
* Son image

## Page d'article

### Etape 1 : mise en place

Créez un fichier `article.html`. Copiez-collez le code d'une des deux autres
pages dans ce fichier, de manière à récupérer les éléments communs à toutes les
pages.

### Etape 2 : code du contenu de la page

La page contient un article de blog. Elle est constituée :

* D'une image
* Du titre de l'article
* Du contenu de l'article

Le contenu de l'article est composé de :

* Titres
* Listes ordonnées
* Paragraphes
* Liens
* Un bloc de citation à la toute fin de l'article (à vous de trouver quelle balise utiliser pour celui-ci !)

## Conclusion

Vous venez de créer votre premier site web, constitué de 3 pages. Celui-ci est
pour le moment uniquement composé de HTML. Son contenu est donc bien structuré
et compris par une machine.

Toutefois, il nous reste encore un peu de travail pour arriver au résultat
visuel des maquettes. Ce qu'il nous manque, c'est du CSS. Ce sera le sujet de
la prochaine séance, lors de laquelle nous écrirons le code CSS permettant
d'arriver au résultat visuel souhaité.
