+++
title = "Tips : Git"
weight = 1004
pre = "<b>1.4 </b>"
+++

Git est un outil de versionning extrêmement puissant qui simplifie grandement la vie des développeurs.

Avez-vous déjà eu plusieurs versions d’un projet dans un répertoire, nommées de telle sorte :

Nom_projet_v1, Nom_projet_v2, Nom_projet_v3 ?

Git permet d’éviter cela en créant des versions à votre fichier.

De plus, Git permet aux groupes de développeurs de travailler efficacement sur un projet notamment en précisant qu’une ligne de code a été modifiée par telle personne.
Nous pouvons utiliser Git que ce soit sur le site Github [https://github.com/](https://github.com/)[1], sur la console [CMD pour Windows, Terminal pour Linux](2) ou encore avec une extension installable directement sur Visual Studio[3].

Nous utiliserons dans ce cours la troisième possibilité : rendez vous dans extensions placé dans la boite à outils en haut de Visual Studio. Cliquez ensuite sur « Gérer les extensions ». Cherchez l’extension « Github Extension for Visual Studio ». Elle ressemble à ça, téléchargez la:

![image1](/img/1.4/img01.png?height=100px)

Relancez Visual Studio 2019.
Vous pouvez alors utiliser Git en le choisissant en bas à droite de la barre bleue l’extension.
Dans l’explorateur de solutions, choisissez de vous connecter avec Github. Il faudra préalablement vous avoir créé un compte. C’est facile, ne prend pas beaucoup de temps, et vous en aurez toujours besoin pour plus tard !

![image2](/img/1.4/img02.png?height=400px)

Voici un lien qui explique bien les différentes commandes à utiliser pour Git : [https://rogerdudler.github.io/git-guide/](https://rogerdudler.github.io/git-guide/).

Un repository est un dossier dont Git traque les modifications. Le fichier qui permet cette traque se nomme .git. .git traque donc tous les fichiers dans le repository et dans les sous-dossiers de ce repository.

Il est possible d’avoir plusieurs repositories (pour différents projets).

Git peut donner 3 états différents pour chaque fichier à l’intérieur du repository :

- Modified -> des fichiers ont été changés mais pas encore de commit.  Git checkout master pour revenir là où on était.
- Staging -> On ajoute les fichiers dont on veut commit
- Commited -> Tous les fichiers qui étaient dans staging on été commited.

Lorsque des modifications ont été effectuées et amènent à une potentielle version de l’application, il est possible de stage certains fichiers puis de commit ces derniers.

Un commit représente une version globale d’un ensemble de fichiers. Il est possible de naviguer entre les différents commits effectués.

On peut checkout ou revert ou reset un commit (du moins dangereux au plus dangereux) :

1. Checkout commit permet de revenir à un ancien commit pour voir son code.
2. Revert commit permet d’annuler un commit sans le supprimer. Cela va créer un nouveau commit (reverse de celui dont on a revert) qui annule toutes les modifications du commit en question.
3. Reset commit va revenir au commit spécifié mais supprimer tous les commits après celui spécifié. Cependant dans l’éditeur de texte nous aurons le code du plus récent commit en guise de sécurité (il est alors possible de faire un commit qui symbolisera tous ceux qui ont été supprimés). Faire git reset –hard pour éviter de garder les codes des récents commits.

Dans l’explorateur de solutions, un fichier vert représente un tout nouveau fichier (qui n’a jamais été stagé ou quoi que ce soit), un fichier orange représente un fichier qui a été modifié puis stagé mais pas encore commited.

Git branch -a permet de visualiser toutes les branches qui existent et voir sur laquelle nous nous trouvons.
Au lieu de créer la branche et de checkout pour y aller, on peut faire directement git checkout -b name_branch
Pour changer de branche, on utilise git checkout branch.

Tutoriel  :

1. git init
2. git add file1 file2 file3
    - git rm –cached file1
3. git status
4. git add . (pour stager tous les fichiers du dossier)
5. git commit -m “My message for this commit”
6. git log pour voir tous les commits effectués
7. git branch new_feature
