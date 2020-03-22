+++
title = "Les premiers contrôles - Exercices"
weight = 201
pre = "<b>2.1 </b>"
+++

## 2.1 Les premiers contrôles <!-- omit in toc -->

- [Exercice 1](#exercice-1)
- [Exercice 2](#exercice-2)
- [Exercice 3](#exercice-3)
- [Exercice 4](#exercice-4)
- [Exercice 5](#exercice-5)
- [Exercice 6](#exercice-6)
- [Exercice 7](#exercice-7)

### Exercice 1

{{% exercice %}}
Créez 4 boutons, chacun dans un angle, avec une couleur de police différent à chaque fois.
{{% /exercice %}}
![image1](/img/2.1/exos/im1.png?height=300px)

{{% expand "Correction" %}}

```xml
<Grid>
        <Button Content="Up left" VerticalAlignment="Top" HorizontalAlignment="Left" Margin="0" Foreground="Red"/>
        <!-- Le bouton en haut à gauche-->
        <!-- Pour placer un bouton dans le coin en haut à gauche, on place le point de référence en haut à gauche avec verticalAlignement="top" 
        et horizontalAlignement= "left", puis pour qu'il reste bien dans le coin, on met une marge de 0 -->
        <!-- Pour la couleur, comme on ne veut que le texte coloré, il faut utiliser Foreground="la couleur souhaitée"-->

        <Button Content="Down left" VerticalAlignment="Bottom" HorizontalAlignment="Left" Margin="0" Foreground="Blue"/>
        <!-- Le bouton en bas à gauche-->
        <!-- Cette fois, il faut utiliser les arguments bottom et left, toujours avec une marge de 0-->

        <Button Content="Up right" VerticalAlignment="Top" HorizontalAlignment="Right" Margin="0" Foreground="Green"/>
        <!-- Le bouton en haut à droite-->
        <!-- Cette fois, il faut utiliser les arguments top et right, toujours avec une marge de 0-->

        <Button Content="Bottom Right" VerticalAlignment="Bottom" HorizontalAlignment="Right" Margin="0" Foreground="Purple"/>
        <!-- Le bouton en bas à droite-->
<!-- Cette fois, il faut utiliser les arguments bottom et right, toujours avec une marge de 0-->
</Grid>
```

{{%/expand%}}

### Exercice 2

{{% exercice %}}
Placez 4 boutons de 40*40 au centre, sans qu’ils ne superposent. Jouez sur les marges pour obtenir le résultat.
{{% /exercice %}}
![image2](/img/2.1/exos/im2.png?height=300px)

{{% expand "Correction" %}}

```xml
<Grid>
        <!-- Dans cet exercice, tous les boutons auront HorizontalAlignement et VerticalAlignement sur "center" : l'énoncé demande qu'ils soient centrés-->
        <!-- Mais ils ne doivent pas se superposer. C'est pour cela que l'ont utilise les Margins pour les 'déplacer' -->
        <!-- Il faut alors définir les marges de la sorte : Margin="W,X,Y,Z" avec W : marge à gauche, X : marge en haut, Y : marge à droite, Z : marge en bas-->
        <!-- Logiquement, si l'on veut déplacer un élément dans une direction, il faut jouer sur la marge de l'autre sens. 
        Exemple : déplacer un objet vers le haut va me demander d'augmenter la marge du bas-->
        <!-- Les boutons font du 40 par 40. La marge ne prend pas par rapport au centre, mais par rapport au bord inverse : il faudra donc des marges de 40px-->

        <Button Content="UpLe" Margin="0,0,40,40" HorizontalAlignment="Center" VerticalAlignment="Center" Height="40" Width="40"/>
        <!-- Le bouton en haut à gauche-->
        <!-- On veut monter et décaler le bouton à gauche, on joue donc sur les marges du bas et à droite-->

        <Button Content="UpRi" Margin="40,0,0,40" HorizontalAlignment="Center" VerticalAlignment="Center" Height="40" Width="40"/>
        <!-- Le bouton en haut à droite-->
        <!-- On veut monter et décaler le bouton à droite, on joue donc sur les marges du bas et à gauche-->

        <Button Content="DoLe" Margin="0,40,40,0" HorizontalAlignment="Center" VerticalAlignment="Center" Height="40" Width="40"/>
        <!-- Le bouton en bas à gauche-->
        <!-- On veut descendre et décaler le bouton à gauche, on joue donc sur les marges du haut et à droite-->

        <Button Content="DoRi" Margin="40,40,0,0" HorizontalAlignment="Center" VerticalAlignment="Center" Height="40" Width="40"/>
        <!-- Le bouton en bas à droite-->
        <!-- On veut descendre et décaler le bouton à droite, on joue donc sur les marges du haut et à gauche-->

        <!-- A noter que les solutions pour cet exercice sont illimités : le point de repère de chaque bouton peut être différent, et donc les marges aussi,
        on peut réutiliser un unique point de repère, mais ailleurs... Je présente cette méthode avec le repère au centre car c'est plus simple à comprendre-->

</Grid>
```

{{%/expand%}}

### Exercice 3

{{% exercice %}}
Alignez 4 boutons de 40*40 sur une ligne horizontale au centre de la fenêtre.
{{% /exercice %}}
![image3](/img/2.1/exos/im3.png?height=300px)

{{% expand "Correction" %}}

```xml
<Grid>  
        <!-- On place tous les boutons sur le même verticalAlignement="center" puisque l'on veut les aligner. Par défaut, HorizontalAlignement est sur center-->
        <!-- Les boutons sont créés de gauche à droite (B1 à gauche, B4 à droite)-->
        <!-- Les marges sont additives, d'où le fait que l'on ajoute 80 px de distance plutôt que 40 -->
        <Button Content="B1" Height="40" Width="40" VerticalAlignment="Center" Margin="0,0,120,0"/>

        <Button Content="B2" Height="40" Width="40" VerticalAlignment="Center" Margin="0,0,40,0"/>

        <Button Content="B3" Height="40" Width="40" VerticalAlignment="Center" Margin="40,0,0,0"/>

        <Button Content="B4" Height="40" Width="40" VerticalAlignment="Center" Margin="120,0,0,0"/>

        <Button Content="B5" Height="40" Width="40" VerticalAlignment="Center" Margin="200,0,0,0" Foreground="Red"/>
        <!-- Bouton supplémentaire pour démontrer l'utilisation des marges plus loin. Ici, on rajoute encore 80px, 
        et pas 120px comme les deux premiers boutons à droite pourraient le laisser comprendre-->
</Grid>
```

{{%/expand%}}

### Exercice 4

{{% exercice %}}
Créez deux TextBlocks centrés dans la fenêtre avec un texte dans chacun qui revient à la ligne.
{{% /exercice %}}
![image4](/img/2.1/exos/im4.png?height=300px)

{{% expand "Correction" %}}

```xml
<Grid>
        <!-- On va créer deux TextBlock-->
        <!-- Les placements se font avec HorizontalAlignement (soit à right, soit à left)-->
        <!-- Pour que le texte de Text="" aille à la ligne, il faut utiliser TextWwrapping="Wrap" -->
        <!-- Cependant, si vous voulez utiliser tout l'espace, le reflexe logique serait de mettre Height="300" et Width="200"... Mais en faisant ça, vous verrez déjà que les TextBlock se superposent au milieux, et débordent vers le bas-->
        <!-- En fait, la fenêtre que vous définissez avec 300 sur 400 possède déjà une marge de 25px en haut, et 5px sur les autres bords, il faut donc prendre cela en compte en créant des textblocks de 270 (300 - 25 - 5) sur 195 (400/2 - 5) -->
        <TextBlock Text="Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat." TextWrapping="Wrap" Height="270" Width="195" HorizontalAlignment="Left"/>

        <TextBlock Text="Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum." TextWrapping="Wrap" Height="270" Width="195" HorizontalAlignment="Right"/>
</Grid>
```

{{%/expand%}}

### Exercice 5

{{% exercice %}}
Créez 1 TextBox qui prend la moitié gauche de la fenêtre. Placez un bouton de 50*50 au centre de l’autre moitié de fenêtre.
{{% /exercice %}}
![image5](/img/2.1/exos/im5.png?height=300px)

{{% expand "Correction" %}}

```xml
<Grid>
        <!-- Similaire à l'exercice précédent, la textbox a les dimensions suivantes : 270*195 -->
        <TextBox Height="270" Width="195" HorizontalAlignment="Left" Text="hello" VerticalContentAlignment="Center" HorizontalContentAlignment="Center"/>
        <Button Content="Center" Height="50" Width="50" HorizontalAlignment="Center" Margin="200,0,0,0"/>
</Grid>
```

{{%/expand%}}

### Exercice 6

{{% exercice %}}
Créez un CheckBox dans le coin en haut à droite avec le texte en bleu et avec trois états.
{{% /exercice %}}
![image6](/img/2.1/exos/im6.png?height=300px)

{{% expand "Correction" %}}

```xml
<Grid>
        <CheckBox Content="CheckBox" VerticalAlignment="Top" HorizontalAlignment="Left" IsThreeState="True"/>
</Grid>
```

{{%/expand%}}

### Exercice 7

{{% exercice %}}
Créez une ListBox contenant le nom d’au moins 7 musiques. Vous donnerez un gradient de couleur pour signifier votre ordre de préférence, en utilisant les couleurs en hexadécimale.
{{% /exercice %}}
![image7](/img/2.1/exos/im7.png?height=300px)

{{% expand "Correction" %}}

```xml
</Grid>
    <ListBox HorizontalAlignment="Center" Height="100">
        <ListBoxItem Content="Danse macabre" Foreground="#0f2d7e" FontSize="15" FontWeight="Bold"/>
        <ListBoxItem Content="Printemp" Foreground="#2147ae" FontSize="15" FontWeight="Bold"/>
        <ListBoxItem Content="You'd judged me" Foreground="#3959b0" FontSize="15" FontWeight="Bold"/>
        <ListBoxItem Content="Random classic" Foreground="#566fb2" FontSize="15" FontWeight="Bold"/>
        <ListBoxItem Content="No idea" Foreground="#6f81b0" FontSize="15" FontWeight="Bold"/>
        <ListBoxItem Content="Beat it" Foreground="#8a95b4" FontSize="15" FontWeight="Bold"/>
        <ListBoxItem Content="DP road 216" Foreground="#b6bed2" FontSize="15" FontWeight="Bold"/>
    </ListBox>
</Grid>
```

{{%/expand%}}
