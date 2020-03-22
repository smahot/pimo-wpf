+++
title = "Les évènements"
weight = 2002
pre = "<b>2.2 </b>"
+++

- [a. Comment affecter un evenement a un objet](#a-comment-affecter-un-evenement-a-un-objet)
- [b. Liste des événements](#b-liste-des-événements)
- [c. Les événements routés](#c-les-événements-routés)
  - [Direct Event](#direct-event)
  - [Bubbling Event](#bubbling-event)
  - [Tunnel Events](#tunnel-events)

En WPF, un événement est déclenché lorsqu’une action de l’utilisateur interagit avec les objets (bouton, image...) dans la fenêtre affichée. Ces événements permettent d’impacter l’environnement et des méthodes peuvent être rattachées à ceux-ci.

## a. Comment affecter un evenement a un objet

Pour affecter un évènement à un objet :

- Sélectionner l’objet.

![image1](/img/2.2/img01.png?height=300px)

- Choisir un évènement dans le menu “propriétés” de l’objet (en bas à droite de votre environnement Visual studio)

![image2](/img/2.2/img02.png?height=300px)

- Lorsque vous double-cliquez sur un évènement, vous êtes redirigés dans le document .cs. Une fonction a été créée.  

![image3](/img/2.2/img03.png?height=100px)

- A vous de remplir cette méthode en fonction de ce que vous attendez de l’évènement. Cette fonction sera exécutée lorsque l’évènement se sera activé. On peut par exemple demander l’affichage d’un message lorsque le bouton est cliqué :

![image4](/img/2.2/img04.png?height=100px)

## b. Liste des événements

Vous trouverez ici quelques exemples mais nous vous invitons à en découvrir plus par vous-même dans la barre d’outils des évènements.

| Nom de l’évènement  | Comment l’activer ?                                       |
| ------------------- | --------------------------------------------------------- |
| Click               | Quand on clique sur le bouton                             |
| KeyDown             | Une touche du clavier est enfoncée                        |
| KeyUp               | Une touche du clavier est relâchée                        |
| TextInput           | Une touche correspondant à du texte est frappée           |
| MouseDown           | Un bouton de la souris est enfoncé                        |
| MouseLeftButtonDown | Le bouton gauche de la souris est enfoncé                 |
| MouseLeftButtonUp   | Le bouton gauche de la souris est relâché                 |
| MouseMove           | La souris est placée au-dessus d’un élément               |
| MouseEnter          | La souris est sur un objet                                |
| MouseLeave          | La souris quitte un objet                                 |
| DragEnter           | Un objet commence à être glissé avec la souris            |
| DragLeave           | Un objet est déposé avec la souris au-dessus d’un élément |
| DragOver            | Un objet est glissé avec la souris au-dessus d’un élément |
| Drop                | Un objet est déposé avec la souris au-dessus d’un élément |

## c. Les événements routés

Quand un événement est émis par un élément de l’arbre visuel, il est propagé aux conteneurs successifs de cet élément. L’élément qui a déclenché l’événement est appelé élément source. Le sens de propagation est déterminé par la stratégie de routage.

C’est une notion importante à connaitre afin de bien comprendre comment les événements sont gérés au sein de la structure que l’on a créée.

Il existe trois types d’événements routés :

- Direct Event
- Bubbling Event
- Tunneling Event

### Direct Event

Les événements directs sont des événements qui sont seulement activés par l’élément dans lequel l’événement est implémenté. L’évènement n’est pas propagé.

Par exemple, l’événement que nous avons créé un peu plus haut est un événement direct.

### Bubbling Event

L’événement est traité au niveau de l’élément source puis successivement par chaque niveau de conteneur (dans le sens montant) jusqu'à la racine de l’arbre. D’où l’analogie avec une bulle qui remonte à la surface.

Pour la suite, nous allons considérer l’arbre suivant :

```txt
 - Window
    - Grid
       - Rectangle
```

Voyons comment cela fonctionne avec un exercice :

- Créer une grille que vous pouvez colorer pour une meilleure visibilité
- Dans cette grille, insérez un rectangle

![image5](/img/2.2/img05.png?height=300px)

 La structure de votre document est donc la suivante :

 ```txt
 - Window
    - Grid
       - Rectangle
 ```

Dans un premier temps, ajouter un évènement *mouseDown* à la Window.

![image6](/img/2.2/img06.png?height=100px)

Lancez le programme.
Cliquez sur le rectangle ou la grille. Que se passe-t-il ?  

![image7](/img/2.2/img07.png?height=200px)

En effet, le message Window apparait car l’événement remonte l’arbre jusqu’à la racine.

Ajoutez le même évènement à la grille et au rectangle mais avec un autre message.

![image8](/img/2.2/img08.png?height=200px)

Cliquez sur le rectangle. Que se passe-t-il ?

![image9-11](/img/2.2/img09-11.png?height=200px)

Encore une fois, l’événement remonte l’arbre et active tous les événement MouseDown de l’élément source jusqu’à la racine..

### Tunnel Events

Les événements tunnels sont les opposés des événements bulle. En effet, l’événement est d’abord traité à la racine de l’arbre, puis successivement par chaque niveau de conteneur (dans le sens descendant) jusqu’à atteindre l’élément source.

Les événements Tunnel sont caractérisés par le préfixe “Preview”.

Exercice Tunnel :  
Reprenons la même structure que l’exercice précédent. Sauf que cette fois ci, nous allons affecter l’événement “PreviewMouseDown” aux trois éléments de notre arbre.

![image12](/img/2.2/img12.png?height=300px)

Si vous cliquez sur le rectangle, vous verrez que l’ordre d’apparition des messages est différent par rapport à tout à l’heure. Comme dit plus haut, l’événement se propage de la racine jusqu’à l’élément source qui est le rectangle ici.

![image13-15](/img/2.2/img13-15.png?height=200px)

{{% notice tip %}}
Il est possible d’empecher la propagation d’un évènement !
{{% /notice %}}

Reprenons l’exemple des événements bulles. Il est possible d’empêcher un évènement de se propager au-delà d’un certain élément.

Pour ce faire, il suffit d’ajouter "e.Handled=true” dans la fonction de l’évènement au niveau où l’on souhaite quela propagation s’arrête.

![image16](/img/2.2/img16.png?height=100px)

Si vous cliquez sur le rectangle, l’évènement atteindra la grille mais n’ira pas plus loin.

---

{{% button href="/exercices/c2/part2/" %}}Lien vers les exercices{{% /button %}}
