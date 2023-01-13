---
name: List 2.0 Modellierung
index: 1
toc: show
---

# List

Eine Liste (englisch: **list**) ist ein Datenstrukturtyp der es ermöglicht, eine Sammlung von Elementen zu speichern und zu verwalten. Eine Liste ist ein dynamisches Datenstruktur, das heißt, dass ihre Größe und ihr Inhalt sich während der Laufzeit eines Programms ändern können.

In der Regel können in einer Liste Elemente unterschiedlicher Typen gespeichert werden, beispielsweise Zahlen, Zeichenketten oder andere Objekte.

Um Elemente in einer Liste zu speichern und zu verwalten, werden in der Regel mehrere Methoden bereitgestellt, wie beispielsweise **add()** oder **remove()** zum Hinzufügen oder Entfernen von Elementen, **get()** oder **set()** zum Abrufen oder Ändern von Elementen an bestimmten Indizes und viele andere.

::::tabs{id="List"}

:::tab{title="Video Liste" id="Video Liste"}
::youtube[02 Lineare Datenstrukturen:  List ohne Knoten ]{#zSad1XVQ0hg}
:::

:::
:::tab{title="Quellcode List" id="Quellcode List"}
:::tab{title="Java List" id="Java List"}
```java
public class List
{
    /**
       The first element
       */
    private Node fe;
    /**
       The searched element
       */
    private Node se;
    /**
       The last element
       */
    private Node le;
    
    public List(Node i){
        fe = i;
        le = i;
    }
    /**
    *Adds a node to the end of the list
    */
    public void f(Node i){
        le.setN(i);
        le = le.getN();
    }
    /**
    * Return the node at pos p
    */
    public Node g(int p){
        e(p);
        return se;
    }
    /**
    * Change the element at the given position p
    */
    public void s(Node i, int p){
        e(p);
        i.setN(se.getN());
        r(p);
        a(i, p);
    }
    /**
    * Add the element at the position p
    */
    public void a(Node i, int p){
        e(p);
        i.setN(se);
        Node tmp = se;
        e(p - 1);
        se.setN(i);
    }
    /**
    * Removes the element at position p
    */
    public void r(int p){
        e(p + 1);
        Node temp = se;
        e(p - 1);
        se.setN(temp);
    }
    /**
     * Sets se to the element that is searched
     */
    private void e(int p){
        Node i = fe;
        for(int j = 0; j < p; j++){
            i = i.getN();
        }
        se = i;
    }
}

public class Elephant{
    
    /**
       The name
       */
    private String n;
    
    public Elephant(String n){
        this.n = n;
    }
    /**
     * Returns the name
     */
    public String getN(){
        return n;
    }
    /**
     * Sets the name
     */
    public void setN(String n){
        this.n = n;
    }
}

public class Node<T> {

    /**
       The item
       */
    private final T i;
    
    /**
       The node
       */
    private Node n;
    
    /**
       Given i, the item
       */
    public Node(T i) {
        this.i = i;
    }
    
    /**
       Returns the node
       */
    public Node getN() {
        return n;
    }
    
    /**
       Sets the node
       */
    public void setN(Node n) {
        this.n = n;
    }
    
    /**
       Returns the item
       */
    public T getI() {
        return i;
    }
}
```

:::
::::
