+++
title = "Quizz Chapitre 3"
weight = 3003
pre = "<b>3.3 </b>"
+++

{{% exercice "Quizz" %}}
**Question 1 :** Si vous déclarez un Stack Panel sans rien préciser de plus, la disposition des éléments sera :
{{% /exercice %}}

a)	Verticale    
b)	Horizontale  
c)	On ne peut pas ne pas spécifier la disposition  
d)  Le Stack Panel ne permet qu’une unique disposition

{{% expand "solution" %}}
**Réponse :** a) D’après le cours, par défaut le stack panel dispose les éléments de façon verticale.
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 2 :** Quelle propriété permet de choisir l’épaisseur des bords d’une figure ?
{{% /exercice %}}

a)	Fill    
b)	Border    
c)	Margin   
d)  StrokeThickness  

{{% expand "solution" %}}
**Réponse :** d) Fill permet de remplir une figure, un rectangle par exemple, Margin permet de déterminer l’espace laissé vide autour d’un élément, la bonne réponse est donc StrokeThickness
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 3 :** Quel Panel permet de choisir la place d’un élément en explicitant ses coordonnées ?
{{% /exercice %}}

a)	Wrap Panel   
b)	Canvas     
c)	Dock Panel   
d)  La réponse d

{{% expand "solution" %}}
**Réponse :** c) La bonne réponse est le Dock Panel qui permet cette affectation de l’emplacement des éléments par des coordonnées grâce à la propriété DockPanel.Dock
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 4 :** Peut-on imbriquer plusieurs Panel les uns dans les autres ?
{{% /exercice %}}

a) Oui  

b) Non

{{% expand "solution" %}}
**Réponse :** a) Oui, c’est possible.
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 5 :** Quelle propriété permet de vérifier que le dernier élément d’un Dock Panel rempliera tout l’espace restant ?
{{% /exercice %}}

a) FillAll  
b) RemainingSpaceFill  
c) FillEverywhere  
d) LastChildFill

{{% expand "solution" %}}
**Réponse :** d)
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 6 :** Comment puis-je modifier comment s’organise les éléments du Wrap Panel ?
{{% /exercice %}}

a) VerticalAlignment = “Top”  
b) Orientation = “Horizontal”  
c) HorizontalAlignmant= “Top”  
d) Orientation = “Vertictal”

{{% expand "solution" %}}
**Réponse :** d) Par défaut, le Wrap Panel a ses éléments disposés de façon horizontale, ce n’est donc pas Orientation = « Horizontal ». Les propriétés VerticalAlignment et HorizontalAlignment permettent de choisir où sera placé l’élément dans notre fenêtre. C’est donc Orientation= « Vertical »
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 8 :** On peut déclarer une colonne de la façon suivante : ```<ColumnDefinition Height="auto"/>```
{{% /exercice %}}

a) Vrai

b) Faux

{{% expand "solution" %}}
**Réponse :** b) Faux, une colonne n’a qu’une propriété Width, et pas une propriété Height
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 9 :** Quel code permet d’obtenir cette figure : 
![imageQ3](/img/3.1/imQuizz1.png?height=300px)
{{% /exercice %}}

a)
```
<Canvas>
        <Ellipse Height="50" Width="50" Fill="AliceBlue" Panel.ZIndex="3"/>
        <Ellipse Height="100" Width="100" Fill="Purple" Panel.ZIndex="2"/>
        <Ellipse Height="150" Width="150" Fill="Black" Panel.ZIndex="1"/>
        <Line X1="0" Y1="0" X2="150" Y2="150" Stroke="Yellow" Panel.ZIndex="4"/>
</Canvas>
```

b)
```
<Canvas>
        <Ellipse Height="50" Width="50" Background="AliceBlue" Panel.ZIndex="2"/>
        <Ellipse Height="100" Width="100" Background="Purple" Panel.ZIndex="3"/>
        <Ellipse Height="150" Width="150" Background="Black" Panel.ZIndex="4"/>
        <Line X1="0" Y1="0" X2="150" Y2="150" Stroke="Yellow" Panel.ZIndex="1"/>
</Canvas>
```  

c)
```
<Canvas>
        <Ellipse Height="50" Width="50" Fill="AliceBlue" Panel.ZIndex="2"/>
        <Ellipse Height="100" Width="100" Fill="Purple" Panel.ZIndex="3"/>
        <Ellipse Height="150" Width="150" Fill="Black" Panel.ZIndex="4"/>
        <Line X1="0" Y1="0" X2="150" Y2="150" Stroke="Yellow" Panel.ZIndex="1"/>
</Canvas>
 ```  
    
d)
```
<Canvas>
        <Ellipse Height="50" Width="50" Background="AliceBlue" Panel.ZIndex="3"/>
        <Ellipse Height="100" Width="100" Background="Purple" Panel.ZIndex="2"/>
        <Ellipse Height="150" Width="150" Background="Black" Panel.ZIndex="1"/>
        <Line X1="0" Y1="0" X2="150" Y2="150" Stroke="Yellow" Panel.ZIndex="4"/>
</Canvas> 
```


{{% expand "solution" %}}
**Réponse :** a) Pour remplir une figure, on n’utilise pas la propriété Background, ce n’est donc pas la b) ni la d). Enfin, on rappelle que si deux éléments se chevauchent, grâce à la propriété ZIndex, c’est l’élément avec le Zindex le plus élevé qui sera affiché. La bonne réponse est donc a)
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 10 :** Quel code permet d’obtenir cette figure :   
![imageQ31](/img/3.1/imQuizz2.png?height=300px)
{{% /exercice %}}


a) 
```
<Grid>  
        <ColumnDefinitions>  
            <ColumnDefinition Width="*"/>
            <ColumnDefinition Width="2*"/>
            <ColumnDefinition Width="*"/>
        <ColumnDefinitions>
        <RowDefinitions>
            <RowDefinition Height="*"/>
            <RowDefinition Height="*"/>
            <RowDefinition Height="2*"/>
            <RowDefinition Height="*"/>
        </RowDefinitions>
        <Button Content="Bouton"/>
        <Button Content="Bouton" Grid.Row="1" Grid.Column="1" Grid.RowSpan="2"/>
        <Button Content="Bouton" Grid.Row="3" Grid.ColumnSpan="3"/>
</Grid>
```  

b)
```
<Grid>  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="*"/>  
            <ColumnDefinition Width="2*"/>  
            <ColumnDefinition Width="*"/>  
        </Grid.ColumnDefinitions>  
        <Grid.RowDefinitions>  
            <RowDefinition Height="*"/>  
            <RowDefinition Height="*"/>  
            <RowDefinition Height="2*"/>  
            <RowDefinition Height="*"/>  
        </Grid.RowDefinitions>
        <Button Content="Bouton"/>
        <Button Content="Bouton" Grid.Row="1" Grid.Column="1" Grid.RowSpan="2"/>
        <Button Content="Bouton" Grid.Row="3" Grid.ColumnSpan="3"/>
</Grid>
```  

c)
```
<Grid>
        <ColumnDefinitions>
            <ColumnDefinition Width="*"/>
            <ColumnDefinition Width="2*"/>
            <ColumnDefinition Width="*"/>
        </ColumnDefinitions>
        <RowDefinitions>
            <RowDefinition Height="*"/>
            <RowDefinition Height="*"/>
            <RowDefinition Height="2*"/>
            <RowDefinition Height="*"/>
        </RowDefinitions>
        <Button Content="Bouton"/>
        <Button Content="Bouton" Row="1" Column="1" RowSpan="2"/>
        <Button Content="Bouton" Row="3" ColumnSpan="3"/>
</Grid>
```    
    
d)
```
<Grid>
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="*"/>
            <ColumnDefinition Width="2*"/>
            <ColumnDefinition Width="*"/>
        </Grid.ColumnDefinitions>
        <Grid.RowDefinitions>
            <RowDefinition Height="*"/>
            <RowDefinition Height="*"/>
            <RowDefinition Height="2*"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
        <Button Content="Bouton"/>
        <Button Content="Bouton" Row="1" Column="1" RowSpan="2"/>
        <Button Content="Bouton" Row="3" ColumnSpan="3"/>
</Grid> 
```  


{{% expand "solution" %}}
**Réponse :** b) Les colonnes se définissent à l’intérieur de la balise Grid.ColumnsDefinition et non seulement ColumnsDefinition (respectivement Grid.RowsDefinition). Ce n’est donc pas a) ni c). Enfin, pour affecter une colonne, une ligne à un éléments, et éventuellement l’étendre il faut utiliser les propriétés Grid.Column (respectivement Grid.Row), et Grid.ColumnSpan (respectivement Grid.RowSpan). La bonne réponse est donc la b).
{{%/expand%}}

---