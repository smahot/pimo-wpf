Around C# and WPF <!-- omit in toc --> 
=================

## Table des matières <!-- omit in toc --> 
- [Introduction](#introduction)
- [Construire le projet](#construire-le-projet)
  - [Exécution en local](#ex%c3%a9cution-en-local)
  - [Construction du site statique](#construction-du-site-statique)


## Introduction

Ceci est un [MOOC](https://fr.wikipedia.org/wiki/Massive_Open_Online_Course) sur **WPF (Windows Presentation Foundation)**, un framework d’interface utilisateur qui permet de créer des applications de bureau clientes.

Un générateur de site web, [HUGO](https://gohugo.io/), sera utilisé pour générer le site web contenant le MOOC.

## Construire le projet

### Exécution en local

```
hugo serve
```

> Le site est disponible à l'adresse suivante : [http://localhost:1313/](http://localhost:1313/)

### Construction du site statique

```
hugo
```

> Les fichiers se trouvent dans le dossier `public`.