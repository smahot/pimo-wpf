+++
title = "Les événements"
weight = 2002
pre = "<b>2.2 </b>"
+++

- [1. Comment affecter un événement à un objet](#1-comment-affecter-un-%c3%a9v%c3%a9nement-%c3%a0-un-objet)
- [2. Liste des événements](#2-liste-des-%c3%a9v%c3%a9nements)
- [3. Les événements routés](#3-les-%c3%a9v%c3%a9nements-rout%c3%a9s)
  - [a. Direct Event](#a-direct-event)
  - [b. Bubbling Event](#b-bubbling-event)
  - [c. Tunnel Events](#c-tunnel-events)

En WPF, un événement est déclenché lorsqu’une action de l’utilisateur interagit avec les objets (bouton, image...) dans la fenêtre affichée. Ces événements permettent d’impacter l’environnement et des méthodes peuvent être rattachées à ceux-ci.

## 1. Comment affecter un événement à un objet

Pour affecter un évènement à un objet :

- Sélectionner l’objet.

![image1](/img/2.2/img01.png?height=300px)

- Choisir un évènement dans le menu “propriétés” de l’objet (en bas à droite de votre environnement Visual studio)

![image2](/img/2.2/img02.png?height=300px)

- Lorsque vous double-cliquez sur un évènement, vous êtes redirigés dans le document .cs. Une fonction a été créée.  

![image3](/img/2.2/img03.png?height=100px)

- A vous de remplir cette méthode en fonction de ce que vous attendez de l’évènement. Cette fonction sera exécutée lorsque l’évènement se sera activé. On peut par exemple demander l’affichage d’un message lorsque le bouton est cliqué :

```xml
private void Button_Click(object sender, RoutedEventargs e)
{
   MessageBox.Show("Hello World!");
}
```

## 2. Liste des événements

Vous trouverez ici quelques exemples mais nous vous invitons à en découvrir plus par vous-même dans la barre d’outils des évènements.

| Nom de l’évènement  | Comment l’activer ?                                       |
| ------------------- | --------------------------------------------------------- |
| Click               | Quand on clique sur le bouton                             |
| KeyDown             | Une touche du clavier est enfoncée                        |
| KeyUp               | Une touche du clavier est relâchée                        |
| TextInput           | Une touche correspondant à du texte est frappée           |
| MouseDown           | Un bouton de la souris est enfoncé                        |
| MouseLeftButtonDown | Le bouton gauche de la souris est enfoncé                 |
| MouseLeftButtonUp   | Le bouton gauche de la souris est relâché                 |
| MouseMove           | La souris est placée au-dessus d’un élément               |
| MouseEnter          | La souris est sur un objet                                |
| MouseLeave          | La souris quitte un objet                                 |
| DragEnter           | Un objet commence à être glissé avec la souris            |
| DragLeave           | Un objet est déposé avec la souris au-dessus d’un élément |
| DragOver            | Un objet est glissé avec la souris au-dessus d’un élément |
| Drop                | Un objet est déposé avec la souris au-dessus d’un élément |

## 3. Les événements routés

Quand un événement est émis par un élément de l’arbre visuel, il est propagé aux conteneurs successifs de cet élément. L’élément qui a déclenché l’événement est appelé élément source. Le sens de propagation est déterminé par la stratégie de routage.

C’est une notion importante à connaitre afin de bien comprendre comment les événements sont gérés au sein de la structure que l’on a créée.

Il existe trois types d’événements routés :

- Direct Event
- Bubbling Event
- Tunneling Event

### a. Direct Event

Les événements directs sont des événements qui sont seulement activés par l’élément dans lequel l’événement est implémenté. L’évènement n’est pas propagé.

Par exemple, l’événement que nous avons créé un peu plus haut est un événement direct.

{{% exercice %}}
Créez un bouton avec un événement direct : lorsque l’on clique sur ce bouton, une boite de texte s’ouvre avec « First Event » écrit dedans.
{{% /exercice %}}

![imageex1](/img/2.2/imgExemple1.png?height=300px)

{{% expand "Correction XAML" %}}

```xml
    <Button x:Name="bouton_cible" Content="Button" HorizontalAlignment="Left" Height="105" Margin="302,150,0,0" VerticalAlignment="Top" Width="189" MouseEnter="Button_Click"/>
```

{{%/expand%}}

{{% expand "Correction C#" %}}

```xml
    private void Button_Click(object sender, RoutedEventArgs e)
        {
            MessageBox.Show("First Event !");
        }
```

{{%/expand%}}


{{% exercice %}}
Toujours sur ce même bouton, rajoutez un événement lorsque la souris passe sur le bouton, le bouton change de couleur.
{{% /exercice %}}

{{% expand "Correction XAML" %}}

```xml
    <Button x:Name="bouton_cible" Content="Button" HorizontalAlignment="Left" Height="105" Margin="302,150,0,0" VerticalAlignment="Top" Width="189" MouseEnter="mouse_color1"/>
```

{{%/expand%}}

{{% expand "Correction C#" %}}

```xml
    private void mouse_color1(object sender, MouseEventArgs e)
        {
            bouton_cible.Background = Brushes.Blue;
        }
```

{{%/expand%}}

### b. Bubbling Event

L’événement est traité au niveau de l’élément source puis successivement par chaque niveau de conteneur (dans le sens montant) jusqu'à la racine de l’arbre. D’où l’analogie avec une bulle qui remonte à la surface.

Pour la suite, nous allons considérer l’arbre suivant :

```txt
 - Window
    - Grid
       - Rectangle
```

Voyons comment cela fonctionne avec un exercice :

- Créer une grille que vous pouvez colorer pour une meilleure visibilité
- Dans cette grille, insérez un rectangle

![image5](/img/2.2/img05.png?height=300px)

 La structure de votre document est donc la suivante :

 ```txt
 - Window
    - Grid
       - Rectangle
 ```

Dans un premier temps, ajouter un évènement *mouseDown* à la Window.

![image6](/img/2.2/img06.png?height=100px)

Lancez le programme.
Cliquez sur le rectangle ou la grille. Que se passe-t-il ?  

![image7](/img/2.2/img07.png?height=200px)

En effet, le message Window apparait car l’événement remonte l’arbre jusqu’à la racine.

Ajoutez le même évènement à la grille et au rectangle mais avec un autre message.

![image8](/img/2.2/img08.png?height=200px)

Cliquez sur le rectangle. Que se passe-t-il ?

![image9-11](/img/2.2/img09-11.png?height=200px)

Encore une fois, l’événement remonte l’arbre et active tous les événement MouseDown de l’élément source jusqu’à la racine..

{{% exercice %}}
Testons immédiatement : refaite l’exercice du dessus avec le schéma suivant : 
-grid
	-grid
		-grid
			-button
Chaque event va afficher grid 1, grid 2, grid 3, button…

{{% /exercice %}}

![imageex1](/img/2.2/imgExemple2.png?height=300px)

{{% expand "Correction XAML" %}}

```xml
    <Grid MouseDown="Grid1_mouseDown">
        <Grid HorizontalAlignment="Left" Height="280" Margin="98,67,0,0" VerticalAlignment="Top" Width="623" Background="LightBlue" MouseDown="grid2_MouseDown">
            <Grid HorizontalAlignment="Left" Height="175" Margin="53,54,0,0" VerticalAlignment="Top" Width="527" Background="LightGray" MouseDown="grid3_MouseDown">
                <Button Content="Button" HorizontalAlignment="Left" Height="82" Margin="77,47,0,0" VerticalAlignment="Top" Width="360" Background="Gray" MouseDown="button_MouseDown"/>
            </Grid>
        </Grid>
    </Grid>
```

{{%/expand%}}

{{% expand "Correction C#" %}}

```xml
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private void Grid1_mouseDown(object sender, MouseButtonEventArgs e)
        {
            MessageBox.Show("Grid 1");
        }

        private void grid2_MouseDown(object sender, MouseButtonEventArgs e)
        {
            MessageBox.Show("Grid 2");
        }

        private void grid3_MouseDown(object sender, MouseButtonEventArgs e)
        {
            MessageBox.Show("Grid 3");
        }

        private void button_MouseDown(object sender, MouseButtonEventArgs e)
        {
            MessageBox.Show("Bouton");
        }
    }

```

{{%/expand%}}

### c. Tunnel Events

Les événements tunnels sont les opposés des événements bulle. En effet, l’événement est d’abord traité à la racine de l’arbre, puis successivement par chaque niveau de conteneur (dans le sens descendant) jusqu’à atteindre l’élément source.

Les événements Tunnel sont caractérisés par le préfixe “Preview”.

Exercice Tunnel :  
Reprenons la même structure que l’exercice précédent. Sauf que cette fois ci, nous allons affecter l’événement “PreviewMouseDown” aux trois éléments de notre arbre.

![image12](/img/2.2/img12.png?height=300px)

Si vous cliquez sur le rectangle, vous verrez que l’ordre d’apparition des messages est différent par rapport à tout à l’heure. Comme dit plus haut, l’événement se propage de la racine jusqu’à l’élément source qui est le rectangle ici.

![image13-15](/img/2.2/img13-15.png?height=200px)

{{% notice tip %}}
Il est possible d’empêcher la propagation d’un évènement !
{{% /notice %}}

Reprenons l’exemple des événements bulles. Il est possible d’empêcher un évènement de se propager au-delà d’un certain élément.

Pour ce faire, il suffit d’ajouter "e.Handled=true” dans la fonction de l’événement au niveau où l’on souhaite que la propagation s’arrête.

![image16](/img/2.2/img16.png?height=100px)

Si vous cliquez sur le rectangle, l’évènement atteindra la grille mais n’ira pas plus loin.

---

{{% button href="/exercices/c2/part2/" %}}Lien vers les exercices{{% /button %}}
