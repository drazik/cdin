# TD 2

Dans ce TD, nous allons reprendre comme base le code du TD précédent, et nous
allons le modifier pour régler les problèmes de répétition de code qui sont
présents, en utilisant Pug.

## Mise en place

Comme nous l'avons vu dans le cours, pour transformer nos fichiers Pug et
fichiers HTML, nous allons utiliser Parcel. Rien ne nous y oblige, mais Parcel
nous apporte des fonctionnalités très pratiques :

* Serveur de développement avec rafraichissement automatique
* Découverte automatique des fichiers à compiler (à partir du point d'entrée)
* Optimisations automatiques (minification du HTML, optimisation des images)

Pour installer Parcel, il faut déjà que nous initialisons npm dans notre
projet. Pour cela, ouvrez un terminal (powershell sur Windows). Si vous ne vous
souvenez plus comment faire, reportez vous au sujet du TD 1. Dans ce terminal,
entrez la commande suivante :

```console
npm init -y
```

Cela aura pour effet de créer un nouveau fichier dans votre projet :
`package.json`. Ce fichier va avoir une double utilité :

* Lister les modules dont dépend notre projet (on appelle ça des "dépendances", Parcel en sera une)
* Permettre de définir des scripts permettant d'utiliser les dépendances qui exposent des outils en ligne ce commande

Commençons par installer Parcel. Pour cela, entrez dans le terminal : 

```console
npm install --save-dev parcel-bundler
``` 

Une nouvelle ligne apparaît sous la section `devDependencies` du fichier
`package.json`. Cela indique que nous avons bien ajouté `parcel` comme une
dépendance de développement dans notre projet.

Nous pouvons maintenant ajouter un script dans la section `scripts`, afin
d'utiliser Parcel. Nous allons ajouter un premier script permettant de lancer
le serveur de développement de Parcel. Pour le moment, nous n'allons pas écrire
de code Pug mais simplement demander à Parcel de servir nos fichiers HTML.

```json
"scripts": {
  "serve": "parcel index.html"
}
```

Sauvegardez le fichier, puis dans votre terminal, entrez la commande suivante : 

```console
npm run serve
```

En retour, Parcel devrait vous dire que le serveur de développement est lancé
sur `http://localhost:1234`.

## Conversion du code HTML en code Pug

Nous allons commencer par convertir le code HTML existant en code Pug, sans
chercher à tirer parti de l'héritage ou des mixins dans un premier temps. Nous
allons faire une simple traduction HTML => Pug.

Premièrement, renommez les 3 fichiers HTML en fichiers Pug :

* `index.html` => `index.pug`
* `cookies.html` => `cookies.pug`
* `a-propos.html` => `a-propos.pug`

Puis modifiez le script `serve` dans le fichier `package.json` pour indiquer que le point d'entrée est maintenant le fichier `index.pug` :

```json
"scripts": {
  "serve": "parcel index.pug"
}
```

Arrêtez le serveur de développement en cours d'exécution (CTRL+C), puis
relancez en un. Parcel détecte automatiquement que nous utilisons des fichiers
Pug et installe donc les dépendances nécessaires pour nous. Une fois
l'installation des dépendances terminéee, vous devriez avoir une erreur comme
celle-ci :

```console
Server running at http://localhost:1234
🚨 Build failed.

@parcel/core: Failed to resolve 'index.html' from './index.pug'

@parcel/resolver-default: Cannot load file './index.html' in './'.
```

Cette erreur indique que Parcel voir que nous avons un lien vers le fichier
`index.html`, il essaye donc de le lire. Mais ce fichier n'existe plus, il a
été renommé en `index.pug`. Il faut donc modifier les noms de fichiers dans
tous nos liens, sur les 3 pages.

Cette simple modification nous permet de ne plus avoir d'erreur, et de voir
notre site dans le navigateur. Mais pour tirer le meilleur parti de Pug, il
faut que nous utilisions sa syntaxe. En vous appuyant sur les slides du cours,
essayez de transformer la syntaxe des 3 fichiers en syntaxe Pug. N'essayez pas
d'utiliser de l'héritage ou des mixins pour le moment. Faites une traduction
naïve d'une syntaxe vers l'autre.

## Utilisation de l'héritage

Une fois que nos 3 pages ont été traduites en Pug avec succès, nous pouvons
commencer à mettre une première couche afin d'éviter a répétition de code. Nous
allons commencer par tirer profit de l'héritage de templates.

Pour ça, il faut d'abord identifier la structure qui est commune aux 3 fichiers
Pug. Puis la copier dans un nouveau fichier que nous appelerons `base.pug`.
Dans ce fichier, il faut maintenant ajouter des `block` là où les pages
pourront insérer leur propre contenu. Pensez à donner à chaque `block` un nom
qui lui est unique.

Enfin, une fois les `block` en place, vous pourrez modifier les fichiers des
pages pour les faire hériter du fichier `base.pug`, et définir le contenu de
chaque bloc pour chaque page.

## Utilisation des mixins

Une fois l'héritage mis en place, nous pouvons nous occuper des dernières
répétitions de code qui subsistent dans nos pages.

Il s'agit de répétitions entre la page `index.pug` et la page `cookies.pug`,
qui présentent toutes les deux une liste des cookies, avec la même structure de
contenu.

La page `index.pug` présente 3 cookies sélectionnés par l'équipe, et la page
`cookies.pug` présente l'ensemble des cookies vendus par la marque.

Il convient donc de :

* Analyser le bout de contenu qui pourrait être extrait dans une mixin et l'extraire dans une mixin dans un nouveau fichier
* Identifier les paramètres que devrait prendre en entrée cette mixin
* Inclure le fichier contenant la mixin dans les 2 fichiers qui en ont besoin
* Remplacer les bouts de code par des appels à la mixin avec les bons paramètres
