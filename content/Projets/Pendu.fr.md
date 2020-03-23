+++
title = "Pendu"
weight = 3002
pre = "Projet chapitre 2 : "
+++

Indices de réalisation :

Voici l’organisation des éléments de la fenêtre :

![image1](/img/pendu/img01.png?height=100px)

![image2](/img/pendu/img02.png)


Créer une classe spécifiquement pour le mot à deviner. Cette classe permettra de l’initialiser et de réaliser certaines fonctions de vérification (si le mot est rempli ou non, voir son avancée (ex 4 lettres sur 8)).

Le joueur perd une chance à chaque fois qu’une lettre qui n’est pas dans le mot est choisie. Le joueur possède initialement 10 chances. Le joueur ne perd pas de chance lorsqu’une lettre est correctement choisie.
Le but est de remplit le mot à deviner (qu’il n’y ait plus de _ ).

{{% expand "Correction" %}}

Code source : pendu.zip

- Initialize_word_to_guess_label :

Permet d’initialiser graphiquement le mot à deviner à l’intérieur de notre fenêtre de jeu (- - - -    pour chat par exemple).
Button_Try_Click : Fonction appelée lorsque le bouton content « Try ! » est cliqué. Cette fonction appelle alors Propose_Letter.

- Propose_Letter :

Fonction qui retourne True si la lettre contenue dans le InputText de proposition de lettre se trouve dans le mot à deviner. Cette fonction permet de modifier l’avancée du mot à déterminer, qui est un attribut de l’objet To_guess. Elle utilise All_Indexes_Of pour obtenir les positions de la lettre proposée dans le mot. Cette fonction utilise aussi change_Advance_Word.

- All_Indexes_Of :

Utilise l’attribut de To_guess « Letter_proposed ». Si cet attribut se retrouve dans l’attribut word_to_guess de To_guess, cela retourne l’index de la lettre proposée. Ce qui est retourné est une liste contenant un ou plusieurs index (si la lettre apparaît plus d’une fois dans le mot).

- Change_Advance_Word :

Permet de modifier l’attribut word_advance qui représente l’avancée de la détermination du mot (Ex : - - - e – pour le mot à deviner « chien »).

- Check_Victory_Defeat :

Permet de verifier si l’attribut advance_word de To_guess est similaire au mot à deviner. Si oui (il n’y a plus de – dans advance_word), alors le joueur a gagné. Il perd si il y a encore des – dans advance_word et si le nombre d’échecs de proposition de lettre est supérieur à 10.
{{% /expand %}}

{{%attachments style="grey" /%}}
