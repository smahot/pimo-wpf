+++
title = "Présentation de XAML"
weight = 1002
pre = "<b>1.2 </b>"
+++

- [a. Définitions et caractéristiques](#a-définitions-et-caractéristiques)
- [b. Le fichier XAML](#b-le-fichier-xaml)

#### a. Définitions et caractéristiques

Ceux qui sont familiers avec des langages comme HTML, voire même XML, ne seront pas trop perdus pour cette partie. Ici, je vais vous expliquer comment est structuré le fichier xaml de votre projet wpf.

Tout d’abord, en lançant votre projet, vous avez remarquez que deux fichiers se créent. Un en C#, l’autre en XAML.

Le fichier C# possède le strict minimum pour lancer l’application. Le initializeComponent() est ce qui fait prendre vie à tout le code, si vous voulez.

![image1](/img/1.2/im1.png?height=400px)

Pour l’instant, nous ne nous occuperont pas de ce fichier.

Pour éclaircir un peu ce qu’est XAML (à prononcer Xammel apparemment), voilà une définition :

- XAML est un langage déclaratif qui permet la description de données structurées. Un langage déclaratif, pour faire simple, définit une structure, mais ne donne pas les moyens de la construire. Ce sera le rôle de C#, à partir des données de XAML, de créer cette structure. C’est pourquoi vous ne pouvez pas vous passer de C#.
- XAML utilise, à l’instar d’autres langages cités précédemment (HTML…), utilise des balises pour structurer ses informations. On est plus proche de ce fait d’un XML que d’un JSON dans ce cas.

Une balise est « une unité syntaxique délimitant une séquence de caractère ou marquant une position précisée à l’intérieur d’un flux de caractère »… Bon, pour faire simple, vous pouvez considérer ces balises comme des blocs contenant de l’information que vous assemblez entre eux pour faire une pyramide/projet.

Au cours de ces chapitres, vous croiserez deux types de balises :

- Les doubles balises
- Les balises uniques

Si vous avez fait du XML, vous avez forcément utilisé ce système de double balise :

- `<truc>Bonjour<\truc>` :

Vous définissez un élément ‘’truc’’ et vous lui donnez la valeur Bonjour. Plutôt simple. La balise ouvrante est toujours de la forme `<x>`, et celle fermante `<\x>`. Vous pouvez mettre des balises dans des balises. C’est pourquoi il faut faire attention à toujours placer la balise fermante dès que possible (à noter que Visual Studio crée la balise fermante automatiquement).  
Mais il n’y a pas que ça. Et j’aurais tendance à dire que pour ce que vous allez voir dans ces premiers chapitres, vous serez plus amené à utiliser des balises uniques, de cette forme :

- `<truc caract1 carct2 />` :

Vous définissez un élément  ‘’truc’’ avec des caract1 et caract2. Pas de balise fermante, juste de l’information.
Voilà ce léger point sur les balises fermé !

#### b. Le fichier XAML

Portez votre attention sur le fichier XAML :

![image2](/img/1.2/im2.png?height=400px)

Si vous avez bien suivi le point sur les balises, vous voyez que le fichier XAML prend la forme :

```xml
<Window :info…>
    <grid>
    </grid>
</Window>
```

Il y a deux parties : la fenêtre (Window) et la grille (Grid) à l’intérieur. Ne vous occupez pas de ce qui est déclaré dans la fenêtre, Visual studio se charge de générer le bon code pour cette partie. Vous pouvez cependant modifier la taille de la fenêtre et son titre sur la ligne : Title="MainWindow" Height="450" Width="800">

Modifiez la fenêtre en jouant sur Height et Width : essayez d’obtenir une fenêtre de 300 sur 400, puis une de 800 sur 400.

300 par 400 :
![image3](/img/1.2/im3.png?height=300px)

800 par 400… Ca rentre à peine dans la fenêtre de visualisation !
![image4](/img/1.2/im4.png?height=300px)

{{% expand "Correction" %}}

```xml
<!-- remplacez cette ligne -->
Title="MainWindow" Height="300" Width="400">

Title="MainWindow" Height="800" Width="400">
```

{{% /expand %}}

Là où ça devient vraiment intéressant pour nous, ce sont les balises grid. Window, c’est en quelques sorte le « contour » de la fenêtre. Grid est ce qu’il y a à l’intérieur de la fenêtre. Pour les exemples qui suivront, et quand vous aurez à ajouter quelque chose dans la fenêtre, ce sera entre ces balises grid qu’il faudra ajouter votre code.

Drag’n’droppez un bouton de la Toolbox sur la fenêtre blanche. Tadaaah ! Quelque chose est apparue entre les balises grid : une balise Button !

![image5](/img/1.2/im5.png?height=300px)

```xml
    <Button Content="Button" HorizontalAlignment="Left" Margin="302,179,0,0" VerticalAlignment="Top" Width="75"/>
```

Tout d’abord, vous observez qu’il s’agit d’une balise unique, et c’est comme ça que nous déclarerons la plupart de nos objets. C’est pratique, les attributs sont déclarés à la suite et tout le monde s’y retrouve. A noté que si deux objets se superposent, celui au-dessus sera celui déclaré le dernier.

Autre chose : de la même façon qu’XML, vous pouvez mettre des commentaires. Pour cela, il faudra placer votre commentaire entre `< !-- ‘’Ceci est un commentaire’’ -->`.

![image6](/img/1.2/im6.png?height=300px)

Dans cet exemple, deux boutons sont définis, mais seul 1 apparaît. Si vous regardez bien le code, vous verrez qu’un des deux boutons est en vert, est commenté car entre < !-- et -->.
