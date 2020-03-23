+++
title = "Créer des éléments de façon dynamique"
weight = 3002
pre = "<b>3.2 </b>"
+++

- [1. Quelques éléments du Chapitre 2](#1-quelques-éléments-du-chapitre-2)
  - [a. Le Bouton](#a-le-bouton)
  - [b. Le TextBlock](#b-le-textblock)
  - [c. La TextBox](#c-la-textbox)
  - [d. La CheckBox](#d-la-checkbox)
- [2. Quelques éléments du Chapitre 3](#2-quelques-éléments-du-chapitre-3)
  - [a. La Grid](#a-la-grid)
  - [b. Le Stack Panel](#b-le-stack-panel)
  - [c. Le Wrap Panel](#c-le-wrap-panel)
  - [d. Le Dock Panel](#d-le-dock-panel)
  - [e. Le Canvas](#e-le-canvas)
- [3. Pourquoi utiliser la création dynamique ?](#3-pourquoi-utiliser-la-création-dynamique-)

Nous allons maintenant aborder une nouvelle façon de créer tous les éléments que nous avons vu auparavant, depuis le bouton jusqu’aux différents layouts. En effet, tous ces éléments sont des objets C#, et nous pouvons donc les initialiser et spécifier leurs propriétés directement depuis la `MainWindow.xaml.cs`. Si au départ l’intérêt de cette approche semble inexistant, nous allons voir que se priver de la simplicité du XAML nous permettra d'aller beaucoup plus loin dans notre utilisation de WPF.

## 1. Quelques éléments du Chapitre 2

### a. Le Bouton

Tout ce que nous ferons maintenant concernera la fenêtre `MainWindow.xaml.cs`, et s’écrira donc en C#. Comme nous l’avons dit plus haut, il est possible de créer un bouton sans utiliser notre fenêtre XAML. Pour cela il suffit de déclarer un nouvel objet de la classe Button :

    Button b = new Button();

Comme vous pouvez le voir, l’élément Button a un constructeur qui ne prend aucun argument. Comment donc lui associer un contenu ? Comment peut-on lui attribuer une taille ? Le Button étant un objet, nous le ferons donc en utilisant ses propriétés. Par exemple, si je veux que mon bouton ait le texte Hello World en contenu, il me suffit d’inscrire ce texte dans la propriété Content :

    b.Content = "Hello World";

De même pour lui fixer une taille, il faut donner une valeur aux propriétés Height et Width :

    b.Height = 150;
    b.Width = 150;

Enfin, on peut donner une position à notre bouton grâce à la propriété HorizontalAlignment (respectivement VerticalAlignment). Pour ce faire, vous avez deux options :

    b.HorizontalAlignment = VALEUR;

Avec VALEUR un entier entre 0 et 3 (0 : gauche, 1 : centre, 2 : droite, 3 : stretch). Ou bien vous pouvez utiliser HorizontalAlignment.Left (respectivement .Center, .Right et .Stretch).

    b.HorizontalAlignment = HorizontalAlignment.Left;

Maintenant, créez à votre tour un bouton dans votre fenêtre C#, attribuez-lui une taille, un contenu et spécifiez-lui un alignement.  
Maintenant que tout est prêt lancez votre code et… Et rien ne s’affiche, étrange non ?  
En réalité c’est normal, nous n’avons pas fait le lien entre l’élément que nous avons créé, ici le bouton, et la fenêtre que nous affichons en sortie.  
En effet, sur la fenêtre `MainWindow.xaml`, nous placions directement notre bouton dans la fenêtre XAML, mais ici ce n’est pas le cas.  
Il faut attribuer un contenu à la fenêtre pour que celle-ci affiche autre chose qu’une fenêtre blanche.  
Pour ce faire, comme nous sommes dans la partial class MainWindow, et que l’élément this se réfère donc à l’instance de la classe MainWindow, il faut écrire ceci :

    this.Content = b;

Si vous exécutez le code maintenant, vous allez voir que cette fois-ci vous obtiendrez bien le résultat désiré. A noter que l’objet MainWindow a d’autres propriétés comme Height, Width, Background…

{{% exercice %}}
Reproduisez à l’aide des boutons, d’un Canvas et d’une TextBox le résultat suivant de façon dynamique :
{{% /exercice %}}

![image1](/img/3.2/img01.png?height=300px)

{{% expand "Correction" %}}

```csharp
Canvas cv = new Canvas();

TextBox txtb = new TextBox();

Button h = new Button();
Button e = new Button();
Button l = new Button();
Button o = new Button();

Button excl = new Button();
Button esp = new Button();

public MainWindow()
{
    InitializeComponent();
    MakingGrid();
}

private void MakingGrid()
{
    cv.Height = 480;
    cv.Width = 420;
    txtb.IsEnabled = false;
    txtb.Height = 300;
    txtb.Width = 390;
    txtb.FontSize = 30;
    Canvas.SetLeft(txtb, 10);
    Canvas.SetTop(txtb, 10);
    cv.Children.Add(txtb);
    h.Height = 30;
    h.Width = 30;
    h.Content = "H";
    h.FontSize = 20;
    h.FontWeight = FontWeights.Bold;
    h.Background = Brushes.Honeydew;
    Canvas.SetLeft(h, 10);
    Canvas.SetTop(h, 320);
    h.Click += btn_h;
    cv.Children.Add(h);
    e.Height = 30;
    e.Width = 30;
    e.Content = "E";
    e.FontSize = 20;
    e.FontWeight = FontWeights.Bold;
    e.Background = Brushes.Honeydew;
    Canvas.SetLeft(e, 45);
    Canvas.SetTop(e, 320);
    e.Click += btn_e;
    cv.Children.Add(e);
    l.Height = 30;
    l.Width = 30;
    l.Content = "L";
    l.FontSize = 20;
    l.FontWeight = FontWeights.Bold;
    l.Background = Brushes.Honeydew;
    Canvas.SetLeft(l, 80);
    Canvas.SetTop(l, 320);
    l.Click += btn_l;
    cv.Children.Add(l);
    o.Height = 30;
    o.Width = 30;
    o.Content = "O";
    o.FontSize = 20;
    o.FontWeight = FontWeights.Bold;
    o.Background = Brushes.Honeydew;
    Canvas.SetLeft(o, 115);
    Canvas.SetTop(o, 320);
    o.Click += btn_o;
    cv.Children.Add(o);
    excl.Height = 30;
    excl.Width = 30;
    excl.Content = "!";
    excl.FontSize = 20;
    excl.FontWeight = FontWeights.Bold;
    excl.Background = Brushes.Honeydew;
    Canvas.SetLeft(excl, 150);
    Canvas.SetTop(excl, 320);
    excl.Click += btn_excl;
    cv.Children.Add(excl);
    esp.Height = 30;
    esp.Width = 30;
    esp.Content = " ";
    esp.FontSize = 20;
    esp.FontWeight = FontWeights.Bold;
    esp.Background = Brushes.Honeydew;
    Canvas.SetLeft(esp, 185);
    Canvas.SetTop(esp, 320);
    esp.Click += btn_esp;
    cv.Children.Add(esp);
    this.Content = cv;
}

private void btn_h(object sender, EventArgs ev)
{
    txtb.Text = txtb.Text + "h";
}

private void btn_e(object sender, EventArgs ev)
{
    txtb.Text = txtb.Text + "e";
}

private void btn_l(object sender, EventArgs ev)
{
    txtb.Text = txtb.Text + "l";
}

private void btn_o(object sender, EventArgs ev)
{
    txtb.Text = txtb.Text + "o";
}

private void btn_excl(object sender, EventArgs ev)
{
    txtb.Text = txtb.Text + "!";
}

private void btn_esp(object sender, EventArgs ev)
{
    txtb.Text = txtb.Text + " ";
}
```

{{% /expand %}}

### b. Le TextBlock

De la même façon, le TextBlock est un objet et se déclare comme on déclare un bouton :

    TextBlock txtbl = new TextBlock();

Pour attribuer un texte au TextBlock, il suffit de donner une valeur à sa propriété Text :

    txtbl.Text = "TextBlock créée sans XAML";

Evidemment, on peut aussi attribuer une taille au TextBlock (comme pour tous les autres éléments, mais, l’exemple étant été donné pour le bouton, nous ne nous y arrêterons plus). Arrêtons-nous maintenant sur les propriétés du texte.

Nous pouvons spécifier la police de texte que nous voulons utiliser comme suit :

    txtbl.FontFamily = new FontFamily("Nom_De_La_Police");

Nous pouvons aussi spécifier sa taille :

    txtbl.FontSize = VALEUR;

> Avec VALEUR un entier qui déterminera la taille de la police.

Nous pouvons aussi déterminer l’épaisseur de la police :

    txtbl.FontWeight = FontWeights.WEIGHT_POLICE;

> Avec WEIGHT_POLICE la nature de la police de caractère, par exemple FontWeights.UltraBold.

Nous pouvons aussi choisir la couleur du texte comme suit :

    txtbl.Foreground = Brushes.COLOR;

> Avec COLOR la couleur du texte par exemple Brushes.AliceBlue.

De même, on peut spécifier la couleur de fond de notre TextBlock comme suit :

    txtbl.Background = Brushes.COLOR;

Enfin, on peut choisir la couleur des bords de notre TextBox :

    txtbl.BorderBrush = Brushes.COLOR;

Ainsi que choisir l’épaisseur des bords :

    txtbl.BorderThickness = new Thickness(VALEUR);

Ou en spécifiant chaque valeur une par une :

    txtbl.BorderThickness = new Thickness(VALEUR1, VALEUR2, VALEUR3, VALEUR4);

{{% exercice %}}
Reproduisez à l’aide du TextBlock et en dynamique le résultat suivant :
{{% /exercice %}}

![image2](/img/3.2/img02.png?height=200px)

![image3](/img/3.2/img03.png?height=200px)

{{% expand "Correction" %}}

```csharp
Canvas cv = new Canvas();

TextBlock txtb = new TextBlock();
TextBlock txtb2 = new TextBlock();
TextBlock txtb3 = new TextBlock();
TextBlock txtb4 = new TextBlock();

int compteur = 0;

Button b = new Button();

public MainWindow()
{
    InitializeComponent();
    MakingTextBlock();
}

private void MakingTextBlock()
{
    cv.Height = 400;
    cv.Width = 400;
    txtb.Height = 50;
    txtb.Width = 100;
    txtb.FontSize = 20;
    txtb.Text = "";
    txtb.Background = Brushes.AliceBlue;
    Canvas.SetLeft(txtb, 0);
    Canvas.SetTop(txtb, 0);
    cv.Children.Add(txtb);
    txtb2.Height = 50;
    txtb2.Width = 100;
    txtb2.FontSize = 20;
    txtb2.Text = "";
    txtb2.Background = Brushes.AliceBlue;
    Canvas.SetLeft(txtb2, 300);
    Canvas.SetTop(txtb2, 0);
    cv.Children.Add(txtb2);
    txtb3.Height = 50;
    txtb3.Width = 100;
    txtb3.FontSize = 20;
    txtb3.Text = "";
    txtb3.Background = Brushes.AliceBlue;
    Canvas.SetRight(txtb3, 0);
    Canvas.SetBottom(txtb3, 0);
    cv.Children.Add(txtb3);
    txtb4.Height = 50;
    txtb4.Width = 100;
    txtb4.FontSize = 20;
    txtb4.Text = "";
    txtb4.Background = Brushes.AliceBlue;
    Canvas.SetRight(txtb4, 300);
    Canvas.SetBottom(txtb4, 0);
    cv.Children.Add(txtb4);
    b.Width = 50;
    b.Height = 50;
    b.Background = Brushes.LightSteelBlue;
    b.Click += b_Event;
    Canvas.SetBottom(b,175);
    Canvas.SetLeft(b, 175);
    cv.Children.Add(b);
    this.Content = cv;
}

private void b_Event(object sender, EventArgs e)
{
    if (compteur ==0)
    {
        txtb.Text = "1";
        txtb4.Text = "";
        compteur++;
    }
    else if (compteur == 1)
    {
        txtb2.Text = "2";
        txtb.Text = "";
        compteur++;
    }
    else if (compteur == 2)
    {
        txtb3.Text = "3";
        txtb2.Text = "";
        compteur++;
    }
    else
    {
        txtb3.Text = "";
        txtb4.Text = "4";
        compteur =0;
    }
}
```

{{% /expand %}}

### c. La TextBox

On déclare l’objet TextBox comme suit :

    TextBox txtbx = new TextBox();

On y insère du texte avec la propriété Text :

    txtbx.Text = "TextBox créée sans XAML";

Si notre texte dépasse de la TextBox, on peut choisir de le faire retourner à la ligne :

    txtbx.TextWrapping = TextWrapping.Wrap;

{{% exercice %}}
Reproduisez à l’aide du TextBlock et en dynamique le résultat suivant :
{{% /exercice %}}

![image4](/img/3.2/img04.png?height=200px)

![image5](/img/3.2/img05.png?height=200px)

{{% expand "Correction" %}}

```csharp
Canvas cv = new Canvas();

TextBox txtb = new TextBox();
TextBox txtb2 = new TextBox();
TextBox txtb3 = new TextBox();
TextBox txtb4 = new TextBox();

int compteur = 0;

Button b = new Button();

public MainWindow()
{
    InitializeComponent();
    MakingTextBlock();
}

private void MakingTextBlock()
{
    cv.Height = 400;
    cv.Width = 400;
    txtb.Height = 50;
    txtb.Width = 100;
    txtb.FontSize = 20;
    txtb.Text = "";
    txtb.Background = Brushes.AliceBlue;
    Canvas.SetLeft(txtb, 0);
    Canvas.SetTop(txtb, 0);
    cv.Children.Add(txtb);
    txtb2.Height = 50;
    txtb2.Width = 100;
    txtb2.FontSize = 20;
    txtb2.Text = "";
    txtb2.Background = Brushes.AliceBlue;
    Canvas.SetLeft(txtb2, 300);
    Canvas.SetTop(txtb2, 0);
    cv.Children.Add(txtb2);
    txtb3.Height = 50;
    txtb3.Width = 100;
    txtb3.FontSize = 20;
    txtb3.Text = "";
    txtb3.Background = Brushes.AliceBlue;
    Canvas.SetRight(txtb3, 0);
    Canvas.SetBottom(txtb3, 0);
    cv.Children.Add(txtb3);
    txtb4.Height = 50;
    txtb4.Width = 100;
    txtb4.FontSize = 20;
    txtb4.Text = "";
    txtb4.Background = Brushes.AliceBlue;
    Canvas.SetRight(txtb4, 300);
    Canvas.SetBottom(txtb4, 0);
    cv.Children.Add(txtb4);
    b.Width = 50;
    b.Height = 50;
    b.Background = Brushes.LightSteelBlue;
    b.Click += b_Event;
    Canvas.SetBottom(b,175);
    Canvas.SetLeft(b, 175);
    cv.Children.Add(b);
    this.Content = cv;
}

private void b_Event(object sender, EventArgs e)
{
    if (compteur == 0)
    {
        txtb.Text = "1";
        txtb4.Text = "";
        compteur++;
    }
    else if (compteur == 1)
    {
        txtb2.Text = "2";
        txtb.Text = "";
        compteur++;
    }
    else if (compteur == 2)
    {
        txtb3.Text = "3";
        txtb2.Text = "";
        compteur++;
    }
    else
    {
        txtb3.Text = "";
        txtb4.Text = "4";
        compteur = 0;
    }
}
```

{{% /expand %}}

### d. La CheckBox

On déclare l’objet CheckBox comme suit :

    CheckBox cbx = new CheckBox();

Nous avons déjà évoqué comment attribuer du texte et choisir les caractéristiques de la police plus haut. On peut aussi attribuer à la CheckBox la propriété IsThreeState abordée au chapitre 2 :

    cbx.IsThreeState = true;

{{% exercice %}}
Pour aller plus loin, vous pouvez essayer de reproduire ceci en dynamique :
{{% /exercice %}}

![image6](/img/3.2/img06.png?height=200px)

![image7](/img/3.2/img07.png?height=200px)

{{% expand "Correction" %}}

```csharp
Canvas cv = new Canvas();

TextBox t_fname = new TextBox();
TextBox t_lname = new TextBox();
TextBox t_birth = new TextBox();
TextBox t_mail = new TextBox();
TextBox t_tele = new TextBox();

Button sd = new Button();

ListBox result = new ListBox();

public MainWindow()
{
    InitializeComponent();
    MakingCanvas();
}

private void MakingCanvas()
{

    cv.Height = 500;
    cv.Width = 500;
    Label lb = new Label();
    lb.Height = 50;
    lb.Width = 400;
    lb.Foreground = Brushes.BlueViolet;
    lb.FontSize = 20;
    lb.HorizontalContentAlignment = HorizontalAlignment.Center;
    lb.FontWeight = FontWeights.Bold;
    lb.Content = "Press 'Enter' key, for delivering values";
    Canvas.SetLeft(lb, 10);
    Canvas.SetTop(lb, 20);
    cv.Children.Add(lb);
    Label fname = new Label();
    fname.Height = 30;
    fname.Width = 100;
    fname.FontSize = 15;
    fname.FontWeight = FontWeights.Bold;
    fname.Content = "First Name";
    Canvas.SetLeft(fname, 20);
    Canvas.SetTop(fname, 80);
    cv.Children.Add(fname);
    Label lname = new Label();
    lname.Height = 30;
    lname.Width = 100;
    lname.FontSize = 15;
    lname.FontWeight = FontWeights.Bold;
    lname.Content = "Last Name";
    Canvas.SetLeft(lname, 20);
    Canvas.SetTop(lname, 140);
    cv.Children.Add(lname);
    Label birth = new Label();
    birth.Height = 30;
    birth.Width = 200;
    birth.FontSize = 15;
    birth.FontWeight = FontWeights.Bold;
    birth.Content = "Birth (dd/mm/yyyy)";
    Canvas.SetLeft(birth, 20);
    Canvas.SetTop(birth, 200);
    cv.Children.Add(birth);
    Label tele = new Label();
    tele.Height = 30;
    tele.Width = 200;
    tele.FontSize = 15;
    tele.FontWeight = FontWeights.Bold;
    tele.Content = "Telephone";
    Canvas.SetLeft(tele, 20);
    Canvas.SetTop(tele, 260);
    cv.Children.Add(tele);
    Label mail = new Label();
    mail.Height = 30;
    mail.Width = 200;
    mail.FontSize = 15;
    mail.FontWeight = FontWeights.Bold;
    mail.Content = "E-MAIL";
    Canvas.SetLeft(mail, 20);
    Canvas.SetTop(mail, 320);
    cv.Children.Add(mail);
    t_fname.Height = 30;
    t_fname.Width = 100;
    t_fname.FontSize = 15;
    t_fname.VerticalContentAlignment = VerticalAlignment.Center;
    Canvas.SetLeft(t_fname, 22);
    Canvas.SetTop(t_fname, 110);
    cv.Children.Add(t_fname);
    t_lname.Height = 30;
    t_lname.Width = 100;
    t_lname.FontSize = 15;
    t_lname.VerticalContentAlignment = VerticalAlignment.Center;
    Canvas.SetLeft(t_lname, 22);
    Canvas.SetTop(t_lname, 170);
    cv.Children.Add(t_lname);
    t_birth.Height = 30;
    t_birth.Width = 100;
    t_birth.FontSize = 15;
    t_birth.VerticalContentAlignment = VerticalAlignment.Center;
    Canvas.SetLeft(t_birth, 22);
    Canvas.SetTop(t_birth, 230);
    cv.Children.Add(t_birth);
    t_tele.Height = 30;
    t_tele.Width = 100;
    t_tele.FontSize = 13;
    t_tele.VerticalContentAlignment = VerticalAlignment.Center;
    Canvas.SetLeft(t_tele, 22);
    Canvas.SetTop(t_tele, 290);
    cv.Children.Add(t_tele);
    t_mail.Height = 30;
    t_mail.Width = 100;
    t_mail.FontSize = 13;
    t_mail.VerticalContentAlignment = VerticalAlignment.Center;
    Canvas.SetLeft(t_mail, 22);
    Canvas.SetTop(t_mail, 350);
    cv.Children.Add(t_mail);
    Label youare = new Label();
    youare.Height = 50;
    youare.Width = 100;
    youare.FontSize = 20;
    youare.FontWeight = FontWeights.Bold;
    youare.Content = "You Are";
    youare.Foreground = Brushes.DodgerBlue;
    Canvas.SetLeft(youare, 300);
    Canvas.SetTop(youare, 100);
    cv.Children.Add(youare);
    result.Height = 200;
    result.Width = 200;
    result.FontSize = 12;
    result.FontWeight = FontWeights.SemiBold;
    Canvas.SetLeft(result, 240);
    Canvas.SetTop(result, 150);
    cv.Children.Add(result);
    sd.Height = 25;
    sd.Width = 50;
    sd.FontSize = 13;
    sd.Content = "Send";
    Canvas.SetLeft(sd, 45);
    Canvas.SetTop(sd, 400);
    cv.Children.Add(sd);
    t_fname.Focus();
    t_fname.KeyDown += T_fname_KeyDown;
    t_lname.KeyDown += T_lname_KeyDown;
    t_birth.KeyDown += T_birth_KeyDown;
    t_tele.KeyDown += T_tele_KeyDown;
    t_mail.KeyDown += T_mail_KeyDown;
    sd.Click += btn_send;
    this.Content = cv;
}

private void T_fname_KeyDown(object sender, KeyEventArgs e)
{
    if (e.Key.Equals(Key.Enter))
    {
        t_lname.Focus();
    }
    else if (e.Key.Equals(Key.Tab))
    {
        t_fname.Text = "Press Enter";
    }
}

private void T_lname_KeyDown(object sender, KeyEventArgs e)
{
    if (e.Key.Equals(Key.Enter))
    {
        t_birth.Focus();
    }
    else if (e.Key.Equals(Key.Tab))
    {
        t_lname.Text = "Press Enter";
    }
}

private void T_birth_KeyDown(object sender, KeyEventArgs e)
{
    if (e.Key.Equals(Key.Enter))
    {
        t_tele.Focus();
    }

    else if (e.Key.Equals(Key.Tab))
    {
        t_birth.Text = "Press Enter";
    }
}

private void T_tele_KeyDown(object sender, KeyEventArgs e)
{
    if (e.Key.Equals(Key.Enter))
    {
        t_mail.Focus();
    }
    else if (e.Key.Equals(Key.Tab))
    {
        t_tele.Text = "Press Enter";
    }
}

private void T_mail_KeyDown(object sender, KeyEventArgs e)
{
    if (e.Key.Equals(Key.Enter))
    {
        sd.Focus();
    }
    else if (e.Key.Equals(Key.Tab))
    {
        t_mail.Text = "Press Enter";
    }
}

private void btn_send(object sender, EventArgs e)
{
    result.Items.Add("Your first Name : " + t_fname.Text);
    result.Items.Add("Your Last Name : " + t_lname.Text);
    result.Items.Add("Your birth : " + t_birth.Text);
    result.Items.Add("Your Phone Number : " + t_tele.Text);
    result.Items.Add("Your E-MAIL Address : " + t_mail.Text);
    sd.IsEnabled = false;
}
```

{{% /expand %}}

## 2. Quelques éléments du Chapitre 3

### a. La Grid

On déclare un Grid comme suit :

    Grid myGrid = new Grid();

Pour pouvoir créer une colonne, respectivement une ligne, il faut créer un objet :

    ColumnDefinition colDef1 = new ColumnDefinition();
    myGrid.ColumnDefinitions.Add(colDef1);

Imaginons que nous créions le TextBlock suivant :

    TextBlock txt = new TextBlock();
    txt.Text = "TextBlock";
    txt.FontSize = 20;
    txt.FontWeight = FontWeights.Bold;

Notre Grid a pour l’instant trois colonnes et quatre lignes :

    ColumnDefinition colDef2 = new ColumnDefinition();
    ColumnDefinition colDef3 = new ColumnDefinition();
    ColumnDefinition colDef1 = new ColumnDefinition();
    myGrid.ColumnDefinitions.Add(colDef1);
    myGrid.ColumnDefinitions.Add(colDef2);
    myGrid.ColumnDefinitions.Add(colDef3);
    RowDefinition rowDef1 = new RowDefinition();
    RowDefinition rowDef2 = new RowDefinition();
    RowDefinition rowDef3 = new RowDefinition();
    RowDefinition rowDef4 = new RowDefinition();
    myGrid.RowDefinitions.Add(rowDef1);
    myGrid.RowDefinitions.Add(rowDef2);
    myGrid.RowDefinitions.Add(rowDef3);
    myGrid.RowDefinitions.Add(rowDef4);

On choisit la localization du TextBlock dans notre Grid comme suit :

    Grid.SetColumn(txt, 0);
    Grid.SetRow(txt, 0);

Evidemment, on peut toujours utiliser les propriétés ColumnSpan et RowSpan comme suit :

    Grid.SetColumnSpan(txt, 3);

Enfin, on ajoute l’élément à notre Grid comme suit :

    myGrid.Children.Add(txt);

{{% exercice %}}
Essayez d’obtenir grâce à la grille et en dynamique le résultat suivant :
{{% /exercice %}}

![image13](/img/3.2/img13.png?height=200px)

{{% expand "Correction" %}}

```csharp
public MainWindow()
{
    InitializeComponent();
    myGrid.Name = "grille";
    myGrid.Width = 250;
    myGrid.Height = 250;
    myGrid.HorizontalAlignment = HorizontalAlignment.Left;
    myGrid.VerticalAlignment = VerticalAlignment.Top;
    ColumnDefinition colDef1 = new ColumnDefinition();
    ColumnDefinition colDef2 = new ColumnDefinition();
    ColumnDefinition colDef3 = new ColumnDefinition();
    ColumnDefinition colDef4 = new ColumnDefinition();
    myGrid.ColumnDefinitions.Add(colDef1);
    myGrid.ColumnDefinitions.Add(colDef2);
    myGrid.ColumnDefinitions.Add(colDef3);
    myGrid.ColumnDefinitions.Add(colDef4);
    RowDefinition rowDef1 = new RowDefinition();
    RowDefinition rowDef2 = new RowDefinition();
    RowDefinition rowDef3 = new RowDefinition();
    RowDefinition rowDef4 = new RowDefinition();
    myGrid.RowDefinitions.Add(rowDef1);
    myGrid.RowDefinitions.Add(rowDef2);
    myGrid.RowDefinitions.Add(rowDef3);
    myGrid.RowDefinitions.Add(rowDef4);
    Button Top = new Button();
    Top.Content = "Top";
    Button Bottom = new Button();
    Bottom.Content = "Bottom";
    Button Left = new Button();
    Left.Content = "Left";
    Button Right = new Button();
    Right.Content = "Right";
    Button Center = new Button();
    Center.Content = "Center";
    Grid.SetRow(Top, 0);
    Grid.SetColumnSpan(Top, 4);
    Grid.SetRow(Bottom, 3);
    Grid.SetColumnSpan(Bottom, 4);
    Grid.SetRow(Left, 1);
    Grid.SetColumn(Left, 0);
    Grid.SetRowSpan(Left, 2);
    Grid.SetRow(Right, 1);
    Grid.SetColumn(Right, 3);
    Grid.SetRowSpan(Right, 2);
    Grid.SetRow(Center, 1);
    Grid.SetColumn(Center, 1);
    Grid.SetRowSpan(Center, 2);
    Grid.SetColumnSpan(Center, 2);
    myGrid.Children.Add(Top);
    myGrid.Children.Add(Bottom);
    myGrid.Children.Add(Left);
    myGrid.Children.Add(Right);
    myGrid.Children.Add(Center);
    this.Content = myGrid;
}
```

{{% /expand %}}

### b. Le Stack Panel

Nous pouvons déclarer des layouts, qui sont eux aussi des objets C#. Pour construire un Stack Panel, il faut écrire la ligne suivante :

    StackPanel stp = new StackPanel();
Nous rappelons que nous pouvons choisir si notre Stack Panel sera vertical ou horizontal avec la propriété Orientation :

    stp.Orientation = Orientation.Horizontal;

Nous pouvons donner une taille à notre Stack Panel comme nous le faisons pour tous les éléments :

    stp.Width = VALEUR;
    stp.Height = VALEUR;

Une fois notre Stack Panel construit, nous pouvons lui insérer des éléments. Créons tout d’abord un TextBlock :

    TextBlock txtbl = new TextBlock();
    txtbl.Text = "TextBlock Without XAML";
    txtbl.Background = Brushes.AliceBlue;

Maintenant que nous avons notre TextBlock, nous pouvons l’ajouter à notre Stack Panel :

    stp.Children.Add(txtbl);

{{% exercice %}}
Essayez d’obtenir grâce au Stack Panel le résultat suivant :
{{% /exercice %}}

![image8](/img/3.2/img08.png?height=200px)

![image9](/img/3.2/img09.png?height=200px)

{{% expand "Correction" %}}

```csharp
Grid myGrid = new Grid();

ListBox lbx = new ListBox();
TextBox txtb1 = new TextBox();
TextBox txtb2 = new TextBox();
TextBox txtb3 = new TextBox();

public MainWindow()
{
    InitializeComponent();
    MakingStackPanel();
}

private void MakingStackPanel()
{
    StackPanel sp = new StackPanel();
    sp.Orientation = Orientation.Vertical;
    sp.Width = 400;
    sp.Height = 500;
    sp.HorizontalAlignment = HorizontalAlignment.Left;
    sp.VerticalAlignment = VerticalAlignment.Top;
    sp.Background = Brushes.AliceBlue;
    Label lb = new Label();
    lb.Height = 50;
    lb.Width = 400;
    lb.Content = "Simple Message !";
    lb.FontSize = 25;
    lb.Foreground = Brushes.IndianRed;
    lb.HorizontalContentAlignment = HorizontalAlignment.Center;
    lb.FontWeight = FontWeights.Bold;
    sp.Children.Add(lb);
    txtb1.Width = 300;
    txtb1.Height = 50;
    txtb1.IsReadOnly = true;
    sp.Children.Add(txtb1);
    txtb2.Width = 300;
    txtb2.Height = 50;
    txtb2.IsReadOnly = true;
    sp.Children.Add(txtb2);
    txtb3.Width = 300;
    txtb3.Height = 50;
    txtb3.IsReadOnly = true;
    txtb3.Margin = new Thickness(0, 0, 0, 125);
    sp.Children.Add(txtb3);
    Button btn1 = new Button();
    btn1.Height = 45;
    btn1.Width = 300;
    btn1.FontSize = 15;
    btn1.Content = "Hi, I'm PIMO.";
    btn1.Click += btn_hi;
    sp.Children.Add(btn1);
    Button btn2 = new Button();
    btn2.Height = 45;
    btn2.Width = 300;
    btn2.FontSize = 15;
    btn2.Content = "How is the weather in Paris?";
    btn2.Click += btn_weather;
    sp.Children.Add(btn2);
    Button btn3 = new Button();
    btn3.Height = 45;
    btn3.Width = 300;
    btn3.FontSize = 15;
    btn3.Content = "I hope you be healthy !";
    btn3.Click += btn_healthy;
    this.Content = sp;
    sp.Children.Add(btn3);
}

private void btn_hi(object sender, EventArgs e)
{
    txtb1.Text = "Hi, I'm PIMO.";
}

private void btn_weather(object sender, EventArgs e)
{
    txtb2.Text = "How is the weather in Paris?";
}

private void btn_healthy(object sender, EventArgs e)
{
    txtb3.Text = "I hope you be healthy !";
}
```

{{% /expand %}}

### c. Le Wrap Panel

Nous pouvons créer un Wrap Panel comme suit :

    WrapPanel wp = new WrapPanel();

Comme pour le Stack Panel, on peut choisir son orientation :

    wp.Orientation = Orientation.CHOIX_ORIENTATION;

> Avec CHOIX_ORIENTATION qui peut prendre les valeurs Horizontal et Vertical.

Bien entendu, nous pouvons aussi choisir où se situera notre Wrap Panel dans la fenêtre grâce aux propriétés HorizontalAlignment et VerticalAlignment :

    wp.HorizontalAlignment = HorizontalAlignment.Left;
    wp.VerticalAlignment = VerticalAlignment.Top;

D’autres propriétés sont également disponibles, telle la propriété Background :

    wp.Background = Brushes.COLOR_NAME;

Si nous reprenons notre TextBlock de tout à l’heure, nous pouvons l’ajouter à notre Wrap Panel comme suit :

    wp.Children.Add(txtbl);

{{% exercice %}}
Essayez d’obtenir avec Wrap Panel et en dynamique le résultat suivant :
{{% /exercice %}}

![image10](/img/3.2/img10.png?height=200px)

{{% expand "Correction" %}}

```csharp
public MainWindow()
{
    InitializeComponent();
    WrapPanel wp = new WrapPanel();
    wp.Width = 500;
    wp.Height = 500;
    Rectangle r1 = new Rectangle();
    r1.Width = 150;
    r1.Height = 150;
    r1.Fill = Brushes.White;
    r1.Stroke = Brushes.Red;
    r1.StrokeThickness = 5;
    wp.Children.Add(r1);
    Rectangle r2 = new Rectangle();
    r2.Width = 150;
    r2.Height = 150;
    r2.Fill = Brushes.White;
    r2.Stroke = Brushes.Orange;
    r2.StrokeThickness = 5;
    wp.Children.Add(r2);
    Rectangle r3 = new Rectangle();
    r3.Width = 150;
    r3.Height = 150;
    r3.Fill = Brushes.White;
    r3.Stroke = Brushes.Yellow;
    r3.StrokeThickness = 5;
    wp.Children.Add(r3);
    Rectangle r4 = new Rectangle();
    r4.Width = 150;
    r4.Height = 150;
    r4.Fill = Brushes.White;
    r4.Stroke = Brushes.Green;
    r4.StrokeThickness = 5;
    wp.Children.Add(r4);
    Rectangle r5 = new Rectangle();
    r5.Width = 150;
    r5.Height = 150;
    r5.Fill = Brushes.White;
    r5.Stroke = Brushes.Blue;
    r5.StrokeThickness = 5;
    wp.Children.Add(r5);
    Rectangle r6 = new Rectangle();
    r6.Width = 150;
    r6.Height = 150;
    r6.Fill = Brushes.White;
    r6.Stroke = Brushes.Black;
    r6.StrokeThickness = 5;
    wp.Children.Add(r6);
    Rectangle r7 = new Rectangle();
    r7.Width = 150;
    r7.Height = 150;
    r7.Fill = Brushes.White;
    r7.Stroke = Brushes.Violet;
    r7.StrokeThickness = 5;
    wp.Children.Add(r7);
    this.Content = wp;
}
```

{{% /expand %}}

### d. Le Dock Panel

On peut déclarer un objet Dock Panel comme suit :

    DockPanel dcpnl = new DockPanel();

Comme nous l’avons vu, le Dock Panel permet de choisir si l’élément que nous plaçons sera en haut, en bas, à gauche ou à droite dans notre fenêtre. Cela complique donc un petit peu sa création. Cet objet a lui aussi des propriétés de taille, de Background, de bordure et d’épaisseur de bordure, voici quelques exemples :

    b.Height = 25;
    b.BorderBrush = Brushes.AliceBlue;
    b.BorderThickness = new Thickness(5);

Nous devons ensuite ajouter cette bordure à notre Dock Panel, en choisissant sa future position :

    DockPanel.SetDock(b, Dock.POSITION);

Avec POSITION qui a pour valeur Top, Bottom, Right et Left. Si nous reprenons de nouveau notre TextBlock de tout à l’heure, nous devons l’associer à la bordure que nous venons de créer :

    b.Child = txtbl;

Enfin, nous ajoutons le tout à notre Dock Panel comme suit :

    dcpnl.Children.Add(b);

Il est important de se souvenir que l’ordre dans lequel nous ajoutons les éléments dans notre Dock Panel va influer sur leur disposition dans notre fenêtre (pour rappel voir la première partie de ce chapitre).

Enfin, nous pouvons utiliser la propriété LastChildFill qui spécifie si le dernier élément placé remplit toute la place restante (dans ce cas sa valeur est true) ou non :

    dcpnl.LastChildFill = true;

> Par défaut cette propriété a pour valeur true.

{{% exercice %}}
Essayez d’obtenir avec Dock Panel et en dynamique le résultat suivant :
{{% /exercice %}}

![image11](/img/3.2/img11.png?height=200px)

{{% expand "Correction" %}}

```csharp
 public MainWindow()
{
    InitializeComponent();
    DockPanel dck = new DockPanel();
    dck.Width = 700;
    dck.Height = 400;
    dck.LastChildFill = true;
    Border b1 = new Border();
    b1.Width = 150;
    b1.Background = Brushes.Black;
    DockPanel.SetDock(b1, Dock.Left);
    dck.Children.Add(b1);
    Border b2 = new Border();
    b2.Width = 150;
    b2.Background = Brushes.Black;
    DockPanel.SetDock(b2, Dock.Right);
    dck.Children.Add(b2);
    Border b3 = new Border();
    b3.Height = 100;
    b3.Background = Brushes.Purple;
    DockPanel.SetDock(b3, Dock.Top);
    dck.Children.Add(b3);
    Border b4 = new Border();
    b4.Height = 100;
    b4.Background = Brushes.Purple;
    DockPanel.SetDock(b4, Dock.Bottom);
    dck.Children.Add(b4);
    Border b5 = new Border();
    b5.Width = 75;
    b5.Background = Brushes.DarkBlue;
    DockPanel.SetDock(b5, Dock.Left);
    dck.Children.Add(b5);
    Border b6 = new Border();
    b6.Width = 75;
    b6.Background = Brushes.DarkBlue;
    DockPanel.SetDock(b6, Dock.Right);
    dck.Children.Add(b6);
    Border b7 = new Border();
    b7.Height = 50;
    b7.Background = Brushes.RoyalBlue;
    DockPanel.SetDock(b7, Dock.Top);
    dck.Children.Add(b7);
    Border b8 = new Border();
    b8.Height = 50;
    b8.Background = Brushes.RoyalBlue;
    DockPanel.SetDock(b8, Dock.Bottom);
    dck.Children.Add(b8);
    Border b9 = new Border();
    DockPanel.SetDock(b9, Dock.Top);
    dck.Children.Add(b9);
    this.Content = dck;
}
```

{{% /expand %}}

### e. Le Canvas

On déclare un objet Canvas comme suit :

    Canvas cv = new Canvas();

Evidemment, les figures que nous avions vues dans la première partie de ce chapitre, comme le rectangle ou l’ellipse sont elles aussi des objets :

    Rectangle rect = new Rectangle();
    rect.Width = 100;
    rect.Height = 75;
    rect.Fill = Brushes.AliceBlue;
    rect.Stroke = Brushes.Black;
    rect.StrokeThickness = 5;

On peut choisir la position précise de l’élément grâce aux propriétés SetRight, SetLeft, SetTop, SetBottom :

    Canvas.SetBottom(rect, 100);
    Canvas.SetRight(rect, 10);

Enfin, on ajoute notre figure au Canvas comme suit :

    cv.Children.Add(rect);

{{% exercice %}}
Essayez d’obtenir grâce au Canvas et en dynamique le résultat suivant :
{{% /exercice %}}

![image12](/img/3.2/img12.png?height=200px)

{{% expand "Correction" %}}

```csharp
public MainWindow()
{
    InitializeComponent();
    Canvas cv = new Canvas();
    cv.Width = 1500;
    cv.Height = 1500;
    Rectangle r1 = new Rectangle();
    r1.Width = 500;
    r1.Height = 170;
    r1.Fill = Brushes.Red;
    Canvas.SetLeft(r1, 170);
    Canvas.SetTop(r1, 60);
    Rectangle r2 = new Rectangle();
    r2.Width = 700;
    r2.Height = 170;
    r2.Fill = Brushes.Red;
    Canvas.SetLeft(r2, 70);
    Canvas.SetTop(r2, 170);
    Rectangle r3 = new Rectangle();
    r3.Width = 150;
    r3.Height = 80;
    r3.Fill = Brushes.LightSkyBlue;
    Canvas.SetLeft(r3, 450);
    Canvas.SetTop(r3, 85);
    Rectangle r4 = new Rectangle();
    r4.Width = 150;
    r4.Height = 80;
    r4.Fill = Brushes.LightSkyBlue;
    Canvas.SetLeft(r4, 215);
    Canvas.SetTop(r4, 85);
    Ellipse e1 = new Ellipse();
    e1.Width = 150;
    e1.Height = 150;
    e1.Fill = Brushes.Black;
    Canvas.SetLeft(e1, 120);
    Canvas.SetTop(e1, 230);
    Ellipse e2 = new Ellipse();
    e2.Width = 150;
    e2.Height = 150;
    e2.Fill = Brushes.Black;
    Canvas.SetLeft(e2, 550);
    Canvas.SetTop(e2, 230);
    cv.Children.Add(r1);
    cv.Children.Add(r2);
    cv.Children.Add(r3);
    cv.Children.Add(r4);
    cv.Children.Add(e1);
    cv.Children.Add(e2);
    this.Content = cv;
}
```

{{% /expand %}}

## 3. Pourquoi utiliser la création dynamique ?

La création dynamique est un outil très puissant qui va vous permettre de modifier votre contenu XAML au cours de l’exécution de votre code.

Cela vous permettra à tout instant d’ajouter, de supprimer, de modifier un élément ou certaines de ces propriétés en fonctions des actions réalisées par l’utilisateur.

Voici un exemple de ce que l’on peut faire.
Créez un nouveau projet WPF et entrez le code suivant dans la fenêtre XAML, en ayant pris soin d’affecter à la fenêtre une dimension 1000*1000 :

```xml
<Grid>
    <Grid Name="grid1" ShowGridLines="true" Width="600" Height="600" VerticalAlignment="Top" HorizontalAlignment="Right">
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
    </Grid>
</Grid>
```

Comme vous pouvez le voir, nous venons de créer une grille qui a trois lignes et trois colonnes de mêmes dimensions.
Nous donnons le nom grid1 à notre grille, ce qui aura,nous le verrons, une importance par la suite. A noter que la propriété suivante permettra d’afficher les lignes et colonnes de notre grille :

    myGrid.ShowGridLines = true;

Nous allons maintenant créer un premier StackPanel (n’oubliez pas de le placer à l’intérieur de la première Grid, et sous la balise fermante de la deuxième Grid) :

```xml
<StackPanel HorizontalAlignment="Left" Orientation="Vertical">
    <Button Width="125" Height="100" Click="addCol">Add Column</Button>
    <Button Width="125" Height="100" Click="addRow">Add Row</Button>
</StackPanel>
```

Comme vous l’avez vu dans les chapitres précédents, la propriété Click va nous permettre de créer des fonctions dans le `.cs` afin de réaliser un évènement lorsqu’on cliquera sur le bouton. Ajoutons maintenant un deuxième StackPanel :

```xml
<StackPanel HorizontalAlignment="Left" Orientation="Vertical" Margin="125 0 0 0">
    <Button Width="125" Height="100" Click="insertRowAt">Insert Row</Button>
    <TextBox Text="" Name="tp1" Height="100" Width="125" Background="AliceBlue" TextWrapping="Wrap" IsReadOnly="True"/>
    <Button Width="125" Height="100" Click="insertColAt">Insert Column</Button>
    <TextBox Text="" Name="tp2" Height="100" Width="125" Background="AliceBlue" TextWrapping="Wrap" IsReadOnly="True"/>
</StackPanel>
```

Là encore, il est important de remarquer que nous avons donné des noms à nos deux TextBox. La propriété IsReadOnly indique le fait que l’utilisateur ne peut pas écrire dans cette TextBox. Enfin, ajoutons un troisième et dernier StackPanel :

```xml
<StackPanel HorizontalAlignment="Left" Orientation="Vertical" Margin="250 0 0 0">
   <Button Width="125" Height="100" Click="addBut">Add Button</Button>
   <TextBox Text="" Width="125" Height="100" Name="txtbx" TextWrapping="Wrap" IsReadOnly="True"/>
   <TextBox Text="" Width="125" Height="100" Name="txtbx2" TextWrapping="Wrap" TextChanged="txtbx2_changed"/>
</StackPanel>
```

Exécutez le code. Vous devriez avoir un résultat comme suit :

![image14](/img/3.2/img14.png?height=300px)

Nous allons maintenant créer les fonctions Click dans notre `.cs` qui nous permettront de réaliser les actions proposées par les boutons. Premièrement, dans la `MainWindow.xaml.cs`, supprimez ce qui suit :

    public MainWindow()
    {
        InitializeComponent();
    }

Ensuite, il nous faut ajouter quelques variables :

    RowDefinition rowDef1;
    ColumnDefinition colDef1;
    bool ligne = true;
    int c1 = -1;
    int c2 = -1;

Une fois que cela est fait nous allons commencer par créer la fonction qui nous permettra d’ajouter une colonne :

    private void addCol(object sender, RoutedEventArgs e)
    {
        colDef1 = new ColumnDefinition();
        grid1.ColumnDefinitions.Add(colDef1);
    }

Remarquez que nous nous sommes servis dans cette fonction de notre variable de clase rowDef1. Remarquez aussi que nous avons pu ajouter une colonne directement à notre grille créée depuis la fenêtre XAML en se servant du nom que nous lui avions défini (grid1). On voit ici qu’on peut se référer à notre instance de Grid créée en XAML depuis notre `.cs` en utilisant son nom.

Une fois cette fonction réalisée, on peut facilement écrire la fonction qui permet d’ajouter une ligne. Cette tâche est d’ailleurs laissée comme exercice.

Maintenant, créons la fonction qui nous permettra d’insérer une colonne :

    private void insertColAt(object sender, RoutedEventArgs e)
    {
        colDef1 = new ColumnDefinition();
        grid1.ColumnDefinitions.Insert(grid1.ColumnDefinitions.Count, colDef1);
        tp2.Text = "ColumnDefinition added at index position " +                                                                                                            grid1.ColumnDefinitions.IndexOf(colDef1).ToString();
    }

Nous pouvons remarquer que la propriété ColumnDefinitions.Insert permet de choisir à quelle position nous allons insérer notre élément. Là encore, nous pouvons modifier le texte de notre TextBox créée depuis notre XAML grâce à son prénom et à la propriété Text. En exercice, créez cette fonction mais qui permettra d’insérer non plus une colonne mais une ligne.
Enfin, nous allons créer la fonction qui permet de rajouter un bouton à l’emplacement désiré.  
Tout d’abord, créez la fonction addBut qui modifiera le texte de notre TextBox txtbx en lui affectant :

    "Choisissez la ligne où insérer le bouton dans la TextBox ci-dessous"

Enfin créez la fonction qui répond à l’évènement TextChanged de la TextBox. La fonction suivante est commentée pour vous aider à sa compréhension :

```csharp
private void txtbx2_changed(object sender, EventArgs e)
{
    int test; //Permet de récupérer le texte de l'utilisateur si c'est un entier
    if (int.TryParse(txtbx2.Text, out test))//Test si la string est un int
    {
        if(ligne == true)//Si nous choisissons le numéro de la ligne
        {
            if(test>=0 && test<grid1.RowDefinitions.Count)//Si l'index que nous donnons est valide
            //A noter que RowDefinitions.Count permet d'obtenir le nombre total de Rows
            {
                c1 = test;//c1 est notre index pour la ligne
                txtbx2.Text = "";//On vide notre TextBox txtbx2
                txtbx.Text = "Choisissez la colonne où insérer le bouton dans la TextBox ci-dessous";//On modifie le texte de notre TextBox txtbx
                ligne = false;//On va maintenant choisir la colonne
            }
            else
            {
                txtbx.Text = "Veuillez choisir un numéro de ligne valide";//Sinon on demande à l'utilisateur un index valide
                txtbx2.Text = "";
            }
        }
        else//Si nous choisissons le numéro de la colonne
        {
            if (test >= 0 && test < grid1.ColumnDefinitions.Count)//Si la colonne existe
            {
                c2 = test;//Notre coordonnée pour la colonne vaut test
                txtbx2.Text = "";//On vide la TextBox txtbx2
                txtbx.Text = "Bouton inséré !";//On modifie le texte de la TextBox txtbx
                ligne = true;//Si prochaine insertion, on fixe la ligne
                Button b = new Button();//On crée le bouton à insérer
                b.Content = "Bouton";//On lui affecte le texte Bouton
                b.Background = Brushes.AliceBlue;//On lui affecte un Background
                Grid.SetRow(b, c1);//On affecte la row choisie au bouton
                Grid.SetColumn(b, c2);//On affecte la column choisie au bouton
                grid1.Children.Add(b);//On ajoute notre bouton à la grille
            }
            else//Sinon le numéro n'est pas valide
            {
                txtbx.Text = "Veuillez choisir un numéro de colonne valide";
                txtbx2.Text = "";
            }
        }
    }
    else//Sinon le numéro n'est pas valide ou nous avons saisie une string
    {
        txtbx2.Text = "";
        txtbx.Text = "Veuillez choisir un nombre entier valide";
    }
}
```

Jouez avec le code et voyez ce que permet la création dynamique !

Evidemment, bien plus de possibilités s’offrent à vous, vous pouvez réaliser bien plus de chose que simplement ajouter des lignes, des colonnes et des boutons.
