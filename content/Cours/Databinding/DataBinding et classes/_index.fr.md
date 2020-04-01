+++
title = "DataBinding et classe"
weight = 4001
pre = "<b>4.1 </b>"
+++

- [1. Data Binding sur des éléments](#1-data-binding-sur-des-%c3%a9l%c3%a9ments)
  - [a. L'origine du problème](#a-lorigine-du-probl%c3%a8me)
  - [b. One Way Data Binding](#b-one-way-data-binding)
  - [c. Two Time Databinding](#c-two-time-databinding)
  - [d. One Time Databinding](#d-one-time-databinding)
  - [e. One Way To Source Databinding](#e-one-way-to-source-databinding)
- [2. Data Binding sur des classes](#2-data-binding-sur-des-classes)
  - [a. One-Way Data Binding](#a-one-way-data-binding)
  - [b. Two-Way Data Binding](#b-two-way-data-binding)
  - [c. Data Binding : ListBox et classe Person](#c-data-binding--listbox-et-classe-person)



## 1. Data Binding sur des éléments

Le databinding est une des fonctionnalités les plus importantes de WPF. Le principe est simple : vous désignez une variable ou classe que vous affichez à l’aide d’un élément comme textblock ou textbox. 

### a. L'origine du problème

Pour commencer, nous allons nous attarder au databinding sur un élément. Plus tard, nous vous expliquerons comment cela fonctionne avec une classe.

Prenons un exemple : 
```xml
<Grid>
        <TextBox x:Name="Affichage" Width="400" Height="200" FontSize="50" Foreground="Purple" Text="Bonjour"/>
        <TextBlock x:Name="relier" Width="400" Height="100" HorizontalAlignment="Center" VerticalAlignment="Bottom" FontSize="30" Text="Bonjour" />
 </Grid>
```
Lorsque vous lancez le programme, Bonjour s’affiche dans les deux textbox et textblock, pas de souci.

![image13](/img/4.1/im01.png?height=400px)

Vous pouvez aussi modifier le texte du Textbox (en violet). Cependant, cela ne modifie pas le contenue du textblock. Encore une fois, c’est normal, les deux contenues (ici, Text) ont été définis séparément.
Supposons que vous voulez que ce que vous écrivez dans le textbox s’affiche aussi dans le textblock, comment faire ?

Une possibilité, peu élégante, serait de rajouter un bouton qui aurait un événement qui copierait le text du textbox et le mettrait dans le textbloc. L’ennui, c’est que cela demande une intervention directe de la part de l’utilisateur, et le changement ne se fait pas en temps réel.
Pour résoudre ce problème, nous allons alors utiliser le Data Binding !


### b. One Way Data Binding

Le databinding permet d’update en temps réel la variable auquel il est attribué. Cela permet d’éviter le scénario décrit plus haut qui utiliserait un bouton.
Pour ce faire, rien de plus simple, on va ajouter à l’attribut Text de notre Textblock la ligne suivante :
"{Binding ElementName=Affichage, Path=Text, Mode=OneWay}"
Ce qui nous donnerait :

```xml
<Grid>
        <TextBox x:Name="Affichage" Width="400" Height="200" FontSize="50" Foreground="Purple" Text="Bonjour"/>
        <TextBlock x:Name="relier" Width="400" Height="100" HorizontalAlignment="Center" VerticalAlignment="Bottom" FontSize="30" Text="{Binding ElementName=Affichage, Path=Text, Mode=OneWay}"/>
</Grid>
```
Compilez, vous allez voir, c’est magique ! Tout ce que vous écrivez dans le Textbox va effectivement se retrouver dans le Textblock.

![image13](/img/4.1/im02.png?height=400px)

- {Binding …} : il s’agit de la nomenclature normale lorsque l’on fait usage du databinding.
ElementName=… : il faut renseigner le Name de l’élément que vous voulez databinder, dont vous voulez récupérer le Text/Content. Ici, il s’agit de Affichage.

- Path=… : il faut renseigner l’attribut à cibler de l’élément. Normalement, on met Text ou Content en fonction de l’élément ciblé. Ici, on vise un Textblock, donc Text.

- Mode=… : Une propriété très intéressante que nous allons voir tout de suite. 

- OneWay = Pour faire simple, il s’agit du sens d’update de la variable. OneWay signifie dans notre cas que « relier » va changer en fonction d’ « affichage », mais pas l’inverse. Par exemple, vous voyer bien que modifier Affichage modifie aussi « relier ». Mais si l’ont crée un événement qui modifie le texte de « relier », alors le texte d’ « affichage » ne change pas.

Pour vérifier cela, transformez « relier » en textbox :

```xml
<Grid>
        <TextBox x:Name="Affichage" Width="400" Height="200" FontSize="50" Foreground="Purple" Text="Bonjour" TextWrapping="Wrap"/>
        <TextBox x:Name="relier" Width="400" Height="100" HorizontalAlignment="Center" VerticalAlignment="Bottom" TextWrapping="Wrap" FontSize="30" Text="{Binding ElementName=Affichage, Path=Text, Mode=OneWay}"/>
</Grid>
```
![image13](/img/4.1/im03.png?height=400px)

Bien que j’eusse écris hello en haut, puis magie dans « relier », rien ne change en haut.

Voilà un autre exemple un peu plus ‘concret’ utilisant un slider : 
```xml
<Grid>
        <StackPanel Orientation="Vertical">
            <Slider Name="mySlider" Maximum="100" Minimum="0" Margin="20"></Slider>
            <TextBox Name="txtValue" Text="{Binding ElementName=mySlider, Path=Value, Mode=OneWay}" Margin="20" Width="50" Height="30"></TextBox>
        </StackPanel>
    </Grid>

```
![image13](/img/4.1/im04.png?height=400px)

On retrouve deux éléments : un slider, et un textbox. Le databinding se fait dans le Textbox avec 
Text="{Binding ElementName=mySlider, Path=Value, Mode=OneWay}"
L’élément ciblé est le Slider (ElementName=mySlider), et l’on veut utiliser sa valeur, donc Path=Value. Le tout en mode OneWay.
Lancez le programme, et voyez comment évolue le chiffre dans la textbox avec le slider. Bien entendu, modifier le contenue de txtValue ne changera pas le slider.

{{% exercice %}}
Un petit exemple que vous allez réaliser :
Créez une grid de 3*3 avec un textbox au centre et 8 buttons sur les bords qui seront databindé au textbox du milieu.
{{% /exercice %}}

![image13](/img/4.1/im05.png?height=400px)

{{% expand "Correction" %}}

```xml
<Grid>
        <Grid>
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="1*"/>
                <ColumnDefinition Width="1*"/>
                <ColumnDefinition Width="1*"/>
            </Grid.ColumnDefinitions>
            <Grid.RowDefinitions>
                <RowDefinition Height="1*"/>
                <RowDefinition Height="1*"/>
                <RowDefinition Height="1*"/>
            </Grid.RowDefinitions>
            <TextBox x:Name="target" Grid.Column="1" Grid.Row="1" VerticalContentAlignment="Center" HorizontalAlignment="Center" TextWrapping="Wrap" Text="O" VerticalAlignment="Center"/>
            <Button Grid.Column="0" Grid.Row="0" Content="{Binding ElementName=target, Path=Text, Mode=OneWay}" />
            <Button Grid.Column="0" Grid.Row="1" Content="{Binding ElementName=target, Path=Text, Mode=OneWay}" />
            <Button Grid.Column="0" Grid.Row="2" Content="{Binding ElementName=target, Path=Text, Mode=OneWay}" />

            <Button Grid.Column="1" Grid.Row="0" Content="{Binding ElementName=target, Path=Text, Mode=OneWay}" />
            <Button Grid.Column="1" Grid.Row="2" Content="{Binding ElementName=target, Path=Text, Mode=OneWay}" />

            <Button Grid.Column="2" Grid.Row="0" Content="{Binding ElementName=target, Path=Text, Mode=OneWay}" />
            <Button Grid.Column="2" Grid.Row="1" Content="{Binding ElementName=target, Path=Text, Mode=OneWay}" />
            <Button Grid.Column="2" Grid.Row="2" Content="{Binding ElementName=target, Path=Text, Mode=OneWay}" />
        </Grid>
    </Grid>

```

{{%/expand%}}

---


### c. Two Time Databinding

Très similaire dans sa nomenclature, le data binding two way se distingue du One Way par un détail : si l’on modifie n’importe lequel des deux, alors l’autre sera aussi modifié.
Reprenons l’exemple du début, mais avec le data binding two way :

```xml
<Grid>
        <TextBox x:Name="Affichage" Width="400" Height="200" FontSize="50" Foreground="Purple" Text="Bonjour" TextWrapping="Wrap"/>
        <TextBox x:Name="relier" Width="400" Height="100" HorizontalAlignment="Center" VerticalAlignment="Bottom" TextWrapping="Wrap" FontSize="30" Text="{Binding ElementName=Affichage, Path=Text, Mode=TwoWay, UpdateSourceTrigger=PropertyChanged}"/>
    </Grid>
```

![image13](/img/4.1/im06.png?height=400px)

On a dû rajouter un paramètre dans la ligne de databinding, et il s’agit de UpdateSourceTrigger = PropertyChanged. Cela signifie que la source est update au moindre changement dans la cible.

{{% exercice %}}
Testons cela rapidement : dans une fenêtre, placez trois textbox, une au centre, une à gauche et une à droite. Celle de droite est relié en two way à celle du milieu et celle de gauche uniquement en one way à celle du milieu. Ensuite, essayez d’anticiper leur comportement puis vérifiez en changeant un à un le contenu des textbox.
{{% /exercice %}}

![image13](/img/4.1/im07.png?height=400px)

{{% expand "Correction" %}}
Ainsi, modifier : 
-	A gauche ne change rien dans les deux autres
-	Au centre modifie les deux qui sont bindés dessus
-	A droite modifie le centre qui modifie à gauche

```xml
<Grid>
        <TextBox x:Name="gauche" HorizontalAlignment="Left" Height="71" Margin="24,103,0,0" TextWrapping="Wrap" Text="{Binding ElementName=centre, Path=Text, Mode=OneWay}" VerticalAlignment="Top" Width="73"/>
        <TextBox x:Name="centre" HorizontalAlignment="Left" Height="71" Margin="154,103,0,0" TextWrapping="Wrap" Text="bonjour" VerticalAlignment="Top" Width="81"/>
        <TextBox x:Name="droite" HorizontalAlignment="Left" Height="71" Margin="276,103,0,0" TextWrapping="Wrap" Text="{Binding ElementName=centre, Path=Text, Mode=TwoWay, UpdateSourceTrigger = PropertyChanged}" VerticalAlignment="Top" Width="93"/>
</Grid>

```

{{%/expand%}}

---


### d. One Time Databinding

Le one time databinding fonctionne comme le one way à l’exception qu’il ne fonctionne qu’une seule fois. C’est-à-dire que la valeur cible pourra être changée uniquement à l’initialisation de votre code. Cela signifie qu’elle ne peut être changée que dans votre code WPF, aucune autre extension de code est nécessaire.

### e. One Way To Source Databinding

En one way to source databinding, la cible contrôle la mise à jour de la valeur source. Il s’agit tout simplement de l’inverse du one way databinding. Comme pour notre exemple vu en one way, nous allons réaliser l’exemple inverse, c’est-à-dire la textbox va update le slider.
On va prendre pour exemple le slider du début. En se plaçant dans le contexte du one way to source , on obtient cela : 

```xml
<Grid>
        <StackPanel Orientation="Vertical">

            <Separator BorderThickness="20" BorderBrush="Black"></Separator>
            <Slider Name="mySlider4" Maximum="100" Minimum="0" Margin="20"></Slider>
            <TextBox Name="txtvalue4" Text="{Binding ElementName=mySlider4,
                                                Path=Value,
                                                Mode=OneWayToSource, 
                                                UpdateSourceTrigger=PropertyChanged}" 
                                                Margin="20" Width="50" Height="30">
            </TextBox>
        </StackPanel>
    </Grid>

```
![image13](/img/4.1/im08.png?height=400px)

Cette fois ci, il faut écrire un nombre entre 1 et 100 pour faire bouger le slider, et pas l’inverse ! 

{{% exercice %}}
Afin de tester cette propriété, reprenez l’exemple des trois textbox. Cette fois ci, celui de droite sera data bindé avec un one way to source. Observez comment réagissent les textbox avec les différentes modifications alors !
{{% /exercice %}}

![image13](/img/4.1/im09.png?height=400px)

{{% expand "Correction" %}}
Ainsi, modifier : 
-	A gauche ne change rien dans les deux autres
-	Au centre modifie celui de gauche
-	A droite modifie le centre qui modifie à gauche

```xml
<Grid>
        <TextBox x:Name="gauche" HorizontalAlignment="Left" Height="71" Margin="24,103,0,0" TextWrapping="Wrap" Text="{Binding ElementName=centre, Path=Text, Mode=OneWay}" VerticalAlignment="Top" Width="73"/>
        <TextBox x:Name="centre" HorizontalAlignment="Left" Height="71" Margin="154,103,0,0" TextWrapping="Wrap" Text="bonjour" VerticalAlignment="Top" Width="81"/>
        <TextBox x:Name="droite" HorizontalAlignment="Left" Height="71" Margin="276,103,0,0" TextWrapping="Wrap" Text="{Binding ElementName=centre, Path=Text, Mode=OneWayToSource, UpdateSourceTrigger = PropertyChanged}" VerticalAlignment="Top" Width="93"/>
    </Grid>

```

{{%/expand%}}

---

## 2. Data Binding sur des classes

Dans cette partie, nous allons vous montrer qu’il est possible de faire ce databinding via les variables d’une classe.
Nous allons vous montrer ici un exemple basique en utilisant une classe Personne.

### a. One-Way Data Binding

![image1](/img/4.1/img01.png?height=200px)

Le code XAML ci-dessous, crée 2 labels, 2 textboxes et un bouton et les initialise avec quelques propriétés.

```xml
<Window x:Class="DataBinding.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:DataBinding"
        mc:Ignorable="d"
        Title="MainWindow" Height="200" Width="350">
    <Grid>
        <Grid.RowDefinitions>
            <RowDefinition Height="67*"/>
            <RowDefinition Height="18*"/>
        </Grid.RowDefinitions>

        <Label Name="nameLabel" Margin="7,17,281,79.4">_Name:</Label>

        <TextBox Name="nameText" Margin="53,17,42,79.4"
            Text="{Binding Name, Mode = OneWay}" RenderTransformOrigin="0.519,0.575"/>

        <Label Name="ageLabel" Margin="7,67,291,29.2">_Age:</Label>

        <TextBox Name="ageText" Margin="53,67,42,29.4"
            Text="{Binding Age, Mode = OneWay}"/>

        <Button Content="_Show..." Click="Button_Click" Margin="53,110,42,28.4" Grid.RowSpan="2"/>
    </Grid>
</Window>
```

- La propriété Text des deux textboxes sont bind aux variables Name et Age de la classe Person qui est montrée juste en dessous.
- Dans la classe Person, il y a juste 2 variables Name et Age, et une instance est initialisée dans la classe MainWindow.
- Dans le code XAML, nous faisons un data binding vers les propriétés Name et Age, mais nous n’avons pas sélectionné à quel objet appartiennent ces propriétés.
- La manière la plus simple est d’assigner un objet au DataContext dans le constructeur MainWindow.

```csharp
public partial class MainWindow : Window
{
    Person person = new Person { Name = "Jordan", Age = 22 };

    public MainWindow()
    {
        InitializeComponent();
        this.DataContext = person;
    }

    private void Button_Click(object sender, RoutedEventArgs e)
    {
        string message = person.Name + " is " + person.Age;
        MessageBox.Show(message);
    }
}

public class Person
{
    private string nameValue;

    public string Name
    {
        get { return nameValue; }
        set { nameValue = value; }
    }

    private double ageValue;

    public double Age
    {
        get { return ageValue; }

        set
        {
            if (value != ageValue)
            {
                ageValue = value;
            }
        }
    }
}
```

Executez l’application. Vous pouvez voir que dans notre MainWindow qu’il y a bien un data bind vers les varables Name and Age de l’objet Person.

![image2](/img/4.1/img02.png?height=200px)

Quand vous appuyez sur le bouton Show, cela affichera le nom et l'âge. Comme ceci :

![image3](/img/4.1/img03.png?height=200px)

Changeons le nom et l'âge :

![image4](/img/4.1/img04.png?height=200px)

Si vous appuyez encore une fois sur le bouton Show, cela affichera le même message que précédemment.

![image5](/img/4.1/img05.png?height=200px)

Cela est dû au fait que le mode de data binding est “one-way” dans le code XAML. Pour afficher la mise à jour de l'âge et du nom, il faut utiliser le two-way databinding.

### b. Two-Way Data Binding

Prenons le même exemple mais changeons le mode de dataBinding :

```xml
<Window x:Class="DataBinding.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:DataBinding"
        mc:Ignorable="d"
        Title="MainWindow" Height="200" Width="350">
    <Grid>
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="91*"/>
            <ColumnDefinition Width="253*"/>
        </Grid.ColumnDefinitions>
        <Grid.RowDefinitions>
            <RowDefinition Height="67*"/>
            <RowDefinition Height="18*"/>
        </Grid.RowDefinitions>

        <Label Name="nameLabel" Margin="7,17,28,79.4">_Name:</Label>

        <TextBox Name="nameText" Margin="53,17,42,79.4"
         Text="{Binding Name, Mode = TwoWay}" RenderTransformOrigin="0.519,0.575" Grid.ColumnSpan="2"/>

        <Label Name="ageLabel" Margin="7,67,38,29.4">_Age:</Label>

        <TextBox Name="ageText" Margin="53,67,42,29.4"
         Text="{Binding Age, Mode = TwoWay}" Grid.ColumnSpan="2"/>

        <Button Content="_Show..." Click="Button_Click" Margin="53,110,42,28.4" Grid.RowSpan="2" Grid.ColumnSpan="2" />
    </Grid>
</Window>
```

Exécutons l’application une nouvelle fois.

![image6](/img/4.1/img06.png?height=200px)

Cela va produire le même message que plus haut.

![image7](/img/4.1/img07.png?height=200px)

Changeons maintenant l'âge et le nom :

![image8](/img/4.1/img08.png?height=200px)

Si vous appuyez sur le bouton Show, vous verrez cette fois ci que le message a été mis à jour.

![image9](/img/4.1/img09.png?height=200px)

### c. Data Binding : ListBox et classe Person

Nous allons également voir pourquoi utiliser des observable collection plutôt que des List en WPF.
Nous reprendrons la classe Person qui a été créée juste avant.
Nous allons dans un premier temps créer une liste de Personne comme suit :

```csharp
public partial class MainWindow : Window
{
    List<Person> persons = new List<Person>();

    public MainWindow()
    {
        InitializeComponent();
        persons.Add(new Person() { Name = "Jordan", Age = 22 });
        persons.Add(new Person() { Name = "Marie", Age = 27 });
        persons.Add(new Person() { Name = "Pedro", Age = 54 });
        this.DataContext = persons;
    }
}
```

![image10](/img/4.1/img10.png?height=200px)

Le code XAML suivant crée une list box et un bouton.

```xml
<Window x:Class="DataBinding.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:DataBinding"
        mc:Ignorable="d"
        Title="MainWindow" Height="200" Width="350">
    <Grid>
        <ListBox Name="Persons" ItemsSource="{Binding}" Margin="47,10,48,34.4">
            <ListBox.ItemTemplate>
                <DataTemplate>
                    <StackPanel Orientation="Horizontal" Margin="2">
                        <TextBlock Text="Name : " Margin="2"/>
                        <TextBlock Text="{Binding Name}" Margin="2"/>
                        <TextBlock Text="Age : " Margin="2"/>
                        <TextBlock Text="{Binding Age}" Margin="2"/>
                    </StackPanel>
                </DataTemplate>
            </ListBox.ItemTemplate>
        </ListBox>
    </Grid>
</Window>
```

Si vous exécutez votre code, vous pouvez voir que les personnes ont été ajoutées à la liste :

![image11](/img/4.1/img11.png?height=200px)

Nous allons maintenant ajouter un bouton qui permettra d’ajouter des personnes.

![image12](/img/4.1/img12.png?height=200px)

```xml
<Button x:Name="addperson" Content="Add" HorizontalAlignment="Left" Margin="132,141,0,0" VerticalAlignment="Top" Width="75" Click="Addperson_Click"/>
```

Il faut également ajouter un événement Click à ce bouton :
Cet événement ajoute une personne à la liste persons.

```csharp
private void Addperson_Click(object sender, RoutedEventArgs e)
{
    persons.Add(new Person() { Name = "Clemence", Age = 47 });
}
```

Exécutez le code et appuyez sur le bouton :

![image13](/img/4.1/img13.png?height=200px)

Rien ne se passe.

Nous allons maintenant changer cette liste de Person en une ObservableCollection :

```csharp
ObservableCollection<Person> persons = new ObservableCollection<Person>();
```

Si on réexécute le code :

![image14](/img/4.1/img14.png?height=200px)

Une ObservableCollection va directement communiquer à l’interface utilisateur dès qu’il y a un changement dans la collection. Ce que la liste simple ne fait pas.

---

{{% button href="/exercices/c4/exercices/" %}}Lien vers les exercices{{% /button %}}

