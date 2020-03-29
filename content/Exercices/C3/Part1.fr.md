+++
title = "Les Layouts - Exercices"
weight = 301
pre = "<b>3.1 </b>"
+++

## 2.1 Les Layouts <!-- omit in toc -->

- [Exercice 1 : Des briques et des layouts](#exercice-1)
- [Exercice 2 : Enchaînement dans un StackPanel](#exercice-2)
- [Exercice 3 : Canva multicolor](#exercice-3)
- [Exercice 4 : Calculatrice](#exercice-4)
- [Exercice 5 : Dessin](#exercice-5)

### Exercice 1 : Des briques et des layouts

{{% exercice %}}
Le saviez-vous ? la force de ce genre de layouts est qu’ils peuvent s’imbriquer les uns dans les autres : par exemple, vous pouvez mettre des canvas dans des stackpanels, et inversement. Ce n’est pas forcément nécessaire, mais dans certains cas, lorsque l’interface devient complexe, il devient intéressant de tout « ranger » dans des cases. Pour cela, on utiliserait la grid avec ses columns et rows.  
![image1exo](/img/3.1/exo/im1.png?height=300px)  
A l’aide d’une grid, scindez la fenêtre  de 450 par 600 en quatre (deux lignes et deux colonnes, de même taille).
Dans la partie en haut à gauche, placez un stackpanel avec deux boutons.
Dans la partie en haut à droite, réutilisez l’exemple fournie plus haut avec les directions
Dans la partie en bas à gauche, définissez un wrappannel avec 6 boutons répartis sur deux lignes.
Dans la partie en bas à gauche, amusez vous à reproduire une cible de tir à l’arc (trois couleurs : bleu puis rouge puis jaune) et centrez-la.

{{% /exercice %}}

{{% expand "Correction" %}}

```xml
    Title="MainWindow" Height="450" Width="600">
    <!-- on commence par définir la grid-->
    <Grid>
        <!-- On va définir les deux colonnes avec chacune width="*" pour les ajuster automatiquement-->
        <Grid.ColumnDefinitions>
            <!-- première colonne-->
            <ColumnDefinition Width="*"/>
            <!-- première colonne-->
            <ColumnDefinition Width="*"/>
            <!-- si l'on voulait une troisième colonne, on rajoueterait la même ligne que précédement-->
        </Grid.ColumnDefinitions>
        
        <!-- Pareil avec les lignes avec height="*" pour les ajuster automatiquement-->
        <Grid.RowDefinitions>
            <!-- première ligne-->
            <RowDefinition Height="*"/>
            <!-- deuxième ligne-->
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>

        <!-- Nous voilà avec notre fenêtre scindée en 4 parties égales-->
        <!-- Passons maintenant au remplissage des parties-->
        
        <!-- Pour imbriquer un layout dans un autre, rien de plus simple : il faut placer ce layout entre les balises de celui qui l'englobe, de la  même façons qu'avec un bouton-->
        
        <!-- On définit donc notre stackpanel comme lors des exemples -->
        <!-- CEPENDANT ! pour bien préciser la partie de la grid dans laquelle on crée ce stackpanel, on va intégrer à la balise du stackpanel 
        Grid.Column="0" Grid.Row="0" comme pour un bouton ! Il faudra faire la même chose pour les autres layouts-->
        <StackPanel Grid.Column="0" Grid.Row="0">
            <!-- premier bouton-->
            <Button Height="100"> button 1</Button>
            <!-- deuxième bouton-->
            <Button Height="100"> Button 2</Button>
        </StackPanel>
        
        <!-- On définit notre wrappanel en y rajoutant sa position dans la grid-->
        <WrapPanel Grid.Column="0" Grid.Row="1">
            <!-- la construction est très semblable à ce qui a été donné dans un exemple du cours-->
            <!-- les boutons de largeur 95 se succèdent sur une même ligne jusqu'à dépaser la largeur du wrappanel et revenir à la ligne-->
            <Button Width="95">Button 1</Button>
            <Button Width="95">Button 2</Button>
            <Button Width="95">Button 3</Button>
            <!-- ici on revient à la ligne et on change la hauteur de tous les boutons de cette ligne grâce aux propriétés du wrappanel-->
            <Button Width="95" Height="65">Button 4</Button>
            <Button Width="95">Button 5</Button>
            <Button Width="95">Button 6</Button>
        </WrapPanel>
        
        <!-- Puis vient le tour du Dockpanel-->
        <!-- Fait un simple copy paste de l'exemple en adaptant les hauteurs/largeurs et en précisant la colonne/ligne de la grid-->
        <DockPanel Grid.Column="1" Grid.Row="0">
            <Button DockPanel.Dock="Top" Height="40">Top</Button>
            <Button DockPanel.Dock="Bottom" Height="40">Bottom</Button>
            <Button DockPanel.Dock="Right" Width="100">Right</Button>
            <Button DockPanel.Dock="Left" Width="100">Left</Button>
            <Button>Direction</Button>
        </DockPanel>
        
        <!-- Nous avons un quart de fenêtre, soit 225 de haut et 300 de large, un peu de réglage pour comprendre
        sera nécessaire pour bien tout centrer (environ...)-->
        <Canvas Grid.Column="1" Grid.Row="1">
            <!-- Les ellispse, à l'instar d'autres contrôles, vont avoir leur position déterminée par leur angle en haut à gauche si vous utilisez Canvas.left et top-->
            
            <!-- ellipse de diamètre 150, soit 75 de rayon pour une fenêtre de 300 de large = pour le centrer, il nous faut une "marge" (soit canvas.left) de 75 donc-->
            <!-- La fenêtre est haute de 225, et l'ellipse est de rayon 75. La marge sera d'à peu près 25-->
            <Ellipse Fill="#FF1E1EEC" Height="150" Canvas.Left="75" Stroke="Black" Canvas.Top="25" Width="150"/>
            
            <!-- On applique les mêmes calculs pour les cercles concentriques. Pour faire court, augmentez de 25 px les marges comme on diminue le rayons de 25 à chaque fois-->
            <Ellipse Fill="#FFEC1E1E" Height="100" Canvas.Left="100" Stroke="Black" Canvas.Top="50" Width="100"/>
            <Ellipse Fill="#FFECD91E" Height="50" Canvas.Left="125" Stroke="Black" Canvas.Top="75" Width="50"/>

        </Canvas>
            
    </Grid>

```

{{%/expand%}}

### Exercice 2 : Enchaînement dans un StackPanel

{{% exercice %}}
Expérimentons un peu avec les marges dans les layouts. Dans une fenêtre de 300 de haut et 600 de large, créez un stackpanel horizontal et placez-y autant de boutons carrés (bord = 50), chacun espacé de 10px avec l’autre et centré.

{{% /exercice %}}

![image2exo](/img/3.1/exo/im2.png?height=300px) 

{{% expand "Correction" %}}

```xml
<!-- on commence par définir le stackpanel en le mettant à l'horizontal-->
    <StackPanel Orientation="Horizontal" >
        <!-- On définit ensuite chaque bouton avec une marge de 5 pour que leur somme fasse 10-->
        <Button Height="50" Width="50" Margin="5">Button 1</Button>
        <Button Height="50" Width="50" Margin="5">Button 2</Button>
        <Button Height="50" Width="50" Margin="5">Button 3</Button>
        <Button Height="50" Width="50" Margin="5">Button 4</Button>
        <Button Height="50" Width="50" Margin="5">Button 5</Button>
        <Button Height="50" Width="50" Margin="5">Button 6</Button>
        <Button Height="50" Width="50" Margin="5">Button 7</Button>
        <Button Height="50" Width="50" Margin="5">Button 8</Button>
        <Button Height="50" Width="50" Margin="5">Button 9</Button>
        <!-- On ne peut plus en rajouter après-->
      
    </StackPanel>


```

{{%/expand%}}


### Exercice 3 : Canva multicolor

{{% exercice %}}
Dans un canva, créez un bouton d’une couleur différente dans chaque angle avec une marge de 20 px des bords. Lorsque vous appuyez sur un bouton, il doit faire changer la couleur du bouton suivant (dans le sens des aiguilles d’une montre).
{{% /exercice %}}

![image3exo](/img/3.1/exo/im3.png?height=300px) 

{{% expand "Correction XAML" %}}

```xml
<Canvas>
        <!-- Rien de spécial, on crée un canvas avec ses deux balises -->
        
        <!-- assez simple, on veut être à 20 px des bords, du coup, en haut à gauche, on demande une marge de 20 dans ces deux directions -->
        <Button x:Name="one" Background="Red" Canvas.Left="20" Canvas.Top="20" Width="50" Height="50" Click="One_Click">1</Button>

        <!-- même raisonnement pour les trois autres : on demande une marge de 20 sur les deux bords les plus proches. Ici : top et right -->
        <Button x:Name="two" Background="Green" Canvas.Right="20" Canvas.Top="20" Width="50" Height="50" Click="One_Click">2</Button>

        <!-- Ici : bottom et left -->
        <Button x:Name="four" Background="Blue" Canvas.Left="20" Canvas.Bottom="20" Width="50" Height="50" Click="One_Click">4</Button>

        <!-- ici : bottom et right -->
        <Button x:Name="three" Background="Yellow" Canvas.Right="20" Canvas.Bottom="20" Width="50" Height="50" Click="One_Click">3</Button>
        

    </Canvas>

```

{{%/expand%}}

{{% expand "Correction C#" %}}

```xml
public partial class MainWindow : Window
    {

       

        public string next_color(string enter)
        {   // cette fonction prend un string en entrée, qui sera le code héxadécimal de la couleur,
            // et retourne la couleur suivante sur le cycle

            // code héxadécimal des couleurs :
            // #FFFF0000 : rouge
            // #FF008000 : vert
            // #FFFFFF00 : jaune
            // #FF0000FF : bleu
            string ret = "#FFFF0000";

            if(enter == "#FFFF0000")
            {
                ret = "#FF008000";
            }
            else if (enter == "#FF008000")
            {
                ret = "#FFFFFF00";
            }
            else if (enter == "#FFFFFF00")
            {
                ret = "#FF0000FF";
            }
            else if (enter == "#FF0000FF")
            {
                ret = "#FFFF0000";
            }

            return ret;
        }

        public MainWindow()
        {
            InitializeComponent();
        }

        private void One_Click(object sender, RoutedEventArgs e)
        {
            // fonction qui est appelée lorsque l'on clique sur un bouton

            Button bt = sender as Button;

            if (bt.Name=="one")
            {   // si le bouton sur lequel on clique est 1, on va récupérer le code couleur du bouton suivant et prendre 
                // le code héxadécimal de la couleur suivante (ex : rouge -> vert, ou vert -> jaune...)

                // initialiser la variable qui va prendre le code couleur
                string colorValue = "";
                // on convertie en string le background du bouton 2
                colorValue = ((SolidColorBrush)two.Background).Color.ToString();
                
                // on récupére alors le nouveau code couleur...
                string next_col = next_color(colorValue);
                // que l'on convertie ensuite en background...
                SolidColorBrush col_brush = (SolidColorBrush)new BrushConverter().ConvertFromString(next_col);
                // puis que l'on applique au background du bouton 2
                two.Background = col_brush;
            }

            if (bt.Name == "two")
            { // même chose, mais pour le bouton deux vers le bouton trois
                string colorValue = "";


               
                colorValue = ((SolidColorBrush)three.Background).Color.ToString();
                


                string next_col = next_color(colorValue);
                
                SolidColorBrush col_brush = (SolidColorBrush)new BrushConverter().ConvertFromString(next_col);
                three.Background = col_brush;

            }

            if (bt.Name == "three")
            {   // même chose, mais pour le bouton trois vers le bouton quatre
                string colorValue = "";


                
                colorValue = ((SolidColorBrush)four.Background).Color.ToString();
                


                string next_col = next_color(colorValue);
                
                SolidColorBrush col_brush = (SolidColorBrush)new BrushConverter().ConvertFromString(next_col);
                four.Background = col_brush;

            }

            if (bt.Name == "four")
            {   // même chose, mais pour le bouton quatre vers le bouton un
                string colorValue = "";
              
                colorValue = ((SolidColorBrush)one.Background).Color.ToString();
                
                string next_col = next_color(colorValue);
                
                SolidColorBrush col_brush = (SolidColorBrush)new BrushConverter().ConvertFromString(next_col);
                one.Background = col_brush;

            }

        }
    }

```

{{%/expand%}}


### Exercice 4 : Calculatrice

{{% exercice %}}
La grid est très puissante : servez-vous en pour faire une calculatrice avec tous les boutons bien ordonnés en ligne et colonne. La photo finish et les events vous sont fournis pour que vous vous concentriez sur la mise en forme.
{{% /exercice %}}

![image4exo](/img/3.1/exo/im4.png?height=300px) 

{{% expand "Code C#" %}}

```xml
public partial class MainWindow : Window
    {
        // variables used for the calculations

        // variable for calculus
        double result = 0;
        double temp = 0;

        // variable for display and get input
        string result_s = "";
        string line = "";

        // variable used to know which operation to do
        string op = "default";


        public MainWindow()
        {
            InitializeComponent();
        }

        private void OnClickNum(object sender, RoutedEventArgs e)
        {
            Button bt = sender as Button;

            line = line + bt.Content;
            result_s = result_s + bt.Content;
            TextCalcul.Text = line;
        }

        private void OnClickOp(object sender, RoutedEventArgs e)
        {
            if (op == "default")
            {
                //check for the numbers
                if (result_s.Length > 0)
                {
                    temp = Convert.ToDouble(result_s);
                    result_s = "";
                }
                else
                {
                    temp = 0;
                }
                
                Button bt = sender as Button;
                if (bt.Name == "plus")
                {
                    op = "plus";
                    line = line + " + ";
                }
                else if (bt.Name == "minus")
                {
                    op = "minus";
                    line = line + " - ";
                }
                else if (bt.Name == "div")
                {
                    op = "div";
                    line = line + " / ";
                }
                else if (bt.Name == "mult")
                {
                    op = "mult";
                    line = line + " * ";
                }
                result = temp;
            }
            
            TextCalcul.Text = line;
        }

        private void OnclickEqual(object sender, RoutedEventArgs e)
        {
            if (op == "plus")
            {
                temp = Convert.ToDouble(result_s);
                result = result + temp;

                result_s = Convert.ToString(result);
                line = Convert.ToString(result);
            }
            else if (op == "minus")
            {
                temp = Convert.ToDouble(result_s);
                result = result - temp;

                result_s = Convert.ToString(result);
                line = Convert.ToString(result);
            }
            else if (op == "mult")
            {
                temp = Convert.ToDouble(result_s);
                result = result * temp;

                result_s = Convert.ToString(result);
                line = Convert.ToString(result);
            }
            else if (op == "div")
            {
                temp = Convert.ToDouble(result_s);
                result = result / temp;

                result_s = Convert.ToString(result);
                line = Convert.ToString(result);
            }
            op = "default";

            TextCalcul.Text = line;
        }

        private void OnClickClear(object sender, RoutedEventArgs e)
        {
            line = "";
            TextCalcul.Text = "0";
            op = "default";

            temp = 0;
            result = 0;
            result_s = "";

        }
    }


```

{{%/expand%}}


{{% expand "Correction XAML" %}}

```xml
<Grid>

        <Grid.RowDefinitions>
            <RowDefinition Height="*"/>
            <RowDefinition Height="*"/>
            <RowDefinition Height="*"/>
            <RowDefinition Height="*"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
        

        <!-- Textbox to display the result and the line being typed -->
        <StackPanel Grid.Column = "0" Grid.Row = "0" Orientation = "Horizontal" Background="LightBlue" >
            <TextBox x:Name="TextCalcul" HorizontalAlignment="Left" Margin="10,10,10,0" TextWrapping="Wrap" Text="Calculatrice" FontSize="40" TextAlignment="Center" VerticalAlignment="Top" Width="270" Height="80"/>
            <Button x:Name="erase" Content="Clear" FontSize="20" FontStyle="Italic" HorizontalAlignment="Left" Margin="10" VerticalAlignment="Top" Height="75" Width="76" Click="OnClickClear"/>
        </StackPanel>


        <StackPanel Grid.Column = "0" Grid.Row = "1" Orientation = "Horizontal" Background="LightBlue" >
            <!-- numeric button to write the desired expression -->
            <Button x:Name="one" Content="1" HorizontalAlignment="Left" Margin="10" FontSize="50" VerticalAlignment="Top" Height="75" Width="76" Click="OnClickNum" Background="#4bbce7"/>
            <Button x:Name="two" Content="2" HorizontalAlignment="Left" Margin="10" FontSize="50" VerticalAlignment="Top" Height="75" Width="76" Click="OnClickNum" Background="#4bbce7"/>
            <Button x:Name="three" Content="3" HorizontalAlignment="Left" Margin="10" FontSize="50" VerticalAlignment="Top" Height="75" Width="76" Click="OnClickNum" Background="#4bbce7"/>

            <!-- the operator buttons -->
            <Button x:Name="plus" Content="+" HorizontalAlignment="Left" Margin="10" FontSize="50" VerticalAlignment="Top" Height="75" Width="76" Click="OnClickOp" Background="#4294b4"/>
        </StackPanel>

        <StackPanel Grid.Column = "0" Grid.Row = "2" Orientation = "Horizontal" Background="LightBlue" >
            <!-- numeric button to write the desired expression -->
            <Button x:Name="four" Content="4" HorizontalAlignment="Left" Margin="10" FontSize="50" VerticalAlignment="Top" Height="75" Width="76" Click="OnClickNum" Background="#4bbce7"/>
            <Button x:Name="five" Content="5" HorizontalAlignment="Left" Margin="10" FontSize="50" VerticalAlignment="Top" Height="75" Width="76" Click="OnClickNum" Background="#4bbce7"/>
            <Button x:Name="six" Content="6" HorizontalAlignment="Left" Margin="10" FontSize="50" VerticalAlignment="Top" Height="75" Width="76" Click="OnClickNum" Background="#4bbce7"/>

            <!-- the operator buttons -->
            <Button x:Name="minus" Content="-" HorizontalAlignment="Left" Margin="10" FontSize="50" VerticalAlignment="Top" Height="75" Width="76" Click="OnClickOp" Background="#4294b4"/>
        </StackPanel>

        <StackPanel Grid.Column = "0" Grid.Row = "3" Orientation = "Horizontal" Background="LightBlue">
            <!-- numeric button to write the desired expression -->
            <Button x:Name="seven" Content="7" HorizontalAlignment="Left" Margin="10" FontSize="50" VerticalAlignment="Top" Height="75" Width="76" Click="OnClickNum" Background="#4bbce7"/>
            <Button x:Name="eight" Content="8" HorizontalAlignment="Left" Margin="10" FontSize="50" VerticalAlignment="Top" Height="75" Width="76" Click="OnClickNum" Background="#4bbce7"/>
            <Button x:Name="nine" Content="9" HorizontalAlignment="Left" Margin="10" FontSize="50" VerticalAlignment="Top" Height="75" Width="76" Click="OnClickNum" Background="#4bbce7"/>

            <!-- the operator buttons -->
            <Button x:Name="div" Content="/" HorizontalAlignment="Left" Margin="10" FontSize="50" VerticalAlignment="Top" Height="75" Width="76" Click="OnClickOp" Background="#4294b4"/>
        </StackPanel>

        <StackPanel Grid.Column = "0" Grid.Row = "4" Orientation = "Horizontal" Background="LightBlue">

            <!-- numeric button to write the desired expression -->
            <Button x:Name="point" Content="," HorizontalAlignment="Left" Margin="10" FontSize="50" VerticalAlignment="Top" Height="75" Width="76" Click="OnClickNum" Background="#4294b4"/>
            <Button x:Name="zero" Content="0" HorizontalAlignment="Left" Margin="10" FontSize="50" VerticalAlignment="Top" Height="75" Width="76" Click="OnClickNum" Background="#4bbce7"/>

            <!-- the operator buttons -->
            <Button x:Name="mult" Content="*" HorizontalAlignment="Left" Margin="10" FontSize="50" VerticalAlignment="Top" Height="75" Width="76" Click="OnClickOp" Background="#4294b4"/>

            <!-- the equal button to get the result -->
            <Button x:Name="equal" Content="=" HorizontalAlignment="Left" Margin="10" FontSize="50" VerticalAlignment="Top" Height="75" Width="76" Click="OnclickEqual" Background="#4294b4"/>

        </StackPanel>
    </Grid>

```

{{%/expand%}}

### Exercice 5 : Dessin

{{% exercice %}}
Dans un canvas, tentez de dessiner, avec tous les contrôles que vous voulez, le cybertruck de Tesla.
{{% /exercice %}}