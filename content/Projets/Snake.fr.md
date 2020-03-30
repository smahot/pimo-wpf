+++
title = "Snake Game"
weight = 3003
pre = "Projet chapitre 3 : "
+++

![image1](/img/snake/img01.png?height=300px)

- [Première Partie](#première-partie)
  - [Question 1](#question-1)
  - [Question 2](#question-2)
  - [Question 3](#question-3)
  - [Question 4](#question-4)
  - [Question 5](#question-5)
  - [Question 6](#question-6)
  - [Question 7](#question-7)
  - [Question 8](#question-8)
- [Deuxième Partie](#deuxième-partie)
  - [Question 9](#question-9)
  - [Question 10](#question-10)
  - [Question 11](#question-11)
- [Pour aller plus loin](#pour-aller-plus-loin)

## Première Partie

Créez un nouveau Projet.

### Question 1

Modifiez votre fenêtre principale pour que ces dimensions soient les suivantes : 450x465.

### Question 2

Créez une grille nommée “snakeGrid” composée de 10 colonnes et 16 lignes de taille 25.

![image2](/img/snake/img02.png?height=300px)

{{% expand "Correcion partielle" %}}

Le code suivant permet de créer une grille avec 5 colonnes et 5 lignes de taille 25.

```xml
<Grid x:Name="snakeGrid" Margin="10,10,0,0" Height="125" Width="125" HorizontalAlignment="Left" VerticalAlignment="Top" Background="Black">
    <Grid.RowDefinitions>
        <RowDefinition Height="25"/>
        <RowDefinition Height="25"/>
        <RowDefinition Height="25"/>
        <RowDefinition Height="25"/>
        <RowDefinition Height="25"/>
    </Grid.RowDefinitions>
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="25"/>
        <ColumnDefinition Width="25"/>
        <ColumnDefinition Width="25"/>
        <ColumnDefinition Width="25"/>
        <ColumnDefinition Width="25"/>
    </Grid.ColumnDefinitions>
</Grid>
```

{{% /expand %}}

### Question 3

Insérez dans cette grille un rectangle nommé “snake” de la même taille que les carrés de la grille (c’est à dire 25x25).

![image3](/img/snake/img03.png?height=300px)

{{% expand "Correction" %}}

```xml
<Rectangle x:Name="snake" Fill="#FFF4F4F5" HorizontalAlignment="Left" Margin="0,0,0,0.6" Stroke="Black" Width="25" RenderTransformOrigin="-0.118,-0.168" Grid.Row="2" Grid.Column="1"/>
```

{{% /expand %}}

### Question 4

Faites-en sorte de pouvoir déplacer ce rectangle dans la grille via les flèches de votre clavier.

{{% expand "Correction partielle" %}}
Exemple pour la flèche du haut :

```csharp
private void Window_KeyDown(object sender, KeyEventArgs e)
{
    int rowRec = Grid.GetRow(snake);
    int colRec = Grid.GetColumn(snake);
    switch (e.Key.ToString())
    {
        case "Up":
            if (rowRec > 0)
            {
                rowRec = rowRec - 1;
                Grid.SetRow(snake, rowRec);//déplace le rectangle sur ces nouvelles coordonnées
            }
            break;
    }
}
```

{{% /expand %}}

### Question 5

Ajoutez 3 textBlocks (un avec le mot Coordonnées, les deux autres affichant les coordonnées du rectangle sur la grille nommés respectivement coordX et coordY)

![image4](/img/snake/img04.png?height=300px)

{{% expand "Correction" %}}

```xml
<TextBlock HorizontalAlignment="Left" Margin="285,27,0,0" TextWrapping="Wrap" Text="Coordonnées" VerticalAlignment="Top" Height="35" Width="145" Foreground="white" FontSize="22" TextAlignment="Center" Background="Black"/>

<TextBlock x:Name="coordX" HorizontalAlignment="Left" Margin="285,92.2,0,0" TextWrapping="Wrap"  VerticalAlignment="Top" Height="45" Width="45" Foreground="white" FontSize="24"  TextAlignment="Center" Background="Black" Text="2"/>

<TextBlock x:Name="coordY" HorizontalAlignment="Left" Margin="385,92.2,0,0" TextWrapping="Wrap"  VerticalAlignment="Top" Height="45" Width="45" Foreground="white" FontSize="24"  TextAlignment="Center" Background="Black" Text="1"/
```

{{% /expand %}}

### Question 6

Créez une fonction Actual_Coord qui va mettre à jour les textBlocks coordX et coordY en fonction des coordonnées du snake. Puis utilisez là au bon endroit dans votre programme.

{{% expand "Correction" %}}

```csharp
public void Actual_Coord()
{
    coordX.Text = Grid.GetRow(snake).ToString();

    coordY.Text = Grid.GetColumn(snake).ToString();
}
```

> Il faut l’utiliser quand le snake est déplacé. A la fin de l’évènement Window_KeyDown()
{{% /expand %}}

### Question 7

Ajoutez également des boutons (ou rectangles) qui représenteront les flèches de votre clavier sur l’écran.

![image5](/img/snake/img05.png?height=300px)

{{% expand "Correction pour l'ajout des boutons" %}}

```xml
<Button x:Name="top" Content="Top" HorizontalAlignment="Left" Margin="335,270.3,0,0" VerticalAlignment="Top" Width="45" Height="45" Background="Gray"/>

<Button x:Name="left" Content="Left" HorizontalAlignment="Left" Margin="285,320,0,0" VerticalAlignment="Top" Width="45" Height="45" Background="Gray"/>

<Button x:Name="right" Content="Right" HorizontalAlignment="Left" Margin="385,320.3,0,0" VerticalAlignment="Top" Width="45" Height="45" Background="Gray" RenderTransformOrigin="3.489,0.387" />

<Button x:Name="down" Content="Down" HorizontalAlignment="Left" Margin="335,320.3,0,0" VerticalAlignment="Top" Width="45" Height="45" Background="Gray" />
```

{{% /expand %}}

### Question 8

Lorsque vous appuyez sur une flèche, la flèche représentée sur l’écran doit changer de couleur et revenir à sa couleur initiale lorsque la flèche de votre clavier est relâchée.  

Comme ci-dessous, (flèche gauche appuyée puis relâchée)

![image6](/img/snake/img06.png?height=200px)

![image7](/img/snake/img07.png?height=200px)

{{% expand "Correction partielle" %}}

```csharp
private void Window_KeyDown(object sender, KeyEventArgs e)
{
    int rowRec = Grid.GetRow(snake);
    int colRec = Grid.GetColumn(snake);

    switch (e.Key.ToString())
    {
        case "Up":
            top.Background = Brushes.Red;
            if (rowRec > 0)
            {
                rowRec = rowRec - 1;
                Grid.SetRow(snake, rowRec);//déplace le rectangle sur ces nouvelles coordonnées
            }
            break;
        }
        Actual_Coord();
}

private void Window_KeyUp(object sender, KeyEventArgs e)
{
    switch (e.Key.ToString())
    {
        case "Up":
            top.Background = Brushes.Gray;
            Break;  
    }
}
```

{{% /expand %}}

{{< youtube-hw lIo7LBGPCKk 640 360>}}

## Deuxième Partie

### Question 9

Ajoutez un DispatchTimer permettant au rectangle de se déplacer automatiquement dans la direction que l’utilisateur aura choisie.

Lien pour en savoir plus sur l’utilisation du DispatchTimer : [https://www.wpf-tutorial.com/fr/96/divers/le-dispatchertimer/](https://www.wpf-tutorial.com/fr/96/divers/le-dispatchertimer/)

![image8](/img/snake/img08.png?height=300px)

Ici, la fonction timer_Tick va être appelée toutes les 150 millisecondes. Cela correspond à la vitesse de déplacement de notre snake.

Il faut tout d’abord détecter la direction. On crée donc une vrariable _direction que l’on initialise à zéro.

![image9](/img/snake/img09.png)

{{% expand "Correction partielle" %}}

Nous allons reprendre l’événement Window_KeyDown de la première partie et le modifier afin de savoir dans quelle direction l’utilisateur veut déplacer le snake.

```csharp
private void Window_KeyDown(object sender, KeyEventArgs e)
{
    switch (e.Key.ToString())
    {
        case "Up":
            _direction = 1;
            top.Background = Brushes.Red;
            break;
    }
}
```

Puis il faut déplacer le snake en fonction de cette direction.

```csharp
void timer_Tick(object sender, EventArgs e)
{
    int rowRec = Grid.GetRow(pionRectangle);
    int colRec = Grid.GetColumn(pionRectangle);

    switch (_direction)
    {
        case 1://up
            if (rowRec > 0)
            {
                rowRec = rowRec - 1;
                Grid.SetRow(pionRectangle, rowRec);//déplace le rectangle sur ces nouvelles coordonnées
            }
            break;
    }
    Actual_Coord();
}
```

> Vous remarquerez que le fonction Actual_Coord n’est plus appelée dans l’événement KeyDown mais dans la fonction timer_Tick car c’est dans cette dernier que le snake se déplace.

{{% /expand %}}

### Question 10

Insérez un rectangle “nourriture” dynamiquement sur la grille. Ce rectangle apparait aléatoirement sur la grille et correspond à la nourriture de votre Snake. Lorsque ce dernier passe dessus, la nourriture disparait et réapparait à un autre endroit.

Dans un premier temps, on crée la variable nourriture aux cotés de la variable direction. Nous utiliserons également un Random afin de placer cette nourriture aléatoirement.

![image10](/img/snake/img10.png)

{{% expand "Correction partielle" %}}
Changement dans la fonction timer_Tick :

```csharp
void timer_Tick(object sender, EventArgs e)
{
    int rowRec = Grid.GetRow(snake);
    int colRec = Grid.GetColumn(snake);

    int xFood = random.Next(0, snakeGrid.RowDefinitions.Count);
    int yFood = random.Next(0, snakeGrid.ColumnDefinitions.Count);

    if (!snakeGrid.Children.Contains(nourriture) && _direction!=0)
    {
        nourriture.Width = snake.Width;
        nourriture.Height = snake.Height;
        nourriture.Fill = Brushes.Green;
        snakeGrid.Children.Add(nourriture);
        Grid.SetColumn(nourriture, yFood);
        Grid.SetRow(nourriture, xFood);
    }

    switch (_direction)
    {
        case 1://up
            if (rowRec > 0)
            {
                rowRec = rowRec - 1;
                Grid.SetRow(snake, rowRec);//déplace le rectangle sur ces nouvelles coordonnées
            }
            break;
    }

    Actual_Coord();

    if(Grid.GetRow(snake)== Grid.GetRow(nourriture) && Grid.GetColumn(snake)== Grid.GetColumn(nourriture))
    {
        snakeGrid.Children.Remove(nourriture);
    }
}
```

{{% /expand %}}

Voilà ce que vous devez obtenir :

{{< youtube-hw LlmRRSRfLa8 640 360>}}

### Question 11

Créez la fonction GameOver(). Cette fonction est appelée lorsque les coordonnées du snake sorte de la grille de jeu. Elle affiche un message de défaite, retire la nourriture de la grille si il y en a, replace le snake aux coordonnées (2,2) et réinitialise le choix de direction à 0.

{{% expand "Correction" %}}

```csharp
public void GameOver()
{
    MessageBox.Show("PERDU");

    snakeGrid.Children.Remove(nourriture);

    Grid.SetColumn(snake, 2);
    Grid.SetRow(snake, 2);

    _direction = 0;

    Actual_Coord();
}
```

Il faut appeler GameOver() dans la fonction timer_Tick() au moment où l’on déplace le snake comme ci-dessous :  

```csharp
switch (_direction)
{
    case 1://up
        if (rowRec > 0)
        {
            rowRec = rowRec - 1;
            Grid.SetRow(snake, rowRec);//déplace le rectangle sur ces nouvelles coordonnées
            Actual_Coord();
        }
        else
        {
            GameOver();
        }
        break;
}
```

{{% /expand %}}

## Pour aller plus loin

Faites-en sorte que le SNAKE s’agrandisse quand il mange.

---

{{%attachments style="grey" /%}}
