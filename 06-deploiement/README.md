# TD déploiement

Dans ce TD, nous allons utiliser une solution dite « serverless », [Zeit
Now](https://zeit.co/), pour mettre en ligne notre site web BePolyglot.

## Étape 1

Now nous permet de mettre en ligne notre site web en lançant une ligne de
commande dans un terminal. Pour pouvoir lancer cette commande, nous avons
besoin de deux outils : NodeJS et npm. Pour avoir ces deux outils, il suffit en
fait d'installer NodeJS. Théoriquement, il suffit de télécharger la dernière
version sur [le site officiel](https://nodejs.org/en/download/). Mais sur les
machines de l'

### Installer NodeJS sur votre machine perso

Si vous utilisez votre machine personnelle, ou si vous voulez installer NodeJS
chez vous, il vous suffit de télécharger la dernière version sur [le site
officiel](https://nodejs.org/en/download/), puis de l'installer. Ouvrez ensuite
le menu démarrer, et tapez `cmd`. Un terminal s'ouvre. Dans celui-ci, vous
pourrez vérifier que tout est bien installé en tapant :

```console
$ node -v
v12.12.0
$ npm -v
6.11.3
```

Si les deux commandes affichent un numéro de version (pas forcément le même que
dans l'exemple ci-dessus), alors l'installation s'est bien passée.

### Installer NodeJS sur une machine de l'IUT

Sur une machine de l'IUT, nous allons devoir utiliser une version un peu
spécifique de NodeJS, « portable ». Le but est d'installer NodeJS et tous ses
composants sur votre `Z:` afin que vous le retrouviez sur n'importe quelle
machine.

Pour cela, rendez vous sur
[crazy-max/nodejs-portable](https://github.com/crazy-max/nodejs-portable/releases)
et téléchargez la dernière version en cliquant sur « nodejs-portable.exe » dans
la partie « Assets ».

Une fois le fichier téléchargé, placez-le dans un dossier « nodejs » sur votre
Z, puis exécutez-le. Un terminal s'ouvre. Tapez `1` pour installer NodeJS.
Appuyez sur entrée pour valider la version par défaut proposée. De même pour
l'architecture. L'installation se lance, cela dure quelques minutes.

Une fois l'installation terminée, vous pouvez taper `2` pour lancer NodeJS dans
le terminal. Appuyez ensuite sur entrée, et vous voilà dans un terminal dans
lequel vous pouvez utiliser NodeJS. Pour vérifier que tout est OK, tapez :

```console
$ node -v
v12.12.0
$ npm -v
6.11.3
```

Si les deux commandes affichent un numéro de version (pas forcément le même que
dans l'exemple ci-dessus), alors l'installation s'est bien passée.

## Étape 2

Nous pouvons maintenant installer l'outil de Now, qui nous permettra d'envoyer
les fichiers de notre site web sur leurs serveurs afin qu'ils soient mis en
ligne automatiquement. Pour cela, dans le terminal, tapez :

```console
$ npm install -g now
```

Vérifiez l'installation en tapant :

```console
$ now -v
16.3.1
```

## Étape 3

Pour pouvoir utiliser Now, nous avons besoin de créer un compte sur
https://zeit.co/signup?with-email=1. Créez un compte, puis dans le terminal,
tapez

```console
$ now login
```

Entrez votre adresse mail. Un mail vous sera envoyé. Cliquez sur le lien qu'il
contient, vous serez automatiquement connecté à votre compte Now dans le
terminal.

## Étape 4

Avant de mettre en ligne notre site web, nous allons régler un dernier détail.
Par défaut, Now utilise le nom du dossier dans lequel se trouvent nos fichiers
pour définir l'URL qui nous sera attribuée. Par exemple, si le dossier de mon
projet est nommé « siteweb » et que je suis identifié en tant que « drazik »
sur Now, alors l'URL sera`https://siteweb.drazik.now.sh`. Ce fonctionnement
nous oblige à utiliser le même nom de dossier sur toutes les machines à partir
desquelles on voudra faire le déploiement.

Pour éviter cette contrainte, nous allons spécifier le nom du projet dans un
fichier de configuration spécifique pour Now. Dans le dossier de votre projet,
créez un fichier `now.json` et placez-y le contenu suivant :

```json
{
  "name": "nom-de-votre-site"
}
```

Remplacez `nom-de-votre-site` par le nom que vous souhaitez, sans utiliser
d'espace.

## Étape 5

Tout est prêt. Vous pouvez maintenant déployer votre site. Pour cela, dans le
terminal, déplacez-vous dans le dossier contenant votre projet, puis tapez :

```console
now
```

Nos fichiers sont envoyés sur les serveurs de Now, et celui-ci nous renvoie
deux URL :

* Une URL du type `https://monsiteweb-7gkvo8gd6.now.sh` : c'est l'URL unique correspondant au déploiement que vous venez d'effectuer
* Une URL du type `https://monsiteweb.username.now.sh` : c'est l'URL de production, qui pointe toujours sur le dernier déploiement de production effecté. Ici, puisque vous venez d'effectuer votre premier déploiement, il a automatiquement été considéré comme un déploiement de production. Pour faire un nouveau déploiement de production, il faudra spécifier le flag `--prod` (`now --prod`)
