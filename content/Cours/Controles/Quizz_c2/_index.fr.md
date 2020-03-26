+++
title = "Quizz Chapitre 2"
weight = 2003
pre = "<b>2.3 </b>"
+++

{{% exercice "Quizz" %}}
**Question 1 :** Laquelle de ces balises de boutons est incorrect : 
{{% /exercice %}}

a)	``<Button Content="Hello !" HorizontalAlignment="Center" VerticalAlignment="Center" Width=200 Height=200/>``  
b)	``<Button HorizontalAlignment="Center" VerticalAlignment="Center" Width="200" Height="200">Hello</Button>`` 
c)	``<Button Content="Hello !" HorizontalAlignment="Center" VerticalAlignment="Center" Width="200" Margin=”0”/>``  
d)	``<Button Content="Hello!" Width="2000" Height="2000"/>``


{{% expand "solution" %}}
**Réponse :** a) Width et Height prennent un argument entouré de ‘’. La b) est une déclaration normale avec deux balises. La c) déclare avoir 0 px de marge dans chaque direction et la d) possède juste très peu d’attribut.
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 2 :** ``<Button - - - Margin=’’0,20,20,0’’/>`` : Les marges de 20 px sont : 
{{% /exercice %}}

a)	En haut à gauche  
b)	En bas à gauche  
c)	En haut à droite  
d)	En bas à droite  

{{% expand "solution" %}}
**Réponse :** c) Il y a deux manières d’écrire les marges : Margin=’’X’’ avec X le nombre de pixel dans chaque direction, et Margin=’’W,X,Y,Z’’ avec W la marge à gauche, X la marge en haut, Y la marge à droite et Z la marge en bas. Attention, pour ceux qui reviennent d’HTML/CSS, vous ne pouvez pas utiliser Margin.Top ou Margin.Bottom par exemple pour définir une seule marge. Vous devrez écrire Margin=’’0,0,X,0’’.
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 3 :** Vous avez un bouton centré au milieu de la fenêtre (VerticalAlignement=’’center’’ HorizontalAlignement=’’center’’) et de taille 50*50
Vous voulez créer un autre bouton de 50*50, lui aussi avec VerticalAlignement=’’center’’ HorizontalAlignement=’’center’’. Quelle marge devrait-on lui donner pour qu’il ne se superpose avec le premier bouton et soit bord à bord avec ?
{{% /exercice %}}

a)	75  
b)	50  
c)	100  
d)	125  

{{% expand "solution" %}}
**Réponse :** c) Pour comprendre ce calcul, se référer la vidéo sur comment placer les éléments dans la fenêtre.
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 4 :** vous avez un bouton de 40 par 40 dans l’angle en haut à gauche de votre fenêtre avec VerticalAlignement="top" HorizontalAlignement="left". Toujours avec les mêmes alignements, quelles seraient les marges à donner pour qu’un bouton de 50 par 50 touche l’angle bas droit du premier avec son angle haut gauche ? 
{{% /exercice %}}

a)	90,90,0,0  
b)	40,40,0,0  
c)	70,70,0,0  
d)	45,45,0,0  

{{% expand "solution" %}}
**Réponse :** b) Pour comprendre ce calcul, se référer la vidéo sur comment placer les éléments dans la fenêtre.
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 5 :** Un Textblock permet de :
{{% /exercice %}}

a)	Afficher des chaînes de caractères et écrire dedans  
b)	Faire des requêtes par des utilisateurs en rentrant du code dedans  
c)	Juste afficher du texte et rien d’autre.  
d)	Aucun des trois au-dessus  

{{% expand "solution" %}}
**Réponse :** c) A ne pas confondre avec la Textbox qui elle, permet aussi à l’utilisateur d’écrire dedans.
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 6 :** L’attribut qui est affiché dans le Textblock s’appelle : 
{{% /exercice %}}

a)	Content  
b)	Text  
c)	Display  
d)	Display_text  

{{% expand "solution" %}}
**Réponse :** b) Content est pour le contenu des boutons si vous aviez un doute. Le reste n’est pas utilisé dans ce contexte (ou n’existe pas) dans WPF.
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 7 :** L’attribut qui est affiché dans le Textblock s’appelle : 
{{% /exercice %}}

a)	Avoir trois états différents  
b)	D’être placé dans une autre balise  
c)	Placer la checkbox en utilisant les mêmes attributs que le bouton.  
d)	Aucun des trois au-dessus

{{% expand "solution" %}}
**Réponse :** d) IsThreeState permet d’avoir un troisième état outre coché ou décoché. La checkbox, comme tout autre contrôle, est déjà placé dans au moins une balise : Window. Il n’y a pas de changement pour le positionner par rapport à un bouton.
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 8 :** La ListBox est un menu déroulant qui vous propose de sélectionner une option en particulier. Comment s’appellent les items qu’elle contient ?
{{% /exercice %}}

a)	ListBoxItem  
b)	Button  
c)	ListCheckBox  
d)	Aucun des trois au-dessus  

{{% expand "solution" %}}
**Réponse :** a) C’est le type spécial que l’on utilise dans les Listbox.
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 9 :** Comment s’appelle l’attribut qui permet le retour à la ligne ? 
{{% /exercice %}}

a)	Textsigning  
b)	Textwarping  
c)	Textcycling  
d)	Textwrapping  

{{% expand "solution" %}}
**Réponse :** d) Et pour bien préciser d’aller à la ligne, il faut lui donner l’argument "Wrap".
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 10 :** Lequel de ces attributs n’existent pas ?
{{% /exercice %}}

a)	FontSize  
b)	FontColor   
c)	FontStyle  
d)	FontWeight  

{{% expand "solution" %}}
**Réponse :** b) Contrairement à ce que vous pouviez penser, la couleur de la police est définie avec Foreground. Il peut prendre en argument lors de sa définition soit des codes de couleurs hexadécimaux, soit certains strings reconnus (un peu à la manière d’HTML).
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 11 :** Quels types d’événements existent en WPF ?
{{% /exercice %}}

a) Direct Event  
b) Tunneling event  
c) Bubbling event  
d) Les trois

{{% expand "solution" %}}
**Réponse :** d)
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 12 :** Comment activer l’événement MouseEnter ?
{{% /exercice %}}

a) En cliquant sur l’élément où l’événement est défini.   
b) En appuyant sur la touche entrée de votre clavier.   
c) En passant la souris sur l’élément où est défini l’événement.  
d) En activant la molette de la souris sur l’élément.

{{% expand "solution" %}}
**Réponse :** c)
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 13 :** Quelle ligne de code permet d’empecher la propagation d’un événement e?
{{% /exercice %}}

a) e.Handled();     
b) e.Handled =true;    
c) e.Handling;   
d) Aucun des trois

{{% expand "solution" %}}
**Réponse :** a)
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 14 :** Prenons l’arbre suivant :
- Window
    - Grid
        - Rectangle

Un événement MouseDown a été assigné à Window.

En cliquant sur quel(s) élément(s) peut-on déclencher cet événement
{{% /exercice %}}

a) Window       
b) Grid      
c) Rectangle  

{{% expand "solution" %}}
**Réponse :** a), b) et c)
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 15 :** Comment s’appelle l’événement qui s’active lorsqu’une touche du clavier est appuyée :
{{% /exercice %}}

a) KeyEnter        
b) TextInput      
c) KeyDown  
d) Aucun des trois

{{% expand "solution" %}}
**Réponse :** c)
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 16 :** Lesquels de ces évènements n’existent pas ?
{{% /exercice %}}

a) KeyDown          
b) MouseQuit      
c) MouseLeftButton  
d) DragOver

{{% expand "solution" %}}
**Réponse :** b) et c)
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 17 :** Laquelle de ces propositions est fausse ?
{{% /exercice %}}

a) Un objet peut avoir plusieurs événements.         
b) Une seule action peut être associée à un événement.    
c) L’événement Click est un événement exclusif aux boutons

{{% expand "solution" %}}
**Réponse :** b) 
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 18 :** Qu'est-ce qu’un élément source ?
{{% /exercice %}}

a) L’élément Window          
b) L’élément porteur de l’événement      
c) L’élément où est déclenché l’événement   

{{% expand "solution" %}}
**Réponse :** b)
{{%/expand%}}

---