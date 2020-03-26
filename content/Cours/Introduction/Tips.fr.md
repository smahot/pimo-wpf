+++
title = "Tips : Les classes en XAML/WPF"
weight = 1003
pre = "<b>1.3 </b>"
+++

- [Introduction aux classes : Héritage et contrôles](#introduction-aux-classes--héritage-et-contrôles)
- [MVVM : Balises XAML et Classes partielles en code-behind](#mvvm--balises-xaml-et-classes-partielles-en-code-behind)
- [Classes personnalisées](#classes-personnalisées)
- [Créer des objets avec WPF : XAML et Csharp](#créer-des-objets-avec-wpf--xaml-et-csharp)

## Introduction aux classes : Héritage et contrôles

L’infrastructure UI du XAML offre une librairie extensive de contrôles qui supporte le développement d’interfaces utilisateurs pour Windows.
Certains d’eux ont une représentation graphique, tels que Button, Textbox, TextBlock, etc.; tandis que certains sont employés comme conteneurs pour d’autres contrôles ou éléments de contenue, comme, en autres, les images.
Tous les contrôles XAML sont hérités de `System.Windows.Controls.Control`.

Voici la hiérarchie d’héritage complète des éléments de contrôle :

![image1](/img/1.3/img01.png?height=300px)

Il existe quatre classes de base - **UIElement**, **ContentElement**, **FrameworkElement** et **FrameworkContentElement** - qui implémentent un important pourcentage des fonctionnalités d’éléments communes disponibles en WPF. Ces quatre classes sont référencées, dans ce SDK, **comme classes d’éléments de base**.

## MVVM : Balises XAML et Classes partielles en code-behind

La manière la plus courante de développer des applications Windows Presentation Foundation (WPF) est d’utiliser un schéma Modèle – Vue – Vue modèle, ou MVVM.
Il s’agit d’un design pattern qui peut être employé, dans notre cas, dans l’optique de faciliter la séparation du développement d’une GUI entre les données et la vue qui les affichent.
Le lien entre la vue et le modèle de données est fait par des mécanismes de **binding**, que l’on évoquera plus en détail ultérieurement. Globalement, en WPF, il est possible de créer les éléments UI visibles à l’aide de balises en XAML, et de séparer la définition UI en utilisant des fichiers de **code-behind**, qui sont ensuite joints au script XAML à l’aide de définitions **partielles** de classes.

Voici quelques règles qui conditionnent  les classes partielles :

- Une **classe partielle** doit dériver du type qui soutient l’élément racine.
- Les **gestionnaires d’événements** écrits dans le **code-behind** doivent être des méthodes d’instance et non statiques. Ces méthodes doivent être définies par la **classe partielle** dans le namespace CLR identifié par « x:Class », et ne peuvent être appelées que dans le scope de la classe en question. Les gestionnaires d’évènements répondent donc également aux contraintes de scope des classes identifiées par « x:Class ».

Le compilateur du markup WPF crée, pour chaque fichier XAML compilé, une **classe partielle**, dérivant d’une classe du type de l’élément racine. Lorsque l’on fournit du **code-behind** définissant également la même **classe partielle**, le code résultant est combiné dans les mêmes namespaces et classes de l’application compilée.

## Classes personnalisées

XAML implémenté dans les infrastructures CLR prend en charge la possibilité de définir une classe ou une structure personnalisée dans n’importe quel CLR, puis d’accéder à cette classe à l’aide du balisage XAML. Vous pouvez utiliser un mélange de types définis de WPF et de vos types personnalisés dans le même fichier de balisage, généralement en mappant les types personnalisés à un préfixe d’espace de noms XAML. Pour pouvoir être instanciée comme élément objet, votre classe doit répondre aux spécifications suivantes :

- Votre classe personnalisée doit être publique et prendre en charge un constructeur public (sans paramètre).
- Votre classe personnalisée ne doit pas être une classe imbriquée. Les classes imbriquées et le « point », dans leur syntaxe générale d’utilisation du CLR, interfèrent avec d’autres fonctionnalités WPF et/ou XAML.

**Notes :**

- Écriture et attribution d’un convertisseur de type :

Vous devrez parfois écrire une classe dérivée TypeConverter personnalisée pour fournir la conversion de type pour votre type de propriété.

- Spécifications pour la syntaxe des attributs de gestionnaire d’événements XAML sur les événements d’une classe personnalisée :

Pour être utilisable comme un événement CLR, l’événement doit être exposé comme un événement public sur une classe qui prend en charge un constructeur sans paramètre, ou sur une classe abstraite où l’événement est accessible sur les classes dérivées.

## Créer des objets avec WPF : XAML et Csharp

Commençons avec une application WPF, lancée sur Visual Studio, qu’on nommera `WpfApplication1`. Deux fichiers sont automatiquement générés par l’IDE : `MainWindow.xaml` et `MainWindow.xaml.cs`. Créons une classe personnalisée publique dans le fichier code-behind de type `.cs`. Plaçons la en dessous de la classe principale `MainWindow`, dans le namespace `WpfApplication1`. Nous l’appellerons `MyClass` :

```csharp
public class MyClass
{
    public MyClass()
    {
    }
}
```

Il faut ensuite trouver un moyen d’accéder à la définition de notre nouvelle classe depuis le document `MainWindow.xaml`, en important le namespace de la classe dans le code XAML. Il est possible d’importer le namespace de n’importe quelle assembly et d’utiliser ce dernier pour indiquer à quelle classe on fait référence. Nous utiliserons la ligne suivante, déjà présente dès le départ, mise en évidence en bleu ci-dessous :

![image2](/img/1.3/img02.png?height=200px)


L’étape suivante consiste à se débarrasser du champ `<Grid> </Grid>`, puisqu’il est impossible d’imbriquer une classe générale dans un Grid, qui a besoin d’une classe affichable. On les remplacera par : `<local:MyClass> </local:MyClass>`, qui nous permet d’utiliser le namespace désigné par `local` et d’y trouver `MyClass`. Vous risquez d’avoir un message d’erreur à ce moment-ci indiquant que MyClass n’est pas trouvable ou définie ; il suffit de run, d’arrêter, et vous n’aurez plus d’erreur.

Généralement, les composants WPF sont nommés à l’aide de la propriété NAME, mais il existe un mécanisme plus direct pour les classes personnalisées : Utiliser les propriétés offertes par la namespace XAML `x`. L’attribut `x:Name` est employable pour attribuer le nom utilisé par XAML pour créer l’instance, désignée par le nom `MyObject1` :

```xml
<local:MyClass x:Name="MyObject1"> </local:MyClass>
```

Si vous souhaitez vérifier, ajoutez un breakpoint juste après la ligne `InitializeComponent()` dans la classe `MainWindow`, utilisez le débogueur et observez que `MyObject1` a bien été instancié.

Comme avec les objets WPF, en XAML, il est possible d’attribuer des propriétés à des objets personnalisés. Retournons sur notre fichier `.cs`, et ajoutons une propriété triviale de type nombre entier dans `MyClass`, qu’on nommera `MyProperty`, pour rester dans la simplicité :

```csharp
private int _MyProperty;
public int MyProperty
{
    get { return _MyProperty; }
    set { _MyProperty = value; }
}
```

On peut ensuite y attribuer, par exemple, la valeur « 20 » dans le XAML. En cas d'erreur, n'hésitez pas à run puis à arrêter.

```xml
<local:MyClass x :Name="MyObject1" local:MyProperty="20"> </local:MyClass>
```

Un problème peut subvenir lorsque l’on souhaite initialiser une propriété qui prend un type de référence, tel que les types classe, délégué, tableau ou interface. Il faut donc écrire sa propre classe dérivée `TypeConverter`, qui fournira une conversion de type pour ce type de propriété. Créons tout d'abord, dans le même fichier `.cs`, une deuxième classe `MyDataClass` similaire à notre première classe.

```csharp
public class MyDataClass
{
    public MyDataClass()
    {
    }

    private int _MyProperty2;
    public int MyProperty2
    {
        get { return _MyProperty2; }
        set { _MyProperty2 = value; }
    }
}
```

Ajoutons ensuite cette propriété à `MyClass`, en dessous de `MyProperty` :

```csharp
private MyDataClass _MyDataClass;
public MyDataClass MyClassProperty
{
    get { return _MyDataClass; }
    set { _MyDataClass = value; }
}
```

Il faut maintenant pouvoir initialiser, directement depuis le XAML, notre propriété `MyClassProperty`. Nous allons donc implémenter un convertisseur de type personnalisé. Premièrement, ajoutons la ligne  `[TypeConverter(typeof(MyDataClassTypeConverter))]` juste au-dessus de votre classe `MyDataClass` :

```csharp
[TypeConverter(typeof(MyDataClassTypeConverter))]
public class MyDataClass
{ ...
```

Il faut maintenant créer la classe `MyDataClassTypeConverter`. Ajoutons en début de code, dans la liste des `using`, la ligne :

```csharp
using System.ComponentModel;
```

On peut désormais implémenter notre classe. Ici, il s’agit de  :

```csharp
public class MyDataClassTypeConverter : TypeConverter
{
    public override bool CanConvertFrom(ITypeDescriptorContext context, Type t)
    {
        if (t == typeof(String))
            return true;
        return false;
}
```

Comme vous pouvez le constater, le convertisseur de type doit hériter de `TypeConverter`, et implémente tout d’abord `CanConvertFrom` qui renvoie `True` ou `False`, si le convertisseur de type parvient, ou non, à effectuer la conversion demandée. La classe n’est pas encore entièrement définie, puisque c’est la seconde méthode dont nous avons besoin qui fait la conversion :

```csharp
public class MyDataClassTypeConverter : TypeConverter
{
    public override bool CanConvertFrom(ITypeDescriptorContext context, Type t)
    {
        if (t == typeof(String))
            return true;
        return false;
    }

    public override object ConvertFrom(ITypeDescriptorContext context, System.Globalization.CultureInfo culture, object val)
    {
            MyDataClass temp = new MyDataClass();
            temp.MyProperty2 = Convert.ToInt32((string)val);
            return temp;
    }
}
```

Cette définition correspond à celle d’un convertisseur de type String en nombre entier 32 bits. Voici donc une mise en pratique simple vous détaillant les bases de la création d’un objet personnalisé. Il suffit maintenant de compléter votre code XAML :

```xml
<local:MyClass x:Name="MyObject1" local:MyProperty="20" local:MyClassProperty="35">
</local:MyClass>
```

Vous devriez désormais être capables de créer une classe personnalisée, de l’importer dans votre code XAML et de l’utiliser. Vous saurez également compléter votre classe en lui attribuant des propriétés. Enfin, vous devriez être en mesure d’implémenter des convertisseurs de type au début simple, et peut être plus complexes, en fonction de votre progression.

---

{{%attachments style="grey" /%}}
