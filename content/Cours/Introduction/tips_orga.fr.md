+++
title = "Tips : Organisation de la Fenêtre Visual Studio 2019"
weight = 1005
pre = "<b>1.5 </b>"
+++

## Affichage

L’onglet Affichage permet d’afficher des sous fenêtres dans Visual Studio.

![image1](/img/1.5/img01.png?height=300px)

La boite à outils permet de créer des éléments à l’intérieur de votre application de façon très simplifiée. Faîtes un drag and drop pour les placer. Ils se formaliseront à l’intérieur de votre code XAML automatiquement.
La fenêtre propriétés permet de gérer les attributs et évènements de chaque élément présent dans votre code XAML de manière simple. Il suffit de cliquer sur un élément directement dans votre fenêtre graphique, ou dans votre code XAML pour voir apparaître les attributs et évènements.
L’explorateur de solutions vous permet de naviguer entre les différents fichiers de votre projet.

## Extensions

Vous pouvez ajouter certaines extensions, comme celle de Github par exemple :

![image2](/img/1.5/img02.png?height=300px)

## Projet

Rendez-vous dans Projet pour ajouter des fichiers à votre solution, des fenêtres à votre application ou autre.

![image3](/img/1.5/img03.png?height=300px)

## Déboguer

Visual Studio vous permet de déboguer votre code afin qui vous puissiez détecter facilement vos erreurs. Le déboguage se fait seulement sur les fichiers .cs.

Un point d’arrêt (« breakpoint en anglais ») permet de s’arrêter lors de l’exécution du programme à une ligne de code spécifique. Cela est très pratique pour visualiser les valeurs de variables à l’intérieur du bloc {} dans lequel la ligne se trouve. On peut placer plusieurs breakpoints.
On ne peut placer un breakpoint sur une ligne que si cette dernière n’est pas vide (contient du code).

![image4](/img/1.5/img04.png?height=100px)

![image5](/img/1.5/img05.png?height=300px)

Pas à pas détaillé (F11) vous permet de continuer l’éxecution du programme ligne par ligne à partir du breakpoint précédemment spécifié.
Pas à pas sortant permet de sortir du bloc et de continuer le déboguage.


Vous pouvez visualiser les variables comme décrit précédemment :

![image6](/img/1.5/img06.png?height=200px)

Vous pouvez même rajouter un espion sur une variable de votre code afin de visualiser sa valeur tout au long du déboguage. Rendez vous dans l’onglet Espion 1, puis cliquez sur Ajouter un élément à espionner. Vous pourrez alors rentrer le nom de la variable à suivre. 

La pile des appels permet de suivre correctement le parcours de votre application. En effet, dans un programme, plusieurs fonctions peuvent être appelées. Ces fonctions créent alors une pile avec au-dessus la fonction la plus récente qui a été appelée dans votre code. Dans l’image ci-dessous, on peut par exemple voir que la fonction Propose_Letter appelle la fonction change_Advance_Word.

![image7](/img/1.5/img07.png?height=200px)

