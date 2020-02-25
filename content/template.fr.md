+++
title = "Template"
weight = 5
tags = ["tutorial", "template"]
+++

Le retour du PIMO
==============================



{{% notice note %}}
Il est conseillé d'utiliser un éditeur de texte comme [Visual Studio Code](https://code.visualstudio.com/) ou [Atom](https://atom.io/) pour pouvoir profiter des extensions markdown.
{{% /notice %}}

_Bref texte d’introduction_

#### Sommaire avec lien vers les parties
- [Le retour du PIMO](#le-retour-du-pimo)
      - [Sommaire avec lien vers les parties](#sommaire-avec-lien-vers-les-parties)
  - [A. Une nouvelle aube](#a-une-nouvelle-aube)
    - [a. _Felix Felicis_](#a-felix-felicis)
    - [b. Au pays des ~~éponges~~](#b-au-pays-des-s%c3%a9pongess)
  - [B. Un nouveau crépuscule](#b-un-nouveau-cr%c3%a9puscule)

---

## A. Une nouvelle aube 

_Petit texte d’introduction_

### a. _Felix Felicis_

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed non risus. Suspendisse lectus tortor, dignissim sit amet, adipiscing nec, ultricies sed, dolor.  

    Exemple à recopier et à modifier

{{% notice tip %}}
On peut copier le texte facilement avec le bouton `copier` !
{{% /notice %}}

Cras elementum ultrices diam. Maecenas ligula massa, varius a, semper congue, euismod non, mi.  

![Test Image 1](/img/template/Capture.PNG?height=300px)

> On peut cliquer sur l'image pour l'agrandir !

Proin porttitor, orci nec nonummy molestie, enim est eleifend mi, non fermentum diam nisl sit amet erat.  

**Exercice :**

    Consignes :
      - consigne 1
      - consigne 2

    - [x] Case cochée
    - [ ] Case non cochée


> {{%expand "Correction" %}}

```python
from __future__ import absolute_import, division, print_function, unicode_literals

# TensorFlow and tf.keras
import tensorflow as tf
from tensorflow import keras

# Helper libraries
import numpy as np
import matplotlib.pyplot as plt

print(tf.__version__)
```

```sql
SELECT * FROM movie WHERE title LIKE '%A';
```

```csharp
Console.WriteLine("Hello World !");
```
{{% /expand%}}

Duis semper. Duis arcu massa, scelerisque vitae, consequat in, pretium a, enim. Pellentesque congue. Ut in risus volutpat libero pharetra tempor. Cras vestibulum bibendum augue. Praesent egestas leo in pede. Praesent blandit odio eu enim.  

{{< youtube-hw w7Ft2ymGmfc 640 360>}}


Pellentesque sed dui ut augue blandit sodales. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; Aliquam nibh. Mauris ac mauris sed pede pellentesque fermentum. Maecenas adipiscing ante non diam sodales hendrerit. 

### b. Au pays des ~~éponges~~

{{% notice warning %}}
Attention à bien sécuriser son réseau !
{{% /notice %}}

{{<mermaid align="left">}}
graph LR
A[Alice] -.->|...| B[Bob]
A -->|20/20| C[MiddleMan]
C -->|0/20| B
{{< /mermaid >}}

> https://mermaid-js.github.io/mermaid/

Deux ou trois exercices reprenant les points vus dans les sous parties. 

---

## B. Un nouveau crépuscule 

{{% notice info %}}
Tableau en markdown
{{% /notice %}}

| Titre 1       |     Titre 2     |        Titre 3 |
| :------------ | :-------------: | -------------: |
| Colonne       |     Colonne     |        Colonne |
| Alignée à     |   Alignée au    |      Alignée à |
| Gauche        |     Centre      |         Droite |

<!-- tire un trait -->
---
***



{{% expand-bold "Autres shortcodes" %}}
 - [Hugo custom shortcode](https://gohugo.io/templates/shortcode-templates/)
 - [docdock theme](https://theme-hugo-docdock-demo.aerobaticapp.com/shortcodes/)
 - [learn theme](https://learn.netlify.com/en/shortcodes/)
{{%/expand%}}

{{% expand"Niveau de titres" %}}
# h1 Heading <!-- omit in toc -->
## h2 Heading <!-- omit in toc -->
### h3 Heading <!-- omit in toc -->
#### h4 Heading <!-- omit in toc -->
##### h5 Heading <!-- omit in toc -->
###### h6 Heading <!-- omit in toc -->

{{%/expand%}}



{{%attachments style="grey" /%}}

> Liste les pièces jointes de la page ([doc](https://learn.netlify.com/en/shortcodes/attachments/))
>
> [Syntaxe markdown](https://learn.netlify.com/en/cont/markdown/)

{{% button href="/exercices" %}}Lien vers une page d’exercice {{% /button %}}  

{{% button href="/projets" icon="fas fa-briefcase" icon-position="right" %}}Lien vers le projet à faire pour ce chapitre{{% /button %}}

{{% button href="https://github.com/smahot/pimo-wpf" %}}Lien vers le github {{% /button %}}  
