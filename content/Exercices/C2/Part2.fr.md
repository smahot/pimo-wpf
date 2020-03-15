+++
title = "Les évènements - Exercices"
weight = 202
pre = "<b>2.2 </b>"
+++

## 2.2 Les évènements <!-- omit in toc -->

- [Exercice 1 : Simulation Clavier](#exercice-1--simulation-clavier)
- [Exercice 2 : Mini calculateur](#exercice-2--mini-calculateur)
- [Exercice 3 : Questionnaire](#exercice-3--questionnaire)
- [Exercice 4 : Application d’événements sur des boutons](#exercice-4--application-d%c3%a9v%c3%a9nements-sur-des-boutons)
- [Exercice 5 : Ouvrir une autre page xaml avec un bouton](#exercice-5--ouvrir-une-autre-page-xaml-avec-un-bouton)

### Exercice 1 : Simulation Clavier

{{% exercice "Question" %}}
Représentez une partie de votre clavier à l’aide de boutons. Par exemple (les touches azerty, les flèches de votre clavier ou le pavé numérique).  
Ces boutons auront un Background gris et une taille de police égale à 24. 
{{% /exercice %}}

![ex1 image1](/img/2.2/exos/ex1_img1.png?height=200px)

{{% expand "Correction partielle" %}}
    <Button x:Name="un" Content="1" HorizontalAlignment="Left" Margin="258,219,0,0" VerticalAlignment="Top" Width="45" Height="45" FontSize="24" Background="Gray"/>
{{% /expand %}}


{{% exercice "Question" %}}
Faites en sorte que ces touches changent de couleur lorsque vous appuyez dessus.
{{% /exercice %}}

{{% expand "Correction partielle" %}}
```csharp
private void Window_KeyDown(object sender, KeyEventArgs e) 
{
    switch (e.Key.ToString()) 
    { 
        case "NumPad1": 
            un.Background = Brushes.Blue; 
            break; 
    } 
}
private void Window_KeyUp(object sender, KeyEventArgs e) 
{ 
    switch (e.Key.ToString()) 
    { 
        case "NumPad1": 
            un.Background = Brushes.Gray; 
            break; 
    } 
}
```
{{% /expand %}}

### Exercice 2 : Mini calculateur 

{{% exercice "Question" %}}
Créez une interface comme celle-ci dessous avec 3 textBlocks, 2 textBox et un bouton. 
{{% /exercice %}}

![ex2 image1](/img/2.2/exos/ex2_img1.png?height=300px)

{{% expand "Correction" %}}
```xml
<Grid>
    <TextBlock HorizontalAlignment="Left" Margin="149,128,0,0" TextWrapping="Wrap" Text="Chiffre 1" VerticalAlignment="Top" Height="38" Width="178" Foreground="black" FontSize="22" TextAlignment="Center" Background="white"/>

    <TextBox x:Name="chiffre_un" HorizontalAlignment="Left" Height="23" Margin="182,171,0,0" TextWrapping="Wrap"  VerticalAlignment="Top" Width="120"/> 

    <TextBlock HorizontalAlignment="Left" Margin="452,128,0,0" TextWrapping="Wrap" Text="Chiffre 2" VerticalAlignment="Top" Height="38" Width="178" Foreground="black" FontSize="22" TextAlignment="Center" Background="white"/> 

    <TextBox x:Name="chiffre_deux" HorizontalAlignment="Left" Height="23" Margin="481,171,0,0" TextWrapping="Wrap"  VerticalAlignment="Top" Width="120"/> 

    <Button x:Name="button" Content="Multiplication" HorizontalAlignment="Left" Margin="318,225,0,0" VerticalAlignment="Top" Width="131" Height="48"/> 

    <TextBlock x:Name="resultat" HorizontalAlignment="Left" Margin="296,324,0,0" TextWrapping="Wrap" VerticalAlignment="Top" Height="38" Width="178" Foreground="black" FontSize="22" TextAlignment="Center" Background="white"/> 
</Grid>
```
{{% /expand %}}

{{% exercice "Question" %}}
Créez une interface comme celle-ci-dessous avec 3 textBlocks, 2 textBox et un bouton. 
{{% /exercice %}}

{{% expand "Correction" %}}
```csharp
private void Button_Click(object sender, RoutedEventArgs e) 
{ 
    double result = Convert.ToDouble(chiffre_un.Text) * Convert.ToDouble(chiffre_deux.Text); 
    resultat.Text = result.ToString(); 
} 
```
{{% /expand %}}

### Exercice 3 : Questionnaire

{{% exercice "Question" %}}
Créez une interface de type questionnaire.  
Ecrivez dans un textBlock une question.  
Placez ensuite un textbox qui permettra à l’utilisateur d’entrer une réponse.  
Placez un bouton pour soumettre sa réponse puis un rectangle qui sera Vert ou Rouge en fonction de la réponse attendue.  
{{% /exercice %}}

![ex3 image1](/img/2.2/exos/ex3_img1.png?height=200px)
![ex3 image2](/img/2.2/exos/ex3_img2.png?height=200px)

{{% expand "Correction xaml" %}}
```xml
<Grid>
    <TextBlock x:Name="textBlock" HorizontalAlignment="Left" Margin="119,73,0,0" TextWrapping="Wrap" Text="Quel est le nom de domaine dans 'https://www.github.com' ?" VerticalAlignment="Top" Height="29" Width="603" FontSize="22"/> 

    <TextBox x:Name="answer" HorizontalAlignment="Left" Height="23" Margin="258,166,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="291"/> 

    <Button x:Name="button" Content="Check answer" HorizontalAlignment="Left" Margin="258,245,0,0" VerticalAlignment="Top" Width="100" Height="34" Click="Button_Click"/> 

    <Rectangle x:Name="check" Fill="#FFF4F4F5" HorizontalAlignment="Left" Height="34" Margin="449,245,0,0" Stroke="Black" VerticalAlignment="Top" Width="100"/> 
</Grid> 
```
{{% /expand %}}

{{% expand "Correction C#" %}}
```csharp
private void Button_Click(object sender, RoutedEventArgs e) 
{
    if(answer.Text.Equals("github.com")) //answer is the textBox 
    {
        check.Fill = Brushes.Green; //check is the name of the rectangle 
    }
    else 
    {
        check.Fill = Brushes.Red;
    }
}
```
{{% /expand %}}
### Exercice 4 : Application d’événements sur des boutons

{{% exercice "Question" %}}
Placer deux boutons avec un Background gris comme ci-dessous.
{{% /exercice %}}

![ex4 image1](/img/2.2/exos/ex4_img1.png?height=300px)

{{% exercice "Question" %}}
Lorsque la souris passe par-dessus un bouton, la couleur de l’autre bouton change puis revient à la normale lorsque le curseur n’est plus sur le premier bouton.
{{% /exercice %}}

{{% expand "Correction C#" %}}
```csharp
private void Button1_MouseEnter(object sender, MouseEventArgs e) 
{ 
    Button2.Background = Brushes.Red; 
} 

private void Button1_MouseLeave(object sender, MouseEventArgs e) 
{ 
    Button2.Background = Brushes.Gray; 
} 
```
{{% /expand %}}

{{% exercice "Question 3" %}}
Lorsque la souris est sur le bouton numéro2 et que la molette de votre souris est activée, cela doit entrainer un changement de la taille du bouton (augmentation si molette vers le bas et diminution si molette vers le haut).
{{% /exercice %}}

{{% expand "Correction" %}}
```csharp
private void Button2_MouseWheel(object sender, MouseWheelEventArgs e) 
{ 
    if (e.Delta > 0) 
    { 
        Button2.Width += 5; 
        Button2.Height += 5; 
    } 
    else if (e.Delta < 0) 
    {
        Button2.Width -= 5; 
        Button2.Height -= 5; 
    } 
} 
```
{{% /expand %}}

### Exercice 5 : Ouvrir une autre page xaml avec un bouton

{{% exercice "Question" %}}
Créer une page de renseignement (nom, prénom, âge …). Vous pouvez trouver un exemple ci-dessous.
{{% /exercice %}}

![ex5 image1](/img/2.2/exos/ex5_img1.png?height=300px)

{{% expand "Correction" %}}
```xml
<Grid>
    <Button x:Name="submit" Content="SUBMIT" HorizontalAlignment="Left" Margin="351,297,0,0" VerticalAlignment="Top" Width="128" Height="57" Click="Button_Click"/> 

    <TextBox x:Name="textPrenom" HorizontalAlignment="Left" Height="44" Margin="80,188,0,0" TextWrapping="Wrap" VerticalAlignment="Top" Width="267" Foreground="black" FontSize="26" TextAlignment="Left" Background="white"/> 

    <TextBlock HorizontalAlignment="Left" Margin="80,77,0,0" TextWrapping="Wrap" Text="PRENOM" VerticalAlignment="Top" Height="42" Width="267" Foreground="white" FontSize="32" TextAlignment="Center" Background="Black"/> 

    <TextBlock HorizontalAlignment="Left" Margin="477,77,0,0" TextWrapping="Wrap" Text="NOM" VerticalAlignment="Top" Height="42" Width="267" Foreground="white" FontSize="32" TextAlignment="Center" Background="Black"/> 

    <TextBox x:Name="textNom" HorizontalAlignment="Left" Height="44" Margin="477,188,0,0" TextWrapping="Wrap"  VerticalAlignment="Top" Width="267" Foreground="black" FontSize="26" TextAlignment="Left" Background="white"/> 
</Grid> 
```
{{% /expand %}}

{{% exercice "Question" %}}
Quand l'utilisateur clique sur le bouton, une nouvelle fenêtre apparait et affiche les informations renseignées
{{% /exercice %}}

![ex5 image2](/img/2.2/exos/ex5_img2.png?height=300px)
![ex5 image3](/img/2.2/exos/ex5_img3.png?height=300px)

> Pour insérer une deuxième fenêtre WPF : Projet, ajouter une fenêtre, fenêtre (WPF)

{{% expand "Correction xaml" %}}
```xml
<Grid> 

    <TextBlock x:Name="Prenom2" HorizontalAlignment="Left" Margin="0,83,-0.4,0" TextWrapping="Wrap" Text="PRENOM" VerticalAlignment="Top" Height="42" Width="794" Foreground="black" FontSize="32" TextAlignment="Center" Background="white"/> 

    <TextBlock HorizontalAlignment="Left" Margin="0,36,-0.4,0" TextWrapping="Wrap" Text="BIENVENUE" VerticalAlignment="Top" Height="42" Width="794" Foreground="black" FontSize="32" TextAlignment="Center" Background="white"/> 

    <TextBlock x:Name="Nom2" HorizontalAlignment="Left" Margin="0,130,-0.4,0" TextWrapping="Wrap" Text="NOM" VerticalAlignment="Top" Height="42" Width="794" Foreground="black" FontSize="32" TextAlignment="Center" Background="white"/> 

</Grid> 
```
{{% /expand %}}

{{% expand "Correction C#" %}}
```csharp
private void Button_Click(object sender, RoutedEventArgs e) 
{ 
    SecondePage deuxiemePage = new SecondePage(); //SecondePage est le nom de la 2e fenêtre 
    this.Visibility = Visibility.Hidden; 
    deuxiemePage.Prenom2.Text = textPrenom.Text; //Prenom2 est un textBlock sur la 2e fenêtre 
                                                //textPrenom est la textBox où le prénom est entré 
    deuxiemePage.Nom2.Text = textNom.Text; 
    deuxiemePage.Show(); 
} 
```
{{% /expand %}}