---
title: UGEoverFlow
publishDate: 2023-04-04 00:00:00
img: /assets/stock-4.jpg
img_alt: Soft pink and baby blue water ripples together in a subtle texture.
description: |
  Collection en Java
tags:
  - Java

---

>### Collections


 

Java propose des collections pour simplifier la gestion et le stockage de données. Deux interfaces largement utilisées sont la List et la Map.

#### List et Map
##### List

La List est une interface qui définit une liste d'éléments. Elle est indexée par des entiers et maintient l'ordre d'insertion. Cela signifie que les éléments sont stockés dans l'ordre où ils ont été ajoutés. Par exemple :

```java

    List<String> liste = new ArrayList<>();
    liste.add("Premier élément");
    liste.add("Deuxième élément");
    //
```
Dans cet exemple, la liste conserve l'ordre d'insertion des éléments.
##### Map

La Map est une autre interface puissante qui définit un dictionnaire de couples clé/valeur. Dans une Map, les éléments sont indexés par une clé unique. Chaque clé est associée à une valeur. Par exemple :

```java
    
    Map<String, Integer> map = new HashMap<>();
    map.put("Clé 1", 10);
    map.put("Clé 2", 20);
    //

```
Dans cet exemple, chaque clé est associée à une valeur.
Contraintes Importantes

Pour que les collections fonctionnent correctement, il est essentiel que les éléments d'une List ou les clés/valeurs d'une Map implémentent les méthodes equals(Object), hashCode(), et toString(). Par exemple :

```java
    
    class MonElement {
        private String nom;
    
        public MonElement(String nom) {
            this.nom = nom;
        }
    
        @Override
        public boolean equals(Object obj) {
            if (this == obj) return true;
            if (obj == null || getClass() != obj.getClass()) return false;
            MonElement that = (MonElement) obj;
            return Objects.equals(nom, that.nom);
        }
    
        @Override
        public int hashCode() {
            return Objects.hash(nom);
        }
    
        @Override
        public String toString() {
            return nom;
        }
    }
//
```
Il est important de noter que Java ne générera ni avertissements ni erreurs si vous oubliez de mettre en œuvre ces méthodes, il est donc de votre responsabilité de vous assurer qu'elles sont correctement définies pour vos éléments.

#### java.util.List

##### ArrayList VS List.of()

Il y a 2 implantations principales
– List.of() pour les listes non modifiables
 ```java

    var list = List.of("hello", "collection");
//
```
– ArrayList qui s’agrandit dynamiquement
```java
    var list = new ArrayList<String>();
    list.add("hello");
    list.add("collection");
//
```
###### ArrayList
En Java, java.util.ArrayList est une classe qui permet de créer des listes modifiables et extensibles dynamiquement. Cela signifie que vous pouvez ajouter et supprimer des éléments de la liste, et la liste s'agrandira automatiquement pour s'adapter à vos besoins.

Pour créer une liste vide, vous pouvez utiliser la syntaxe suivante :

```java

    var list = new ArrayList<String>(); // Vous devez indiquer le type de la liste

    //add
    list.add("hello");
    list.add("list");

    //ArrayList accepte null
    list.add(null);     // ok, mais à ne pas faire en pratique !

    //Modifier et Supprimer des Éléments
    list.set(index, element);   // Change la valeur de l'élément à la nième position
    var list = Arrays.asList("hello");
    list.set(0, "bonjour");
    list.get(0)                 // bonjour
    //

```

Pour supprimer un élément, vous pouvez utiliser remove de deux manières différentes :

remove(element) : Supprime le premier élément correspondant à la valeur spécifiée.
remove(index) : Supprime l'élément à la position indiquée et décale les éléments restants vers la gauche.

###### List.of()

Liste non modifiable qui n’accepte pas null les méthodes set(), add() et remove(index)/remove(element) lèvent UnsupportedOperationException
List.of(E...)
List.of() est non modifiable :
– List.of("hello").set(0, "list")     // lève UnsupportedOperationException
– List.of("hello").add("list")        // lève UOE
– List.of("hello").remove("hello")    // lève UOE
– List.of("hello").remove(0)          // lève UOE
```java

    var empty = List.<String>of(); // on doit indiquer le type
    var one = List.of(42);
    var three = List.of(1, 5, 8);
//
```
Non modifiable <-> Modifiable
```

    List.copyOf(collection)
    Prend une collection en paramètre et copie tous les élements dans une List non modifiable (la même que List.of())
    new ArrayList<>(collection)
    Prend une collection en paramètre et copie tous les élements dans une ArrayList (modifiable)
```

List.of() avec un tableau d’objets, copie les valeurs 

```java

    var array = new String[] { "hello", "collection" };
    var list = List.of(array);
//
```
**List.isEmpty()/size()/get()**
```java
    
    // list.isEmpty() renvoie true si la liste est vide
    List.of("hello").isEmpty() // false
    // list.size() renvoie le nombre d’élements
    List.of("hello").size() // 1
    // list.get(index) renvoie le n-ième élement (à partir de 0)
    List.of("hello", "list").get(0) // hello
//
```
**Lève une exception IndexOutOfBoundsException si on sort des bornes de la liste**

**toString()/equals()/hashCode()**
```java

    // list.toString() renvoie une version textuelle
    List.of(1, 2, 3).toString() // [1, 2, 3]
    // list.equals(list2) permet de comparer des listes même si ce n’est pas la même implantation
    var list = List.of(1, 2, 3);
    list.equals(list) // true
    // list.hashCode() renvoie une valeur résumée du contenu de la liste
    List.of(1, 2, 3).hashCode() // 30817
//
```
**contains()/indexOf()/lastIndexOf()**
List.contains(element) renvoie si l’élement est contenu (en utilisant element.equals())
```java

    List.of("foo", "bar").contains("bar") // true
//
```
list.indexOf(element) renvoie l’index du premier élément égal (en utilisant element.equals()) ou -1
```java

    List.of("foo", "foo").indexOf("foo") // 0
//
```

list.lastIndexOf(element) renvoie l’index du dernier élément égal (en utilisant element.equals()) ou -1
```java

    List.of("foo", "foo").lastIndexOf("foo") // 1
//
```


**Parcours avec for(:)**
On peut utiliser la syntaxe for(:) sur les listes
```java

    var list = List.of(1, 2, 3);
    for(var element: list) {
    System.out.println(element);
    } // 1
    // 2
    // 3
//
```
C’est la même syntaxe que pour les tableaux mais le code généré par le compilateur n’utilisepas des indices mais un Iterator.
