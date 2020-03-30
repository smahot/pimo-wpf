+++
title = "Projet final"
weight = 40
+++

## Le projet :

Vous êtes un gérant de restaurant. Comme vous possédez des connaissances en WPF, vous allez designer une application qui va vous permettre de surveiller l'évolution de vos stocks d'ingrédients et de garder en mémoire les plats proposés. L'interface devrait ressembler à l'image qui suit : 

![image_resto](/img/projet_resto/template_resto.png?height=300px)

A noter que vous n'êtes pas obligé de répliquer cette fenêtre au pixel près. Laissez libre cours à votre imagination, mais vous devrez respecter les spécifications suivantes.

## Les spécifications : 


Vous allez devoir créer :
- Une classe Recipe composé d'un nom, d'une liste d'ingrédient (avec leur quantité) et d'un prix
- Une classe Restaurant qui possède une trésorerie ainsi qu'une liste d'ingrédient et de Recipe

S'affiche alors sur la fenêtre : 
- Les différentes actions réalisable
- Le nom du Restaurant
- La liste des ingrédients en stock
- Les tables du restaurant

  
Les fonctionnalités : 
- Ajouter un nouvel ingrédient au stock du restaurant
- Ajouter un nouveau plat/Recipe (avec nom, ingrédients)
- Cliquer sur une table ouvre un menu pour commander un plat/Recipe. Une fois choisi, la trésorerie augmente du prix du plat commandé.

Précisions : 
- Tout l'affichage doit se faire avec du Data Binding.
- Vous devez faire en sorte que l'on ne puisse pas commander une recette si les ingrédients ne sont pas en quantité suffisante en stock.


