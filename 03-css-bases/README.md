# TD 3

Au cours des prochains TD, notre but est de faire en sorte que le site de la
marque Cristie Cookie ressemble à [la maquette qui nous est
fournie](https://www.figma.com/file/EXw4hlVqE6AYMY9d7Dhy5v/cristie-cookie?node-id=2%3A2).

Pour le moment, nous n'avons pas vu toutes les techniques permettant
d'implémenter ce design dans son ensemble. Dans ce TD, nous allons poser les
premières bases de style sur le site Cristie Cookie : 

* import des polices d'écriture
* définition des couleurs via des variables CSS
* implémentation de styles globaux
* implémentation de quelques classes :
  * zone utile (wrapper)
  * section (avec variantes de couleur)
  * bouton (avec variantes de couleur)

## Import des polices d'écriture

Les polices (fonts en anglais) utilisées dans les maquettes ne sont pas
proposées par défaut dans les différents systèmes d'exploitation. Par
conséquent, nous allons devoir les importer pour les rendre utilisables dans
nos pages.

Pour cela, nous allons utiliser le service [Google
Fonts](https://fonts.google.com/). Ce service nous permet de sélectionner un
certain nombre de polices et de variantes de celles-ci, et de récupérer un bout
de code HTML permettant de les importer sur nos pages.

En premier lieu, il faut que nous fassions une liste des polices et de leurs
variantes utilisées dans la maquette. Pour cela, rendez-vous dans Figma, plus
précisément sur la frame
[Fonts](https://www.figma.com/file/EXw4hlVqE6AYMY9d7Dhy5v/cristie-cookie?node-id=23%3A122)
qui liste tous les styles de texte utilisés dans la maquette.

Une fois cette liste faite, allez sélectionner toutes les polices et leurs
variantes nécessaires dans Google Fonts, puis copiez-collez le code fournit par
Google Fonts dans votre fichier `base.pug` et votre fichier CSS.

## Définition des couleurs via des variables CSS

La maquette nous présente toutes les couleurs utilisées dans la frame
[Colors](https://www.figma.com/file/EXw4hlVqE6AYMY9d7Dhy5v/cristie-cookie?node-id=25%3A123).
Nous pouvons donc relever chaque code couleur ainsi que son nom pour créer des
variables contenant chaque couleur, afin de ne pas nous répéter lors de
l'utilisation des couleurs et de faciliter le changement d'une couleur.

Grâce aux indications données par le document Figma, stockez les couleurs
utilisées par la maquette dans des variables CSS.

## Implémentation des styles globaux

## Implémentation des premières classes

### Zone utile (wrapper)

On voit sur la maquette que le contenu du site ne doit pas prendre toute la
largeur de la fenêtre. En analysant les différents éléments, on peut déterminer
que la largeur maximum du contenu est de `1024px`. Nous avons donc besoin d'une
classe que nous pourrons appliquer à certains éléments. Nommons-la `wrapper`.

Cette classe devra : 

* contraindre la largeur maximale de son contenu à `1024px`
* aligner son contenu au centre (pour cela, utilisez la propriété `margin` avec la valeur `auto` pour les marges gauche et droite)

Ecrivez cette classe CSS, puis affectez-la aux différents éléments nécessaires
afin que le contenu soit bien centré et avec une largeur maximale. N'hésitez
pas à ajouter de nouveaux éléments si nécessaire. Si vous avez besoin d'un
élément purement stylistique (aucune sémantique), vous pouvez utiliser
l'élément `div`.

### Section (avec variantes de couleur)

Sur la maquette, nous avons des sections, délimitées visuellement par une
couleur de fond et des marges. Ces sections contiennent un titre et du contenu
(textuel, bouton, iframe...).

Les sections n'ont pas toutes la même couleur. On peut voir 2 variantes :

* section sur fond orange, texte blanc
* section sur fond blanc, texte gris foncé

Mais toutes les sections ont aussi des caractéristiques en commun, notamment
leur marge interne verticale (`32px`).

Pour gérer tous les cas, nous pouvons donc écrire les classes CSS suivantes : 

* `.section` : définit les styles appliqués à toutes les sections
* `.section-default` : définit les styles appliqués aux sections avec texte noir et fond blanc
* `.section-primary` : définit les styles appliqués aux sections qui utilisent la couleur de fond primaire

Essayez d'écrire chacune des 3 classes et des les appliquer aux bons éléments
afin que les différentes sections aient la bonne couleur de fond et de texte.

### Bouton (avec variantes de couleur)

Utilisez la même démarche que pour les sections, mais pour les boutons. A
nouveau, les boutons ont 2 couleurs possibles, mais certaines propriétés sont
partagées par tous les boutons.
