+++
title = "Les layouts"
weight = 3001
pre = "<b>3.1 </b>"
+++

- [a. GridPanel](#a-gridpanel)
- [b. StackPanel](#b-stackpanel)
- [c. WrapPanel](#c-wrappanel)
- [d. DockPanel](#d-dockpanel)
- [e. CanvasPanel](#e-canvaspanel)

## a. GridPanel

Grid est un outil qui permet de pouvoir placer des éléments (boutons, textbox…) sous la forme d’un quadrillage. On crée une grille comme suit :

```xml
<Grid></Grid>
```

Une fois que la grille a été créée, il faut définir le nombre de lignes et de colonnes que nous désirons attribuer à notre grille. Pour ce faire, nous devons, à l’intérieur de notre balisage Grid, utiliser Grid.ColumnDefinition et Grid.RowDefinition :

```xml
<Grid>
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="2*"/>
        <ColumnDefinition Width="1*"/>
        <ColumnDefinition Width="1*"/>
    </Grid.ColumnDefinitions>
    <Grid.RowDefinitions>
        <RowDefinition Height="2*"/>
        <RowDefinition Height="1*"/>
        <RowDefinition Height="1*"/>
    </Grid.RowDefinitions>
</Grid>
```

Dans cet exemple, nous définissons une grille de 3 lignes et 3 colonnes. Les attributs Width et Height permettent de déterminer la taille de la cellule. Le caractère `*` sert à obtenir des cellules de dimensions proportionnelle. Ainsi, la première colonne, de dimension 2* sera 2 fois plus grande que les colonnes 2 et 3 de taille 1* (dont on peut simplifier l’écriture dans notre code en la notant `*`). Par défaut, les lignes et colonnes seront étendues sur toute la fenêtre XAML. On peut aussi donner un nombre précis de pixel que l’élément occupera :

```xml
<ColumnDefinition Width="100"/>
```

Cette commande nous donnera une colonne étendue en largeur sur 100 pixels.

Une fois ces opérations effectuées, on peut alors remplir la grille en y plaçant des éléments. Nous devons alors indiquer dans quelle « case » nous voulons placer notre élément, et renseigner le numéro de la ligne et de la colonne qu’il occupera à l’aide des opérateurs Grid.Row et Grid.Column. Par défaut on prend la ligne et la colonne 0. Ces opérateurs sont à placer à l’intérieur de l’élément ajouté. Voici un petit exemple avec des boutons :

![image1](/img/3.1/img01.png?height=200px)

```xml
<Grid>
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="2*"/>
        <ColumnDefinition Width="1*"/>
    </Grid.ColumnDefinitions>
    <Grid.RowDefinitions>
        <RowDefinition Height="1*"/>
        <RowDefinition Height="2*"/>
    </Grid.RowDefinitions>
    <Button>Button 1</Button>
    <Button Grid.Column="1">Button 2</Button>
    <Button Grid.Row="1">Button 2</Button>
    <Button Grid.Column="1" Grid.Row="1">Button 4</Button>
</Grid>
```

On voit bien, à l’aide des trois premiers boutons, que lorsque l’on ne spécifie pas la ligne, la colonne, ou bien les deux, la position par défaut sera la position d’indice 0. Au contraire, on est parfois obligé d’expliciter ces deux informations (bouton 4).

Reprenons l’exemple précédent et imaginons que nous ne voulons plus 4 boutons mais 3, et que le bouton 3 occupe toute la deuxième ligne. On peut facilement augmenter le nombre de « cases » sur lesquelles s’étend notre élément à l’aide des fonctions Grid.ColumnSpan et Grid.RowSpan. Pour étendre un élément sur une ligne, on utilisera ColumnSpan, et donc, pour l’étendre sur une colonne on se servira de RowSpan.

```xml
<Grid>
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="2*"/>
        <ColumnDefinition Width="*"/>
    </Grid.ColumnDefinitions>
    <Grid.RowDefinitions>
        <RowDefinition Height="*"/>
        <RowDefinition Height="2*"/>
    </Grid.RowDefinitions>
    <Button>Button 1</Button>
    <Button Grid.Column="1">Button 2</Button>
    <Button Grid.Row="1" Grid.ColumnSpan="2">Button 3</Button>
</Grid>
```

C’est un outil puissant. Ainsi le résultat suivant :

![image2](/img/3.1/img02.png?height=200px)

Peut être obtenu en quelques lignes avec le code suivant :

```xml
<Grid>
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="*"/>
        <ColumnDefinition Width="*"/>
        <ColumnDefinition Width="*"/>
    </Grid.ColumnDefinitions>
    <Grid.RowDefinitions>
        <RowDefinition Height="*"/>
        <RowDefinition Height="*"/>
        <RowDefinition Height="*"/>
    </Grid.RowDefinitions>
    <Button Grid.ColumnSpan="2">Button 1</Button>
    <Button Grid.Column="3">Button 2</Button>
    <Button Grid.Row="1">Button 3</Button>
    <Button Grid.Column="1" Grid.Row="1" Grid.RowSpan="2" Grid.ColumnSpan="2">Button 4</Button>
    <Button Grid.Column="0" Grid.Row="2">Button 5</Button>
</Grid>
```

{{% exercice %}}
Essayez d’obtenir grâce à la grille le résultat suivant :
{{% /exercice %}}

![image3](/img/3.1/img03.png?height=200px)
{{% expand "Correction" %}}

```xml
<Grid>
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="*"/>
        <ColumnDefinition Width="*"/>
        <ColumnDefinition Width="*"/>
        <ColumnDefinition Width="*"/>
    </Grid.ColumnDefinitions>
    <Grid.RowDefinitions>
        <RowDefinition Height="*"/>
        <RowDefinition Height="*"/>
        <RowDefinition Height="*"/>
        <RowDefinition Height="*"/>
    </Grid.RowDefinitions>
    <Button Content="Top" Grid.Column="0" Grid.ColumnSpan="4"/>
    <Button Content="Bottom" Grid.Column="0" Grid.Row="3" Grid.ColumnSpan="4"/>
    <Button Content="Left" Grid.Row="1" Grid.RowSpan="2"/>
    <Button Content="Right" Grid.Column="3" Grid.Row="1" Grid.RowSpan="2"/>
    <Button Content="Center" Grid.Row="1" Grid.Column="1" Grid.RowSpan="2" Grid.ColumnSpan="2"/>
</Grid>
```

{{% /expand %}}

## b. StackPanel

Le Stack Panel est un autre élément qui vous permettra d’organiser votre fenêtre XAML. Il permet d’empiler les éléments les uns à la suite des autres. Cet enchaînement peut se faire verticalement ou alors horizontalement (par défaut il est vertical). Le Stack Panel se déclare de la façon suivante :

```xml
<StackPanel></StackPanel>
```

Comme dit plus haut, il va nous permettre de hiérarchiser les éléments de façon verticale :

![image4](/img/3.1/img04.png?height=200px)

```xml
<Grid>
    <StackPanel>
        <Button>button 1</Button>
        <Button>button 2</Button>
        <Button>button 3</Button>
        <Button>button 4</Button>
        <Button>button 5</Button>
        <Button>button 6</Button>
    </StackPanel>
</Grid>
```

Ou de façon horizontale :

![image5](/img/3.1/img05.png?height=300px)

```xml
<Grid>
    <StackPanel Orientation="Horizontal">
        <Button>button 1</Button>
        <Button>button 2</Button>
        <Button>button 3</Button>
        <Button>button 4</Button>
        <Button>button 5</Button>
        <Button>button 6</Button>
    </StackPanel>
</Grid>
```

Il faut remarquer que le Stack Panel ne tient pas compte de l’espace disponible pour son contenu. De plus le Stack Panel étire son contenu par défaut. Mais nous pouvons modifier ce phénomène en changeant la propriété HorizontalAlignment ou VerticalAlignment :

```xml
<StackPanel Orientation="Horizontal">
    <Button VerticalAlignment="Top">button 1</Button>
    <Button VerticalAlignment="Center">button 2</Button>
    <Button VerticalAlignment="Bottom">button 3</Button>
    <Button VerticalAlignment="Bottom">button 4</Button>
    <Button VerticalAlignment="Center">button 5</Button>
    <Button VerticalAlignment="Top">button 6</Button>
</StackPanel>
```

La modification de l’alignement va nous permettre d’avoir des boutons qui ne prennent pas tout l’espace :

![image6](/img/3.1/img06.png?height=200px)

{{% exercice %}}
Essayez d’obtenir grâce au Stack Panel le résultat suivant :
{{% /exercice %}}

![image7](/img/3.1/img07.png?height=200px)

> Indice : Aidez-vous de la fonction Margin, explications en tips

## c. WrapPanel

Le Wrap Panel placera chacun des éléments les uns après les autres horizontalement (par défaut) ou verticalement, jusqu’à ce qu’il n’y ait plus assez de place pour rajouter un nouvel élément, auquel cas il retournera à la ligne ou la colonne d’après. On déclare un Wrap Panel comme cela :

```xml
<WrapPanel></WrapPanel>
```

Chaque élément aura la hauteur ou la largeur du plus grand élément en fonction de l’orientation horizontale ou verticale du Wrap Panel, le Wrap Panel horizontal uniformisera les hauteurs d’une même ligne, le vertical d’une même colonne :

![image8](/img/3.1/img08.png?height=200px)

```xml
<Grid>
    <WrapPanel Width="150">
        <Button Width="50">Button 1</Button>
        <Button Width="50">Button 2</Button>
        <Button Width="50">Button 3</Button>
        <Button Width="50" Height="65">Button 4</Button>
        <Button Width="50">Button 5</Button>
        <Button Width="50">Button 6</Button>
    </WrapPanel>
</Grid>
```

La disposition des éléments dépend donc de leur taille et de la taille de la fenêtre. Pour que les éléments soient disposés de haut en bas, il faut changer l’orientation du Wrap Panel :

```xml
<WrapPanel Orientation="Vertical">
```

{{% exercice %}}
Essayez d’obtenir avec le Wrap Panel le résultat suivant :
{{% /exercice %}}

![image9](/img/3.1/img09.png?height=300px)

{{% expand "Correction" %}}

```xml
<WrapPanel VerticalAlignment="Top">
    <Rectangle Width="150" Height="150" Fill="White" Stroke="#FFFF0000" StrokeThickness="10"/>
    <Rectangle Width="150" Height="150" Fill="White" Stroke="#FFFF8400" StrokeThickness="10"/>
    <Rectangle Width="150" Height="150" Fill="White" Stroke="#FFF9FF02" StrokeThickness="10"/>
    <Rectangle Width="150" Height="150" Fill="White" Stroke="#FF048D04" StrokeThickness="10"/>
    <Rectangle Width="150" Height="150" Fill="White" Stroke="#FF0000FF" StrokeThickness="10"/>
    <Rectangle Width="150" Height="150" Fill="White" Stroke="#FF080E64" StrokeThickness="10"/>
    <Rectangle Width="150" Height="150" Fill="White" Stroke="#FFAB00FF" StrokeThickness="10"/>
</WrapPanel>
```

{{% /expand %}}

## d. DockPanel

Le Dock Panel est un outil qui permet de placer des éléments aisément à n’importe quel endroit de notre fenêtre XAML. Par défaut, le dernier élément sera placé au centre. Le Dock Panel se déclare comme suit :

```xml
<DockPanel></DockPanel>
```

Voici un exemple d’utilisation de Dock Panel qui en montre bien la pertinence :

![image10](/img/3.1/img10.png?height=200px)

```xml
<DockPanel>
    <Button DockPanel.Dock="Left">Ouest</Button>
    <Button DockPanel.Dock="Top">Nord</Button>
    <Button DockPanel.Dock="Right">Est</Button>
    <Button DockPanel.Dock="Bottom">Sud</Button>
</DockPanel>
```

Plusieurs choses sont à remarquer. On voit que la place des quatre premiers boutons est spécifiée à l’aide de la commande DockPanel.Dock, alors que celle du dernier bouton ne l’est pas, car par défaut la position du bouton est au centre. Entre les deux chevrons, on trouve le texte qui sera placé dans le bouton. Le premier bouton est placé à gauche, il prend donc tout l’espace de la colonne gauche. La largeur du bouton dépend de la taille du texte du bouton. Le second bouton est situé en haut de la fenêtre, il prend tout l’espace du haut qui n’est pas encore occupé par le premier bouton, et ainsi de suite…

Le problème de l’inégalité de l’épaisseur des boutons peut être résolu comme suit :

![image11](/img/3.1/img11.png?height=200px)

```xml
<Grid>
    <DockPanel>
        <Button DockPanel.Dock="Top" Height="50">Top</Button>
        <Button DockPanel.Dock="Bottom" Height="50">Bottom</Button>
        <Button DockPanel.Dock="Left" Width="50">Left</Button>
        <Button DockPanel.Dock="Right" Width="50">Right</Button>
        <Button>Center</Button>
    </DockPanel>
</Grid>
```

Enfin, on peut placer plusieurs boutons à gauche, plusieurs à droite …

![image12](/img/3.1/img12.png?height=200px)

```xml
<Grid>
    <DockPanel LastChildFill="False">
        <Button DockPanel.Dock="Top" Height="50">Top</Button>
        <Button DockPanel.Dock="Bottom" Height="50">Bottom</Button>
        <Button DockPanel.Dock="Left" Width="50">Left</Button>
        <Button DockPanel.Dock="Left" Width="50">Left</Button>
        <Button DockPanel.Dock="Right" Width="50">Right</Button>
        <Button DockPanel.Dock="Right" Width="50">Right</Button>
    </DockPanel>
</Grid>
```

{{% exercice %}}
Essayez d’obtenir avec Dock Panel le résultat suivant :
{{% /exercice %}}

![image13](/img/3.1/img13.png?height=200px)

{{% expand "Correction" %}}

```xml
<DockPanel>
    <Button Width ="150" Background="Black" DockPanel.Dock="Left"/>
    <Button Width ="150" Background="Black" DockPanel.Dock="Right"/>
    <Button Height="100" Background="Purple" DockPanel.Dock="Top"/>
    <Button Height="100" Background="Purple" DockPanel.Dock="Bottom"/>
    <Button Width ="75" Background="DarkBlue" DockPanel.Dock="Left"/>
    <Button Width ="75" Background="DarkBlue" DockPanel.Dock="Right"/>
    <Button Height="50" Background="RoyalBlue" DockPanel.Dock="Top"/>
    <Button Height="50" Background="RoyalBlue" DockPanel.Dock="Bottom"/>
    <Button DockPanel.Dock="Right"/>
</DockPanel>
```

{{% /expand %}}

## e. CanvasPanel

Le Canvas permet de placer des éléments en fonctions de coordonnées x et y. La Canvas ne fait absolument aucune modification par lui-même ; si par exemple deux boutons sont placés aux mêmes coordonnées, ils seront superposés et nous ne pourrons voir que le second bouton sur la fenêtre. Un Canvas se déclare de la façon suivante :

```xml
<canvas></canvas>
```

On renseigne les coordonnées des éléments de notre Canvas grâce aux quatre opérations suivantes, Canvas.Top, Canvas.Bottom, Canvas.Left et Canvas.Right :

![image14](/img/3.1/img14.png?height=200px)

```xml
<Canvas>
    <Button Canvas.Left="10">Haut Gauche</Button>
    <Button Canvas.Right="10">Haut Droite</Button>
    <Button Canvas.Left="10" Canvas.Bottom="10">Bas Gauche</Button>
    <Button Canvas.Right="10" Canvas.Bottom="10">Bas droite</Button>
    <Button Canvas.Top="96" Canvas.Left="104">Centre</Button>
</Canvas>
```

Le Canvas est surtout pratique pour créer des belles images, il l’est beaucoup moins pour la création d’une boîte de dialogue par exemple. C’est pourquoi on peut placer dans le Canvas plusieurs figures. Voici un exemple simple, le code suivant :

```xml
<Canvas>
    <Ellipse Fill="AliceBlue" Canvas.Left="47" Canvas.Top="10" Width="150" Height="200" Stroke="Black" StrokeThickness="10"/>
    <Rectangle Fill="Navy" Canvas.Left="30" Width="40" Height="80"/>
    <Line X1="10" Y1="25" X2="230" Y2="12" Stroke="Indigo" StrokeThickness="6"/>
    <Polygon Stroke="Red" Points="10,10 150,100 200,200 10,10"/>
</Canvas>
```

Nous donne le résultat suivant :

![image15](/img/3.1/img15.png?height=200px)

Pour placer l’élément, on choisit les coordonnées du point en haut à gauche de notre figure. La propriété Fill permet de remplir la forme créée avec une couleur prédéterminée ou alors avec une couleur donnée en caractères hexadécimaux. Par exemple, on peut remplir notre ellipse de jaune en écrivant Fill = "#FFFFFF00". La propriété Stroke permet de créer le contour de l’objet et la propriété StrokeThickness nous permet de choisir l’épaisseur de ce contour. Pour tracer un segment, il nous faut renseigner les coordonnées x et y de deux points qui seront ses points d’origine et d’arrivée. Le segment est une sorte de contour, c’est pourquoi on ne choisit pas sa couleur avec la propriété Fill mais avec la propriété Stroke. Enfin, pour créer une forme géométrique, un triangle par exemple, il faut renseigner les coordonnées des points de son sommet et ne pas oublier de fermer la figure en finissant par remettre les coordonnées du premier point de notre figure.

Comme nous l’avons dit plus haut, les éléments se superposent et apparaissent dans notre fenêtre en fonction de l’ordre dans lequel on les a créés. Mais imaginons qu’on veuille maintenant s’affranchir de cette contrainte. Dans notre exemple, on pourrait par exemple vouloir que notre ellipse ne soit pas cachée par le rectangle. Pour cela nous allons utiliser Panel.ZIndex :

```xml
<Canvas>
    <Ellipse Panel.ZIndex="1" Fill="AliceBlue" Canvas.Left="47" Canvas.Top="10" Width="150" Height="200" Stroke="Black" StrokeThickness="10"/>
    <Rectangle Panel.ZIndex="0" Fill="Navy" Canvas.Left="30" Width="40" Height="80"/>
    <Line Panel.ZIndex="3" X1="10" Y1="25" X2="230" Y2="12" Stroke="Indigo" StrokeThickness="6"/>
    <Polygon Panel.ZIndex="4" Stroke="Red" Points="10,10 150,100 200,200 10,10"/>
</Canvas>
```

A chaque élément nous associons un index grâce à Panel.ZIndex. Si deux éléments se superposent, celui avec le ZIndex le plus fort sera celui qui sera visible sur la fenêtre XAML. Ainsi, dans notre exemple, l’ellipse, d’index 1, a un plus grand ZIndex que le rectangle, d’index 0. Sur notre fenêtre, on voit donc bien que l’ellipse recouvre le rectangle :

![image16](/img/3.1/img16.png?height=200px)

Par défaut, le ZIndex a pour valeur 0.

{{% exercice %}}
Essayez d’obtenir grâce au Canvas le résultat suivant :
{{% /exercice %}}

![image17](/img/3.1/img17.png?height=200px)

{{% expand "Correction" %}}

```xml
  <Canvas>
        <Rectangle Width="500" Height="170" Fill="Red" Canvas.Left="170" Canvas.Top="60"/>
        <Rectangle Width="700" Height="170" Fill="Red" Canvas.Left="70" Canvas.Top="170"/>
        <Rectangle Width="150" Height="80" Fill="LightSkyBlue" Canvas.Left="450" Canvas.Top="85"/>
        <Rectangle Width="150" Height="80" Fill="LightSkyBlue" Canvas.Left="215" Canvas.Top="85"/>
        <Ellipse Width="150" Height="150" Fill="Black" Canvas.Left="120" Canvas.Top="230"/>
        <Ellipse Width="150" Height="150" Fill="Black" Canvas.Left="550" Canvas.Top="230"/>
        <Button Content="Car" Canvas.Bottom="20" Canvas.Right="330" FontSize="50" Padding="20,5,20,5"/>
     </Canvas>
```

{{% /expand %}}

Pour aller plus loin…

{{% exercice %}}
Reproduisez, à l’aide de Grid et de Canvas, la figure suivante :
{{% /exercice %}}

![image18](/img/3.1/img18.png?height=200px)

---

{{% button href="/exercices/c3/part1/" %}}Lien vers les exercices{{% /button %}}