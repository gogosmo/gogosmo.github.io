---
title: POO en Java
publishDate: 2023-04-04 00:00:00
img: /assets/stock-4.jpg
img_alt: Soft pink and baby blue water ripples together in a subtle texture.
description: |
  Découvrez les principes fondamentaux de la programmation orientée objet en Java.

tags:
  - Java
  - POO
  - Programmation
---

La programmation orientée objet (POO) est un paradigme de programmation puissant qui permet de concevoir des applications modulaires et flexibles. Dans cet article, nous explorerons les bases de la POO en Java et ses concepts clés.

#### 1. Java est un langage compilé ?

Avant de plonger dans la POO en Java, vous vous demandez peut-être si Java est un langage compilé ? Oui, Java est un langage compilé. Cela signifie que le code source Java est d'abord compilé en bytecode, qui est ensuite exécuté par la machine virtuelle Java (JVM).
Lorsque vous écrivez du code Java, vous créez un fichier source avec l'extension ".java". Ce code source est ensuite compilé en bytecode à l'aide du compilateur Java ("javac"). Le bytecode peut être exécuté sur n'importe quelle machine équipée d'une JVM, ce qui permet la portabilité des applications Java.

#### 2. Qu'est-ce que le paradigme objet en Java ?

Le paradigme objet en Java repose sur la création d'objets, d'instances de classes, et l'interaction entre ces objets pour résoudre des problèmes. Il met l'accent sur la réutilisation de code et la modélisation du monde réel en utilisant des classes et des objets.
En POO, un programme est constitué d'objets qui ont des attributs (variables) et des méthodes (fonctions). Les objets interagissent en s'envoyant des messages, ce qui permet de modéliser des relations complexes entre les entités du problème que vous résolvez.

#### 3. Les Principes de l'Orienté Objet

##### 3.1 L'Encapsulation

L'encapsulation est un concept essentiel en programmation orientée objet (POO) qui consiste à regrouper les données (variables) et les fonctions (méthodes) qui les manipulent dans une seule unité appelée "classe". Cette unité protège les données en les rendant privées et permet de contrôler leur accès depuis l'extérieur de la classe.

En Java, cela signifie que vous créez une classe pour définir la structure des objets que vous souhaitez créer. À l'intérieur de cette classe, vous définissez des variables (attributs) pour stocker les données de l'objet, ainsi que des méthodes pour effectuer des opérations sur ces données.

##### 3.2 La Délégation

La délégation est un autre concept important de la programmation orientée objet (POO) qui permet de créer de nouveaux objets en composant avec des objets déjà existants. En Java, cela se fait en utilisant la relation "a un" (ou composition), où un objet contient un autre objet pour lui déléguer certaines tâches.

Supposons que vous ayez une classe "Voiture" et une classe "Moteur". Plutôt que d'intégrer le code de gestion du moteur directement dans la classe "Voiture", vous pouvez déléguer la gestion du moteur à une instance de la classe "Moteur". 
```java
    public class Moteur {
        private boolean allume;
    
        public Moteur() {
            this.allume = false;
        }
    
        public void demarrer() {
            allume = true;
            System.out.println("Le moteur démarre.");
        }
    
        public void arreter() {
            allume = false;
            System.out.println("Le moteur s'arrête.");
        }
    }
    
    public class Voiture {
        private String modele;
        private Moteur moteur; // Délégation à la classe Moteur
    
        public Voiture(String modele) {
            this.modele = modele;
            this.moteur = new Moteur(); // Création d'une instance de Moteur
        }
    
        public void demarrer() {
            moteur.demarrer(); // Délégation de la commande au moteur
        }
    
        public void arreter() {
            moteur.arreter(); // Délégation de la commande au moteur
        }
    }

```

##### 3.3 L'Héritage

L'héritage est l'un des concepts clés de la programmation orientée objet (POO) qui permet à une classe d'hériter des caractéristiques (attributs et méthodes) d'une autre classe appelée "classe parente" ou "classe de base". En Java, cela se fait en créant une nouvelle classe (classe dérivée ou sous-classe) qui hérite des propriétés d'une classe existante (classe de base).

```java

    public class Animal {
        private String nom;
        private int age;
    
        public Animal(String nom, int age) {
            this.nom = nom;
            this.age = age;
        }
    
        public void manger() {
            System.out.println("L'animal mange.");
        }
    
        public void dormir() {
            System.out.println("L'animal dort.");
        }
    }
    
    public class Chien extends Animal {
        public Chien(String nom, int age) {
            super(nom, age); // Appel du constructeur de la classe parente (Animal)
        }
    
        public void aboyer() {
            System.out.println("Le chien aboie.");
        }
    }
    
    public class Chat extends Animal {
        public Chat(String nom, int age) {
            super(nom, age); // Appel du constructeur de la classe parente (Animal)
        }
    
        public void miauler() {
            System.out.println("Le chat miaule.");
        }
    }

```

##### 3.4 Le Polymorphisme Objet

Le polymorphisme est un concept puissant de la programmation orientée objet (POO) qui permet à un objet de posséder plusieurs types. Cela signifie qu'un même nom de méthode peut être utilisé pour effectuer différentes actions en fonction du type de l'objet sur lequel elle est appelée. En d'autres termes, une même méthode peut avoir différents comportements en fonction du contexte.

```java

    public abstract class Forme {
        public abstract double calculerAire(); // Méthode abstraite, doit être redéfinie dans les sous-classes
    }
    
    public class Cercle extends Forme {
        private double rayon;
    
        public Cercle(double rayon) {
            this.rayon = rayon;
        }
    
        @Override // pour la surcharge de la methode
        public double calculerAire() {
            return Math.PI * rayon * rayon;
        }
    }
    
    public class Rectangle extends Forme {
        private double longueur;
        private double largeur;
    
        public Rectangle(double longueur, double largeur) {
            this.longueur = longueur;
            this.largeur = largeur;
        }
    
        @Override
        public double calculerAire() {
            return longueur * largeur;
        }
    }

```
