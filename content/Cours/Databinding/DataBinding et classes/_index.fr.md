+++
title = "DataBinding et classe"
weight = 4001
pre = "<b>4.1 </b>"
+++

- [One-Way Data Binding](#one-way-data-binding)
- [Two-Way Data Binding](#two-way-data-binding)
- [Data Binding : ListBox et classe Person](#data-binding--listbox-et-classe-person)

Dans cette partie, nous allons vous montrer qu’il est possible de faire ce databinding via les variables d’une classe.
Nous allons vous montrer ici un exemple basique en utilisant une classe Personne.

## One-Way Data Binding

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

## Two-Way Data Binding

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

## Data Binding : ListBox et classe Person

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
