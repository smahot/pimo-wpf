+++
title = "DataBinding et classe"
weight = 4001
pre = "<b>4.1 </b>"
+++

- [1. Data Binding sur des variables](#1-data-binding-sur-des-variables)
  - [a. One Way Data Binding](#a-one-way-data-binding)
  - [a. One Way To Source Data Binding](#a-one-way-to-source-data-binding)
  - [c. One Time Databinding](#c-one-time-databinding)
  - [d. Two Way Databinding](#d-two-way-databinding)
- [2. Data Binding sur des classes](#2-data-binding-sur-des-classes)
  - [a. One-Way Data Binding](#a-one-way-data-binding-1)
  - [b. Two-Way Data Binding](#b-two-way-data-binding)
  - [c. Data Binding : ListBox et classe Person](#c-data-binding--listbox-et-classe-person)

Le databinding est une des fonctionnalités les plus importantes du WPF. Dans cette partie du cours, nous allons voir les différents types de databinding.

## 1. Data Binding sur des variables

Dans cette partie, nous utiliserons le Data Binding sur des variables. Plus tard, vous verrez leur utilisation sur des classes.

### a. One Way Data Binding

En one way databinding,  la valeur source va affecter la valeur cible. Dans votre code, il faudra implémenter une section.  
Dans votre code, il faudra alors utiliser l’extension System.Windows.Data.Binding en passant en mode “OneWay”.

Voici un exemple : entrez le code ci desous dans le fichier xaml d'un projet wpf (attention au nom du projet ! ici, il s'appelle exmple_oneway).

```xml
<Window x:Class="exemple_oneway.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:exemple_oneway"
        mc:Ignorable="d"
        Title="MainWindow" Height="350" Width="525">
    <Grid>
        <StackPanel Orientation="Vertical">
            <Slider Name="mySlider" Maximum="100" Minimum="0" Margin="20"></Slider>
            <TextBox Name="txtValue" Text="{Binding ElementName=mySlider, Path=Value, Mode=OneWay}" Margin="20" Width="50" Height="30"></TextBox>
        </StackPanel>
    </Grid>
</Window>

```

Vous obtiendrez la fenêtre suivante : 

![image11](/img/4.1/im1.png?height=400px)

Essayez de faire varier le slider. Vous verrez alors que la valeur contenue dans la Textbox changera.

![image12](/img/4.1/im2.png?height=400px)

Cependant, si vous essayez d’insérer une valeur dans la Textbox, la valeur du slider ne sera pas mise à jour.

![image13](/img/4.1/im3.png?height=400px)



### a. One Way To Source Data Binding

En one way to source databinding, la cible contrôle la mise à jour de la valeur source. Il s’agit tout simplement de l’inverse du one way databinding. Comme pour notre exemple vu en one way, nous allons réaliser l’exemple inverse, c’est-à-dire la textbox va update le slider.

Exemple : Entrez le code suivant :

```xml
<Window x:Class="exemple_onewaytosource.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:exemple_onewaytosource"
        mc:Ignorable="d"
        Title="MainWindow" Height="350" Width="525">
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
</Window>
```

Vous obtiendrez alors la fenêtre suivante :

![image13](/img/4.1/im4.PNG?height=400px)

Si vous changez la valeur contenue dans la textbox, le slider bougera en fonction de cette valeur, mais pas inversement.


### c. One Time Databinding

Le one time databinding fonctionne comme le one way à l’exception qu’il ne fonctionne qu’une seule fois. C’est-à-dire que la valeur cible pourra être changée uniquement à l’initialisation de votre code. Cela signifie qu’elle ne peut être changée que dans votre code WPF, aucune autre extension de code est nécessaire.

### d. Two Way Databinding

Comme son nom l’indique, en two way databinding, la source va update la cible et vice-versa. Cela implique que si la valeur de la source est changée, la valeur de la cible le sera aussi changée. Si la valeur de la cible est changée, la valeur de la source le sera aussi.
Dans votre code, il faudra alors utiliser l’extension System.Windows.Data.Binding comme ceci :
•	Passer l’attribut mode en “TwoWay”
•	Utiliser l’attribut UpdateSourceTrigger pour signaler quand est-ce que la source devrait être updatée. Pour cela, il faut passer la valeur de cet attribut à “PropertyChanged”. La mise à jour de la valeur se fera alors automatiquement.

Voilà un autre exemple : copiez les code ci-dessous dans votre ficher xaml.

```xml
<Window x:Class="TwoWayBinding.Window1"

    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    Title="Window1" Height="361.648" Width="543.608">
    <Grid Height="54" Width="165">
        <TextBox  Name="textBox" Margin="0,-77,0,0" Height="23" VerticalAlignment="Top"
                Text ="{Binding ElementName=listBox,
                        Path=SelectedItem.Content,
                        Mode=TwoWay,
                        UpdateSourceTrigger=PropertyChanged}"
                Background="{Binding ElementName=listBox, Path=SelectedItem.Content, Mode=OneWay}" HorizontalAlignment="Left" Width="165">
        </TextBox>
        <ListBox Name="listBox"  >
            <ListBoxItem Content="Green"/>
            <ListBoxItem  Content="Yellow" IsSelected="True"/>
            <ListBoxItem Content="Orange" />
        </ListBox>
    </Grid>
</Window>
```
Vous obtiendrez alors la fenêtre suivante :

![image15](/img/4.1/im5.PNG?height=400px)

Lorsque vous parcourez les éléments dans la liste, vous pouvez voir que la valeur de la Textbox et sa couleur changent en même temps que vous choisissez un élément de la liste. De plus, si vous écrivez du texte dans la Textbox, la valeur que vous avez sélectionnée dans la liste changera aussi.

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

