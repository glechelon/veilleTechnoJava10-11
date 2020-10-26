# Java 10 & Java 11

## Java 10

### Inférence de type

* Avec le mot clé `var` c'est le compilateur qui déduit le type de la variable.
* Permet: 
  * Permet d'éviter la répétion:
  
```java
 //Sans inférence de type
 ThisIsAVeryLongJavaClassName obj = new ThisIsAVeryLongJavaClassName();
 
 //Avec inférence de type
 var obj = new ThisIsAVeryLongJavaClassName();
 
```
  
  * d'être moins verbeux qaund le type est déjà clair:
  
```java
 //Sans inférence de type
 String myString = "this is a string";
 
 //Avec inférence de type
var myString = "this is a string";
```

* Limitations:
  * Ne pas utiliser si le type n'est pas évident car sinon perte en clarté:
  
  ```java
  
  var result = obj.processData(in); //Il est difficile ici de déduire le type de result
  
  ```
* Le mot clé `var` ne veut pas dire que c'est dynamique, le type est toujours présent mais c'est le compilateur qui déduit.

* Ce n'est pas la prmière apparition de l'inférence de type en java. Elle était déjà présent à travers la déclaration des listes et les lambdas:

```java
List<String> myList = new ArrayList<>(); //Le type de l'ArrayList est déduit par le compilateur

List<Integer> mySecondList = List.of(1, 2, 3);
mySecondList.stream().map(i -> i + 2).collect(Collectors.toList()); //Le type de i est déduit par le compilateur

```

* A la création d'une liste, il faut qu'au moins un des côtés déclare le type sinon par défaut on se retrouve avec une liste d'objets:

```java
var myList = new ArrayList<>(); // => List<Object> 
```

* Fonctionne uniquement pour les variables locales. Ne fonctionne par pour les attributs des classes ou les paramétres des méthodes.

* Avec le mot clé `var` on ne peut pas initialiser de variable à `null`.


### Performances

* **G1GC** (garbage collector) : Fonctionnement en parallèle au leiu de séquentiel.

* **Class data sharing**: Permet de partager des classes communes entre plusieurs instances de JVM. Ce qui peut avoir pour effet de réduire le temps de démarrage de la JVM.

## Java 11

### Scripting 

* Il est possible de lancer des fichiers `.java` directement sans avoir besoin de les compiler au préalable:

```bash

java Main.Java

```

* Il est possible de faire des scripts java:
 * Ajouter le header : `#! /usr/bin/java --source 11`.
 * Le fichier n'a pas besoin d'extension: `myScript` :
 
 ```java
 #! /usr/bin/java --source 11
 public class Script {

	public static void main(String[] args) {
		System.out.println("I'm a script");
	}

}
 ```
 
 * Pour lancer le script: `./myScript`. 
