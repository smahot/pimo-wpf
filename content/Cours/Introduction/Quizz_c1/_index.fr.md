+++
title = "Quizz Chapitre 1"
weight = 1005
pre = "<b>1.5 </b>"
+++

{{% exercice "Quizz" %}}
**Question 1 :** XAML est un langage déclaratif, c’est-à-dire : 
{{% /exercice %}}

a)	Il permet la description de données structurées.  
b)	Il permet de construire une structure définie dans le fichier C# associé.  
c)	Il s’occupe de la déclaration des instances des classes utilisées.  

{{% expand "solution" %}}
**Réponse :** a) XAML ne fait que décrire une structure, donner des informations sur un objet qui sera instancié ensuite par C#, pas l’inverse !
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 2 :** Les balises sont « des unités syntaxiques délimitant une séquence de caractères »… En somme, une balise sert à : 
{{% /exercice %}}

a)	Signaler un problème potentiel dans le fichier XAML lors de la compilation.  
b)	Regrouper les informations sur une instance d’un objet dans le fichier XAML.  
c)	Exécuter des morceaux de code C# dans le fichier XAML.  
d)	Permettre à votre code de ne pas se noyer

{{% expand "solution" %}}
**Réponse : b)** Vous pouvez visionner une balise comme un bloc d’informations, qu’elle soit double ou unique, qui va indiquer à C# comment créer une instance d’une classe. Par exemple : <Button Width="50" Height="60" … /> est lu par C# comme « crée un bouton avec une largeur (Width) de 50 pixels et une hauteur (Heitz) de 60 pixels ("…" correspondrait à d’autres attributs de bouton).
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 3 :** Outre XAML, d’autres langages utilisent des balises. Lesquels ?
{{% /exercice %}}

a)	Json  
b)	XML  
c)	HTML  
d)	Python

{{% expand "solution" %}}
**Réponse :** b) et c). Bien que servant un même objectif, XML est souvent considéré trop « verbeux » comparé à Json, à cause des balises ouvrantes et fermantes partout notamment. HTML utilise des balises pour approximativement le même usage que XAML : organiser une interface. 
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 4 :** lequel de ces exemples est faux (on ne demande que le contenu, la hauteur et la largeur du bouton) ? 
{{% /exercice %}}

a)```<Button> Width="50" Height="50" Content="Button Rouge" </Button> ```  
b)```<Button Width="50" Height="50" Content="Button Rouge" /> ```  
c)```<Button Width="50" Height="50"> Button Rouge </Button> /> ```

{{% expand "solution" %}}
**Réponse :** a) Les attributs du bouton doivent être placés dans les balises, pas entre.
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 5 :** Que dois-je faire si je veux modifier la taille de la fenêtre ? 
{{% /exercice %}}

a)	Créer une instance de la classe Rectangle et lui donner les proportions souhaitées.  
b)	Changer les valeurs Height et Width dans la balise Window.  
c)	Changer les valeurs Height et Width dans la balise Grid qui a été créé au lancement du projet.

{{% expand "solution" %}}
**Réponse :** b) La question concerne la fenêtre de l’application, avec la croix rouge en haut à droite, pas le contenu de cette dernière. C’est donc pour cela que l’on modifie ses attributs à elle. C’est cette première balise qui englobe toutes les autres, <Window - - -> </Window> qui définie la taille de l’application.
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 6 :** la balise grid est forcément de la même taille que la Window ?
{{% /exercice %}}

a)	Vrai  
b)	Faux  

{{% expand "solution" %}}
**Réponse :**  b) la grid pourra être de taille différente, comme plus petite la plupart du temps. Le vide laissé pourra être comblé par une autre grid par exemple.
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 7 :** lorsque je drag’n’drop un bouton depuis la toolbox de visual studio code sur la fenêtre d’application, comment se crée le bouton sur le fichier XAML ? 
{{% /exercice %}}

a)	Dans une balise double  
b)	Dans deux balises : une pour ses coordonnées, une pour son contenu  
c)	Dans une balise simple  
 
{{% expand "solution" %}}
**Réponse :** c) Seules les informations de base sur le positionnement sont écrites. La hauteur et la largeur seront set up automatiquement aussi mais pas décrites. Vous pouvez alors ajouter/modifier/supprimer toutes les infos que vous voulez ensuite.
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 8 :** Comment fait-on un commentaire en XAML ?
{{% /exercice %}}

a)	``<!-- commentaire -->``  
b)	``!-> commentaire  ``  
c)	``//  ``  
d)	``#  ``

 
{{% expand "solution" %}}
**Réponse :** a) Le commentaire doit être placé entre ces deux symboles. Cela fonctionne un peu comme le /* */ de C#. La b) n’existe pas. C) concerne la plupart des langages comme C et C# et la d) est le commentaire dans Python.
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 9 :** Il y une erreur dans cette ligne. Trouvez là :  
``<Button Content="Button" HorizontalAlignment="Left" Margin="302,179,0,0" VerticalAlignment="Top" Width="75">``
{{% /exercice %}}

a)	La marge est en 4 dimensions plutôt qu’en 3 comme tout objet dans l’espace.  
b)	Le Content ne devrait pas se placer ici, mais dans une deuxième balise.  
c)	Il manque un slash à la fin de la balise unique

{{% expand "solution" %}}
**Réponse :**  c) et oui, cela risque d’être une erreur fréquente au début. Si le slash n’est pas là, XAML va considérer que c’est une balise ouvrante et vas se demander pourquoi la balise suivante n’a rien à voir avec la première.
{{%/expand%}}

---

{{% exercice "Quizz" %}}
**Question 10 :** La fonction en C# qui construit l’application avec le fichier XAML est : 
{{% /exercice %}}

a)	DebutApplication() ;  
b)	InitializeComponent() ;  
c)	StartCompiling() ;  

{{% expand "solution" %}}
**Réponse :**  b) C'est la fonction qui est présente dès la création du programme.
{{%/expand%}}

---