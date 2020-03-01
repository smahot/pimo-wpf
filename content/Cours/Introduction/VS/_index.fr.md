+++
title = "Visual Studio"
weight = 1001
pre = "<b>1.1 </b>"
+++


Visual studio est un ensemble complet d’outils permettant la création d’applications, notamment des applications WPF qui sont le sujet du cours. WPF est une approche de Windows visant à gérer l’interface graphique d’une application (GUI).  

Afin de télécharger Visual Studio 2019, rendez-vous sur [https://visualstudio.microsoft.com/vs/](https://visualstudio.microsoft.com/vs/)

Plusieurs choix d’installation sont disponibles, choisissez *Community 2019*. Le téléchargement de l’installateur commence alors. 

![image1](/img/1.1/im1.png?height=300px)

Cliquez sur continuer. 

![image2](/img/1.1/im2.png?height=300px)

Seules les deux charges de travail suivantes vous seront nécessaires afin de créer des applications WPF, cochez-les :  

![image3-4](/img/1.1/im3-4.png?height=200px)

Les étapes suivantes ne sont pas obligatoires, il est libre à vous de les modifier (non conseillé sauf pour le choix du langage au sein de Visual Studio 2019) : 

 - Vous pourrez choisir d’installer certains composants individuels. Cependant, ne pas en rajouter parmi ceux déjà cochés ne nuira pas au bon fonctionnement de WPF. 

![image5](/img/1.1/im5.png?height=300px)

 - Vous pouvez ensuite choisir le langage : 

![image6](/img/1.1/im6.png?height=300px)

 - Et enfin l’emplacement d’installation de Visual Studio 2019 : 

![image7](/img/1.1/im7.png?height=300px)

Cliquez sur *Installer* en bas à droite. 

Le téléchargement prend en moyenne quelques dizaines de minutes. Lorsque ce dernier est terminé, redémarrez l’ordinateur. 

Lancez ensuite Visual Studio 2019. 

Connectez-vous avec un compte Windows créé au préalable (sinon, Visual Studio ne sera plus effectif au bout de 30 jours).

![image8](/img/1.1/im8.png?height=300px)

Choisissez pour le projet :

![image9](/img/1.1/im9.png?height=100px)

Nommez le projet « Premiere_App_WPF » et créez le.


![image10](/img/1.1/im10.png?height=300px)

![image11](/img/1.1/im11.png?height=400px)

L’explorateur de solutions à droite [1] permet de naviguer entre les différents fichiers du projet. 

Pour placer des éléments à l’intérieur de notre page, il existe deux possibilités : 

1. *XAML* est un langage qui est utilisé dans le but de simplifier la disposition des éléments au sein de notre application.
    XAML utilise des balises (de la même manière que HTML) pour des applications Windows. On code alors directement notre XAML en bas de notre fenêtre Visual Studio pour faire apparaître les éléments.  
    Les éléments peuvent s’écrire de deux manières : 
     - Balises ouvrante/fermante (Ex : `<Button> </Button>`).  
     - Balises uniques (Ex :`<Button/>`) 

    On peut noter que les éléments peuvent s’imbriquer les uns les autres. On peut donc avoir une image à l’intérieur d’un bouton par exemple : `<Button <Image/> />`.

2. La boîte à outils située à gauche permet une approche simplifiée et plus intuitive pour la création d’éléments.
    Il suffit de glisser ce que l’on veut dans notre fenêtre. Notez que ce drag and drop implique une création de code automatique dans le fichier XAML.
    Notre interface graphique est gérée par le fichier XAML.

Par la suite, nous verrons comment créer des attributs pour gérer la taille par exemple ou des comportements spécifiques pour les éléments graphiques comme l’affichage de texte lorsqu’un bouton est cliqué. 

