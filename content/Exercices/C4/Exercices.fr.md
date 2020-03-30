+++
title = "Databinding - Exercices"
weight = 401
pre = "<b>4.1 </b>"
+++

## 4.1 Data Binding <!-- omit in toc -->

- [Exercice 1 : La Base](#exercice-1--la-base)
- [Exercice 2 : Des Rectangles](#exercice-2--des-rectangles)
- [Exercice 3 : Chien en laisse](#exercice-3--chien-en-laisse)
- [Exercice 4 : Databinding, classe et Listbox.](#exercice-4--databinding-classe-et-listbox)

### Exercice 1 : La Base

{{% exercice %}}
Créer une TextBox qui affiche ce que l’utilisateur a écrit :
{{% /exercice %}}

![image1](/img/4.1/exos/im01.png?height=300px)

{{% expand "Correction" %}}

```xml
<Window x:Class="exo_databinding.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:exo_databinding"
        mc:Ignorable="d"
        Title="MainWindow" Height="350" Width="525">
    <StackPanel Margin="10">
        <TextBox Name="txtValue"/>
        <TextBlock Text="Value: " FontWeight="Bold" />
        <TextBlock Text="{Binding Path=Text, ElementName=txtValue}" />
 
    </StackPanel>
 
 
</Window>

```

{{% /expand %}}

---


### Exercice 2 : Des Rectangles

{{% exercice %}}
Faites en sorte que lorsque l’on entre une valeur dans la TextBox, le rectangle de droite pivote de (valeur) degrés. C’est-à-dire bindez la valeur dans la TextBox à la valeur de rotation du rectangle bleu.
Aide : Utilisez un StackPanel pour l’user input et une grid pour la position des rectangles
{{% /exercice %}}

![image1](/img/4.1/exos/im02.png?height=300px)

{{% expand "Correction" %}}

```xml
<Window x:Class="WpfApplication4.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApplication4"
        mc:Ignorable="d"
        Title="MainWindow" Height="350" Width="525">
 
    <StackPanel Margin="10">
 
        <StackPanel.Resources>
 
 
            <Style TargetType="Rectangle">
                <Setter Property="Width" Value="50" />
                <Setter Property="Height" Value="100" />
                <Setter Property="Stroke" Value="Black" />
                <Setter Property="StrokeThickness" Value="1" />
                <Setter Property="Margin" Value="10" />
            </Style>
 
        </StackPanel.Resources>
 
        <StackPanel Orientation="Horizontal" Margin="10">
            <Label Content="Choisissez un angle:" />
            <TextBox Width="100" Name="txtAngle" />
        </StackPanel>
 
        <Grid Margin="10">
            <Grid.RowDefinitions>
                <RowDefinition Height="200" />
            </Grid.RowDefinitions>
            <Grid.ColumnDefinitions>
                <ColumnDefinition />
 
                <ColumnDefinition />
            </Grid.ColumnDefinitions>
 
 
 
            <Label Grid.Row="1" Grid.Column="0" FontWeight="Bold" HorizontalContentAlignment="Center" Content="Avant" />
            <Label Grid.Row="1" Grid.Column="2" FontWeight="Bold" HorizontalContentAlignment="Center" Content="Après" />
 
 
            <Rectangle Grid.Row="2" Grid.Column="0" Fill="Red" />
 
           
 
            <Rectangle Grid.Row="2" Grid.Column="2" Fill="Blue">
                <Rectangle.RenderTransform>
                    <RotateTransform Angle="{Binding ElementName=txtAngle, Path=Text}" />
                </Rectangle.RenderTransform>
            </Rectangle>
 
        </Grid>
 
    </StackPanel>
</Window>


```

{{% /expand %}}

---


### Exercice 3 : Chien en laisse

{{% exercice %}}
Question 1 : Créez une classe “Chien” qui décrit un chien grâce à son nom et sa race.   
Question 2 : Instanciez un objet de cette classe que vous appellerez “dog”.  
Question 3 : Créez une textbox pour chaque propriété de la classe Chien.  
Question 4 : Faites un data binding afin que les informations de cet objet apparaissent dans différentes textbox.
{{% /exercice %}}

{{% expand "Correction" %}}

```csharp
public class Chien
    {

        private string race;

        public string Race
        {
            get { return race; }
            set { race = value; }
        }

        private string name;

        public string Name
        {
            get { return name; }
            set { name = value; }
        }
    }
```
```csharp
Chien dog = new Chien(){ Name = "Rex", Race = "bulldog" };
```

```xml
Title="MainWindow" Height="200" Width="350">

<Grid Margin="0,0,0,4.4">

<Grid.RowDefinitions>

<RowDefinition Height="67*"/>

<RowDefinition Height="18*"/>

</Grid.RowDefinitions>

<Label Name = "nameLabel" Margin = "7,17,281,79.4">_Name:</Label>

<TextBox Name = "nameText" Margin = "53,17,42,79.4"

Text = "{Binding Name, Mode = OneWay}" RenderTransformOrigin="0.519,0.575"/>

<Label Name = "raceLabel" Margin = "7,67,291,29.2">_Race:</Label>

<TextBox Name = "ageText" Margin = "53,67,42,29.4"

Text = "{Binding Race, Mode = OneWay}"/>

    </Grid>

```
```csharp
public MainWindow()
        {
            InitializeComponent();
            Chien dog = new Chien(){ Name = "Rex", Race = "bulldog" };
            this.DataContext = dog;
        }

```

{{% /expand %}}

---


### Exercice 4 : Databinding, classe et Listbox.

{{% exercice %}}
Reprenez la classe que vous avez créée dans l’exercice précédent. Faites cette fois ci un databinding via une listbox. Cette listbox devra afficher toutes les instances de la classe chien qui auront été créées.
{{% /exercice %}}