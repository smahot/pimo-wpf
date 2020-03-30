+++
title = "Quizz Chapitre 4"
weight = 4003
pre = "<b>4.2 </b>"
+++

{{% exercice "Quizz" %}}
**Question 1 :** Quels sont les différents types de binding ?
{{% /exercice %}}

a)	-	OneWay, TwoWay, OneWayReverse, OneTime   
b)	-	OneWay, TwoWay, OneWayToSource, OneTime  
c)	-	OneWay, TwoWay, OneWayReverse, OnlyOnce    
d)	-	OneWay, TwoWay, OneWayToSource, OnlyOnce


{{% expand "solution" %}}
**Réponse :** b)
{{%/expand%}}

---


{{% exercice "Quizz" %}}
**Question 2 :** Quelle est la bonne manière de déclarer un binding d’une textbox à la propriété Title ?
{{% /exercice %}}

a)	```<TextBox Text={Binding Path=Title}></TextBox>  ```  
b)	```<TextBox Text= Binding(this, Title)></TextBox>  ```  
c)	```<TextBox Text=Binding(Title)></TextBox> ```   
d)	```<TextBox Text="{Binding Path=Title}"></TextBox>    ```  


{{% expand "solution" %}}
**Réponse :** d)
{{%/expand%}}

---


{{% exercice "Quizz" %}}
**Question 3 :** Quel est le but du OneTime binding ?
{{% /exercice %}}

a)	L’utilisateur ne peut interagir avec l’élément qu’une seule fois    
b)	L’interface ne peut être mise à jour qu’une seule fois  
c)	L’interface peut être mise à jour uniquement si le type de l’élément n’est déclaré qu’une seule fois   
d)	L’utilisateur ne peut interagir avec l’élément que si son type n’est déclaré qu’une seule fois.


{{% expand "solution" %}}
**Réponse :** b)
{{%/expand%}}

---


{{% exercice "Quizz" %}}
**Question 4 :** Quel est le mode de binding le plus intéressant pour une TextBox en mode read-only ?
{{% /exercice %}}

a)	-	One way  
b)	-	TwoWay  
c)	-	TwoWay  
d)	-	OneWayToSource  


{{% expand "solution" %}}
**Réponse :** a)
{{%/expand%}}

---


{{% exercice "Quizz" %}}
**Question 5 :** Quels sont les différents types de binding ?
{{% /exercice %}}

a)	-	One way  
b)	-	TwoWay  
c)	-	OneTime    
d)	-	OneWayToSource


{{% expand "solution" %}}
**Réponse :** c)
{{%/expand%}}

---


{{% exercice "Quizz" %}}
**Question 6 :** Quel est le mode de binding le plus intéressant pour un élément d’un formulaire ?
{{% /exercice %}}

a)	-	One way  
b)	-	TwoWay  
c)	-	OneTime    
d)	-	OneWayToSource  


{{% expand "solution" %}}
**Réponse :** b)
{{%/expand%}}

---


{{% exercice "Quizz" %}}
**Question 7 :** Quel est le mode de binding le plus intéressant pour un élément d’un formulaire ?
{{% /exercice %}}

a)	```<TextBox Name="txtvalue" Text="{Binding ElementName=mySlider, Path=Value, Mode=OneWayToSource, UpdateSourceTrigger=PropertyChanged}” </TextBox> ```  
b)	```<TextBox Name="txtvalue" Text="{Bind ElementName=mySlider, Path=Value, Mode=OneWayToSource, UpdateTrigger=PropertyChanged}” </TextBox>  ```  
c)	```<TextBox Name="txtvalue" Text="{Bind ElementName=mySlider, Path=Value, Mode=OneWayToSource, UpdateTrigger=PropertyChanged}” </TextBox> ```   
d)	```<TextBox Name="txtvalue" Text="{Bind ElementName=mySlider, Path=Value, Mode=OneWay, UpdateTrigger=PropertyChanged}” </TextBox> ```  


{{% expand "solution" %}}
**Réponse :** a)
{{%/expand%}}

---


{{% exercice "Quizz" %}}
**Question 8 :** A quoi sert la valeur Path en databinding ?
{{% /exercice %}}

a)	A quoi sert la valeur Path en databinding ?  
b)	A indiquer de type de binding (oneway, twoway...)  
c)	A indiquer de type de binding (oneway, twoway...)  
d)	A importer des fichiers sur sa fenêtre WPF


{{% expand "solution" %}}
**Réponse :** a)
{{%/expand%}}

---


{{% exercice "Quizz" %}}
**Question 9 :** Imaginons que nous voulions récupérer la valeur sélectionnée dans une ListBox et la bind à un autre élément. Quel sera alors la valeur du Path ?
{{% /exercice %}}

a)	Path = SelectedItem   
b)	Path = Value  
c)	Path = SelectedItem.Content  
d)	Path = Value.Content


{{% expand "solution" %}}
**Réponse :** c)
{{%/expand%}}

---


{{% exercice "Quizz" %}}
**Question 10 :** Quelle(s) est (sont) la (les) valeur(s) nécessaire(s) pour réaliser un binding correct ?
{{% /exercice %}}

a)	ElementName  
b)	Path   
c)	Mode   
d)	UpdateSourceTrigger
e) Toutes les réponses

{{% expand "solution" %}}
**Réponse :** e)
{{%/expand%}}

---