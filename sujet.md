# Static analysis

## Instructions

Some of the exercises in this practical session use PMD, JavaParser or require a full project as input.

To obtain and use PMD, consult the instructions given in https://pmd.github.io/pmd/pmd_userdocs_installation.html

The folder [javaparser-starter](code/javaparser-starter) contains the code of an application that uses JavaParser to print all public classes and public methods from a given project. You can use this example as a starting point for all exercises using JavaParser.

We recommend you use the following projects as input for the exercises:

- [Apache Commons Collections](https://github.com/apache/commons-collections)
- [Apache Commons CLI](https://github.com/apache/commons-cli)
- [Apache Commons Math](https://github.com/apache/commons-math)
- [Apache Commons Lang](https://github.com/apache/commons-lang)

Feel free to use any other project you want.

## Exercises

1. [TCC *vs* LCC](exercises/tcc-vs-lcc.md)

2. [Using PMD](exercises/using-pmd.md)

3. [Extending PMD](exercises/extending-pmd.md)

4. [No getter!](exercises/no-getter.md)

5. [Cyclomatic Complexity with JavaParser](exercises/jp-cc.md) 

6. [Class cohesion with JavaParser](exercises/jp-tcc.md) (bonus)


Exercice 1

Soit M et N deux méthodes .
Dans le contexte de LCC et TCC, M et N sont liés directement si et seulement si il existe au mions une instance de variable commune aux deux . 
Pour que TCC et LCC soient égaux, Il faut que pour tout couple de méthodes M et N du graphes, il existe une liaision directe entre ces deux méthodes.

Exemple :

public class Person{
    private String name;

    public Person(String name){
        this.name = name;
    }

    public getName(){
        return this.name;
    }

    public setName(String name){
        this.name = name;
    }
}


C'est impossible que LCC soit inférieur à TCC .
Supposons que LCC soient supérieur à TCC
Soit a le nombre de liaison directe , b le nombre de liasion indirecte et c le nombre total de couple de méthode du graphe
LCC < TCC <=> (a+b/c)  < a/c <=> a+b < a <=> b < 0 ce qui est absurde car b >= 0 
Donc LCC ne peut pas être inférieur à TCC.