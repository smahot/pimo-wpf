+++
title = "Les premiers contrôles"
weight = 2001
pre = "<b>2.1 </b>"
+++

### A. Les premiers contrôles

#### a. Création d’un bouton

Nous allons commencer par lancer un projet WPF app sur Visual Studio 2017/2019. Pour ce faire, utilisez soit le raccourci _Ctrl+Shift+n_, soit _File_ => _New…_ => _Project…_ Cela ouvre la fenêtre suivante :

![image1](/img/2.1/im1.png?height=400px)

> 1. Sélectionnez Visual C#, le langage de WPF 
> 2. Pas d’application console, mais bien une application WPF  
> 3. Le nom du projet et son adresse 
> 4. Pour l’instant, faites OK pour valider la création. 

Allons maintenant dans le fichier xaml créé. A votre gauche, vous devriez avoir une toolbox avec de nombreux outils dedans. Drag’n’dropez un bouton dans la fenêtre blanche. Cela va créer une ligne dans le fichier xaml qui devrait ressembler à ça : 

```xml
<Button Content="Button" HorizontalAlignment="Left" Margin="335,177,0,0" VerticalAlignment="Top" Width="75"/> 
```

![image2](/img/2.1/im2.png?height=300px)

Comme vous pouvez le voir, nous venons de créer une instance de la classe bouton. Les strings en rouge sont les attributs définis lors de la création du bouton, le tout dans une balise pour respecter le langage XAML. Nous allons parler de chaque attribut, et comment agir dessus. Veuillez donc vous assurer que vous avez bien créé ce bouton, pour changer les valeurs pour voir les effets.

 - **Les attributs affectant la forme du bouton :**

**Content** : Ce qu’il y a marqué dans la case du bouton. Ne prend que des *chars* ou *string*.

{{% exercice %}}
Pour essayer, remplacez ‘’Button’’ par ‘’hello !’’ – le texte du bouton change dans la fenêtre !
{{% /exercice %}}

{{% expand "Correction" %}}
    <Button Content="Hello !" HorizontalAlignment="Center" VerticalAlignment="Center" Width="100" Height="100"/> 
{{%/expand%}}

---

**Width & Height** : respectivement la largeur et la hauteur du bouton (ainsi que les autres contrôles possédant ces attributs). L’unité de longueur est le pixel.

{{% exercice %}}
Changez les valeurs de ces deux atributs : par exemple, mettez 200 et 200 – le bouton prend une plus grande place dans la fenêtre. 
{{% /exercice %}}

{{% expand "Correction" %}}
    <Button Content="Hello !" HorizontalAlignment="Center" VerticalAlignment="Center" Width="200" Height="200"/>
{{%/expand%}}

---

 - **Les attributs affectant la position du bouton dans la fenêtre :**

Tout d’abord, si l’on omet les layouts, les éléments sont placés dans la fenêtre grâce à 3 attributs : Margin, HorizontalAlignement et VerticalAlignement. Considérez que chaque contrôle est placé dans la fenêtre par rapport à un point absolu, un 0,0 que vous définissez, puis donc vous donnez les coordonnées avec Margin.

**HorizontalAlignement** défini l’abscisse de ce point absolu. ‘’left’’ signifie que l’origine se place à gauche, ‘’center’’ au centre et ‘’right’’ à droite (exemple : une fenêtre de 100px de largeur – left signifierai 0px, center 50px et right 100px).

**VerticalAlignement** : pareil que *HorizontalAlignement*, mais pour les ordonnées. Les valeurs sont cette fois ci ‘’Top’’, ‘’Center’’ et ‘’Bottom’’. 

{{% exercice %}}
Pour cet exemple, mettez la valeur de Margin à 0, et testez différentes configurations : ‘’left’’ ‘’center’’, ‘’right’’ ‘’bottom’’… etc – Le bouton va bouger à travers la fenêtre. 
{{% /exercice %}}

{{% expand "Correction" %}}
    <Button Content="Hello ! (1)" HorizontalAlignment="Right" VerticalAlignment="Bottom" Width="100" Height="100"/>
    <Button Content="Hello ! (2)" HorizontalAlignment="Left" VerticalAlignment="Bottom" Width="100" Height="100"/>
    <Button Content="Hello ! (3)" HorizontalAlignment="center" VerticalAlignment="Top" Width="100" Height="100"/> 
{{%/expand%}}

---

**Margin** : donne les coordonnées par rapport à ce point absolu. Il donne la ‘’marge’’, c’est-à-dire la distance en pixel du contrôle par rapport au point d’origine quand il n’est pas dans un layouts (que vous verrez plus tard). Les 4 marges sont définies, ainsi ‘’10,5,0,15’’ signifie une marge à gauche de 10px, une marge en haut de 5px, une marge à droite de 0px et une marge en bas de 15px. Il existe deux manières de définir la marge : soit en ne déclarant juste un nombre (exemple : Margin=’’10’’) où chaque marge fera donc 10px, ou en déclarant les 4 marges séparément.

{{% exercice %}}
Placez d’autres boutons à différents endroits et faites varier les marges pour en voir les différents effets. 
{{% /exercice %}}

{{% expand "Correction" %}}
    <Button Content="Test TL" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="30,20,0,0" Width="50" Height="50"/>
    <Button Content="Test TR" HorizontalAlignment="Right" VerticalAlignment="Top" Margin="0,30,20,0" Width="50" Height="50"/>
    <Button Content="Test BR" HorizontalAlignment="Right" VerticalAlignment="Bottom" Margin="0,0,30,20" Width="50" Height="50"/>
    <Button Content="Test BL" HorizontalAlignment="Left" VerticalAlignment="Bottom" Margin="20,0,0,20" Width="50" Height="50"/>
    <Button Content="Test" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="150,300,0,0" Width="50" Height="50"/> 
{{%/expand%}}

---

A noter que vous verrez dans le chapitre suivant une meilleure façon placer les éléments de la fenêtre avec les layouts. 

 - **D’autres attributs que vous pouvez rajouter :**

*FontSize* : la taille de la police du texte  
*FontStyle* : le style du texte (italique, oblique…)  
*FontWeight* : l’épaisseur du texte (l’IDE propose plusieurs épaisseurs prédéterminées comme black, bold…)  
*Foreground* : la couleur de la police  
*BorderBrush* : la couleur des bords  
*BorderThickness* : l’épaisseur de la bordure  

![image3](/img/2.1/im3.png?height=300px)

{{% exercice %}}
Essayez d’utiliser tous ces attributs sur plusieurs boutons pour découvrir les différents effets en direct. 
{{% /exercice %}}

{{% expand "Correction" %}}
    <Button Content="Size" HorizontalAlignment="Center" VerticalAlignment="Center" Height="100" Width="100" FontSize="30" FontStyle="Italic" FontWeight="Bold" Foreground="Red" BorderBrush="Red" BorderThickness="20" /> 
{{%/expand%}}

---

#### b. Les autres contrôles :

Tout d’abord, n’oubliez pas que les attributs présentés dans la parties précédents (Width, Margin, FontSize…) sont hérités. Ils ne sont pas réservés à seulement les boutons. Ils peuvent donc être utilisés pour les autres contrôles. Pas besoin de tous les re-lister donc pour chaque autre contrôle. 

Le **TextBlock** : un « boîte » qui contient du texte. Elle sert principalement à indiquer ou à expliquer sur une application, mais elle peut aussi servir d’affichage pour des variables. Par exemple, vous pourriez utiliser une Textblock pour afficher le résultat d’une calculatrice que vous venez de créer.  
Son attribut principal est le Text, c’est-à-dire ce qui va être affiché.

![image4](/img/2.1/im4.png?height=300px)

```xml
<TextBox HorizontalAlignment="Left" Height="23" Margin="521,142,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="120"/> 
```

Les attributs que l’on utilise aussi ici sont :  
*Text* : ce qui va s’afficher dans la textbox.  
*TextWrapping* : Si le texte est trop grand, retourne à la ligne. Pour cet effet, précisez ‘’wrap’’  
*LineHeight* : Donne la hauteur de chaque ligne.  

![image5](/img/2.1/im5.png?height=300px)

{{% exercice %}}
En exemple, créez un TextBlock avec une phrase assez longue dedans, qui revient à la ligne, au centre de la fenêtre. Le texte doit être en bleu. Choisissez la taille de police de votre choix. 
{{% /exercice %}}

{{% expand "Correction" %}}
    <TextBlock HorizontalAlignment="Center" Margin="0" TextWrapping="Wrap" Text="Hello from the wasteland of broken programmer's dream" VerticalAlignment="Center" Width="200" Foreground="Blue" FontSize="20"/> 
{{%/expand%}}

---

Le **TextBox** : Très ressemblant à une *TextBlock*, il offre la possibilité à l’utilisateur de taper du texte dedans en plus.  

![image6](/img/2.1/im6.png?height=300px)

```xml
<TextBox HorizontalAlignment="Center" Margin="0" TextWrapping="Wrap" Text="Hello from the wasteland of broken programmer's dream" VerticalAlignment="Center" Width="200" Foreground="Blue" FontSize="20"/> 
```

Remarquez que cette fois ci, vous pouvez cliquer sur la fenêtre et écrire dedans. Il y a de nombreux moyens de « sauver » ce texte, mais vous le verrez plus tard. 

---

Le **CheckBox** : Une case avec sa description. Vous pouvez cocher cette case 2 à 3 fois en fonction des paramètres que vous définissez. 

![image7](/img/2.1/im7.png?height=300px)

```xml
<CheckBox Content="CheckBox" HorizontalAlignment="Left" Margin="150,127,0,0" VerticalAlignment="Top"/> 
```

---

**IsThreeState** : Prend un boulean (en string, soit ‘’True’’ par exemple). Il détermine s’il existe un troisième état lorsque l’on décoche/coche le CheckBox.

![image8](/img/2.1/im8.png?height=300px)

{{% exercice %}}
En nouvel exemple, créez deux checkbox, horizontalement centrées, qui ne se superposent pas, et dont l’une possède trois états et est en rouge.
{{% /exercice %}}

{{% expand "Correction" %}}
    <CheckBox Content="CheckBox" HorizontalAlignment="Center" VerticalAlignment="Top" Margin="0,50" Height="30" />
    <CheckBox Content="CheckBox2" HorizontalAlignment="Center"  VerticalAlignment="Top" Margin="0,100" Height="30" Foreground="Red" IsThreeState="True" /> 
{{%/expand%}}

---

Le ***ListBox*** : il s’agit d’un menu défilant dans lequel vous pouvez sélectionner une option. Il vous faut précisez dans le listBox les éléments le composant. 

```xml
<ListBox Name = "listbox" HorizontalAlignment="Center" VerticalAlignment="Center" Margin = "20,0,0,0" Width = "100" Height="30">
    <ListBoxItem Content = "java"/> 
    <ListBoxItem Content = "C++"/> 
    <ListBoxItem Content = "Python"/> 
    <ListBoxItem Content = "SciLab"/> 
    <ListBoxItem Content="VisualBasic"/> 
</ListBox>
```

![image9](/img/2.1/im9.png?height=300px)

Pour rajouter un élément à la liste, on crée une balise dans le ListBox qui s’appelle ListBoxItem qui agit comme un TextBlock., c’est-à-dire que vous pouvez leur ajouter des attributs (couleur, taille…) comme vous voulez.

{{% exercice %}}
Créez un Listbox contenant au moins 4 choix avec chacun une couleur différente.
{{% /exercice %}}

{{% expand "Correction" %}}
```xml
<ListBox Name = "listbox"  HorizontalAlignment="Center" VerticalAlignment="Center" Margin = "20,0,0,0" Width = "100" Height="60">
    <ListBoxItem Content = "java" Foreground="Green"/> 
    <ListBoxItem Content = "C++" Foreground="Blue"/> 
    <ListBoxItem Content = "Python" Foreground="Red"/> 
    <ListBoxItem Content = "SciLab" Foreground="Yellow"/> 
    <ListBoxItem Content="VisualBasic" Foreground="Purple"/>
</ListBox> 
```
{{%/expand%}}

--- 
---

{{% button href="/fr/exercices/c2/part1/" %}}Lien vers les exercices{{% /button %}}