# Around C# and WPF [![Netlify Status](https://api.netlify.com/api/v1/badges/0ddc6fed-bc69-4db4-a027-e873fc711646/deploy-status)](https://app.netlify.com/sites/pimo-wpf/deploys)<!-- omit in toc -->

## Table des matières <!-- omit in toc -->

- [Introduction](#introduction)
- [Construire le projet](#construire-le-projet)
  - [Cloner le projet](#cloner-le-projet)
  - [Installer Hugo](#installer-hugo)
  - [Exécution en local](#exécution-en-local)
  - [Construction du site statique](#construction-du-site-statique)
- [Tutoriel](#tutoriel)
  - [Ajouter une page](#ajouter-une-page)
  - [Ajouter du html personnalisé](#ajouter-du-html-personnalisé)

## Introduction

Ceci est un [MOOC](https://fr.wikipedia.org/wiki/Massive_Open_Online_Course) sur **WPF (Windows Presentation Foundation)**, un framework d’interface utilisateur qui permet de créer des applications de bureau clientes.

Un générateur de site web, [HUGO](https://gohugo.io/), sera utilisé pour générer le site web contenant le MOOC.

## Construire le projet

### Cloner le projet

```bash
git clone --recursive https://github.com/smahot/pimo-wpf.git
```

### Installer Hugo

Lien de la documentation : [Intaller Hugo](https://gohugo.io/getting-started/installing)

Autrement sur Windows, pour la version 0.68.3 :

- Lancer l'`invite de commande` et se positionner sur le bureau :

```bash
cd Desktop
```

- Télécharger la [dernière version de l'archive](https://github.com/gohugoio/hugo/releases/latest) :

```bash
wget https://github.com/gohugoio/hugo/releases/download/v0.68.3/hugo_0.68.3_Windows-64bit.zip
```

- Décompresser l'archive dans un dossier appelé hugo:

Avec [7-zip](https://www.7-zip.fr/download.html) :

```bash
"C:\Program Files\7-Zip\7z.exe" x hugo_*_Windows-64bit.zip -ohugo
```

Avec Powershell :

```powershell
Expand-Archive "hugo_*_Windows-64bit.zip" "hugo"
```

- Déplacer le dossier `hugo` dans le dossier `Documents`par exemple :

```bash
move hugo %userprofile%\Documents
```

Le dossier doit contenir :

```txt
- hugo.exe (l'exécutable dont on a besoin)
- LICENSE (le fichier de license)
- README.md (le readme markdown, à ouvrir avec VS Code par exemple)
```

- Ajouter le dossier contenant l'executable au path

```bash
path=%path%;%userprofile%\Documents\hugo
```

Le programme doit maintenant pouvoir être utilisé en ligne de commande avec `hugo`.
Vous pouvez supprimer l'archive `zip` de votre bureau.

### Exécution en local

```bash
hugo serve
```

> Le site est disponible à l'adresse suivante : [http://localhost:1313/](http://localhost:1313/)

### Construction du site statique

```bash
hugo
```

> Les fichiers se trouvent dans le dossier `/public`.

## Tutoriel

Le contenu du cours est rédigé en [markdown](https://fr.wikipedia.org/wiki/Markdown).

Nous avons utilisé le thème [Learn](https://learn.netlify.com/en/) pour la mise en page.

Le site est déployé automatiquement à partir de la branche *master* :

- [Netlify](https://pimo-wpf.netlify.com)
- [Render](https://pimo-wpf.onrender.com/)

Lien des documentations :

- [Hugo](https://gohugo.io/documentation/)
- [Learn theme](https://learn.netlify.com/en/)

### Ajouter une page

L'arborescence du site se trouve dans le dossier **/content/**.

> [Explication de l'arborescence](https://learn.netlify.com/en/cont/pages/)

Pour créer une page nommée *test* à la racine du site, deux solutions :

```txt
/content/test/_index.fr.md
```

ou

```txt
/content/test.fr.md
```

> Ici `fr` correspond à l'id de la langue.
> Plus de détail sur le fonctionnement du mode multi-langue [ici](https://learn.netlify.com/en/cont/i18n/).

Ensuite, ouvrez le fichier markdown avec un éditeur de texte comme [Visual Studio Code](https://code.visualstudio.com/), [Atom](https://atom.io/) ou [Notepad++](https://notepad-plus-plus.org/).

Ajoutez en entête :

```txt
+++
title = "Nom du titre"
weight = 5
pre = "<b>X. </b>"
+++
```

- **weight** sert à classer les différentes pages dans l'ordre croissant dans le menu de navigation.
- **title** sera le nom du titre qui sera affiché dans le menu de navigation.
- **pre** est le préfixe du titre

Puis remplissez la page.

Un template est disponible [ici](/content/template.fr.md).

### Ajouter du html personnalisé

Si la syntaxe markdown n'est pas sufisante, il est possible d'ajouter du html via les **shortcodes**.

Les shortcodes sont dans le dossier `/layouts/shortcodes/`.

Le nom du fichier doit s'appeler de la façon suivante : `nomDuShortcode.html`

Puis le code html du fichier peut être appelé de la façon suivante : `{{% nomDuShortcode %}}`.

Il est possible de passer des paramètres comme pour une fonction : `{{% nomDuShortcode "param1" "param2" %}}`

> Pour plus de détails :
>
> - [Exemples du thème](https://learn.netlify.com/fr/shortcodes/)
> - [Documentation hugo](https://gohugo.io/content-management/shortcodes/)
