---
name: List 2.0
index: 1
toc: show
---

# List

Eine Liste (englisch: **list**) ist ein Datenstrukturtyp der es ermöglicht, eine Sammlung von Elementen zu speichern und zu verwalten. Eine Liste ist ein dynamisches Datenstruktur, das heißt, dass ihre Größe und ihr Inhalt sich während der Laufzeit eines Programms ändern können.

In der Regel können in einer Liste Elemente unterschiedlicher Typen gespeichert werden, beispielsweise Zahlen, Zeichenketten oder andere Objekte.

Um Elemente in einer Liste zu speichern und zu verwalten, werden in der Regel mehrere Methoden bereitgestellt, wie beispielsweise **add()** oder **remove()** zum Hinzufügen oder Entfernen von Elementen, **get()** oder **set()** zum Abrufen oder Ändern von Elementen an bestimmten Indizes und viele andere.

::::tabs

:::tab{title="Video ohne Knoten"}
::youtube[02 Lineare Datenstrukturen:  List ohne Knoten ]{#zSad1XVQ0hg}
:::

:::tab{title="Struktogramm ohne Knoten"}
::struktog{data="https://struktog.openpatch.org/#pako:eNqVVMuOEzEQ_JXIp0VKI7ffjsQRJC65wA1xsNttEjF5KJnVgqL8O71iN8siJTBzsdzdLlfVlHxSm13jQS1Oat3UQgWtsza2gEHvIUZmaM0ReDI2murVXI0_9yyTH7dHPoxLOS21vhuG3cP7gTe8HV_AggsZmwakEkBrrBBMJdmir4HSC9iH-y2N6932CW7kH4KiSmsCuV8VwZyrfTmUDY98OKrFl5Pa72RV-ndjKR3ZPU_P9pdz5_nzqH01un6ckvr56zX2NlisrXTh7BAipQYaEwN2a4mS-T8rtvfDcJ4rWq2HdoFOOcXqqoeigxXAlEHsbVCr0diYJ7msQ0WHqYIxSRC9D4KTCWI2BVvFF7DP5fj9tcNHHj9xOdCK25248ebqJS12w60xUBL8XrsHDBzAR64xWprEmDCIzqQh15aAqmbwtiBgicaHXm4xvvzZt8J9KbW745OAp1uua3DIhUwyEL3QT0Z3aDFZMOS7y2aahpqLo14d6CqGWKMz-NQL2BJr9RRvabjEdNzsZ-9mfwm4bhsj6Zo7dDIR0IYGLhWCQtGEnvUk_ugNRxtY1JcEmJqDmkKVRGbrW6gTUjODGd5Ijg5RO3LAPVcgSTe4niOYji42PS3rTV4k7STcGMVwF6hAb6E8IrpE_8r6K5sv-bkk6roGecRKK5hBwq_B--ggeC6AjmJPkSY8BX9-c7Xi9beVtIxzc_WwbuNKLVKO519eXbtd"}
:::

:::tab{title="Quellcode ohne Knoten" }
```java
public class List
{
    private Elephant firstElement;
    private Elephant searchedElement;
    private Elephant lastElement;
    /**
     * Konstruktor
     */
    public List(Elephant pElephant){
        firstElement = pElephant;
        lastElement = pElephant;
    }
    /**
    *Füge ein Element am Ende der Liste hinzu
    *@param Elephant pElephant
    */
    public void append(Elephant pElephant){
        lastElement.setNext(pElephant);
        lastElement = lastElement.getNext();
    }
    /**
    * Erhalte den Wert von einem Element an einer pestimten Position
    * @param int pos
    * @return Elephant searchedElement
    */
    public Elephant get(int pos){
        setSearched(pos);
        return searchedElement;
    }
    /**
    * Ändere das Element an einer bestimten Position
    * @param Elephant pElephant
    * @param int pos
    */
    public void set(Elephant pElephant, int pos){
        setSearched(pos);
        pElephant.setNext(searchedElement.getNext());
        remove(pos);
        add(pElephant, pos);
    }
    /**
    * Füge ein Element an einer bestimmten Position in der Liste hinzu
    * @param Elephant pElephant
    * @param int pos
    */
    public void add(Elephant pElephant, int pos){
        setSearched(pos);
        pElephant.setNext(searchedElement);
        Elephant tmp = searchedElement;
        setSearched(pos - 1);
        searchedElement.setNext(pElephant);
    }
    /**
    * Entfernt ein Element an einer bestimmten Position in der Liste
    * @param int pos
    */
    public void remove(int pos){
        setSearched(pos + 1);
        Elephant tmp = searchedElement;
        setSearched(pos - 1);
        searchedElement.setNext(tmp);
    }
    /**
     * interne Funktion die ein gesuchtes Element in einer Methodenübergreifenden Variable
     */
    private void setSearched(int pos){
        Elephant ele = firstElement;
        for(int i = 0; i < pos; i++){
            ele = ele.getNext();
        }
        searchedElement = ele;
    }
}```

:::

:::tab{title="Quellcode mit Knoten"}
```java
public class List<E> {

    private Node<E> firstElement;
    private Node<E> searchedElement;
    private Node<E> lastElement;

    /**
     * Erstellt eine leere liste
     * */
    public List() {}

    /**
     * Erstellt eine neue liste und setzt das element "item" an die erste und letzte stelle
     */
    public List(E item) {
        Node<E> node = new Node<>(item);
        firstElement = node;
        lastElement = node;
    }

    /**
     * Fügt ein element ans ende der liste hinzu
     */
    public void append(E item) {
        Node<E> node = new Node<>(item);
        if(lastElement == null) {
            firstElement = node;
            lastElement = node;
        } else {
            lastElement.setNextNode(node);
            lastElement = lastElement.getNextNode();
        }
    }

    /**
     * Gibt das element zurück, welches an der position "index" gespeichert ist
     */
    public E get(int index) {
        if(index == 0)
            return firstElement.getItem();
        setSearched(index);
        return searchedElement.getItem();
    }

    /**
     * Ersetze das Element an der position "pos" durch das neue element "item"
     */
    public void set(E item, int pos) {
        Node<E> node = new Node<>(item);
        setSearched(pos);
        node.setNextNode(searchedElement.getNextNode());
        remove(pos);
        add_intern(node, pos);
    }

    /**
     * Eine Hilfsmethode, wird in "set(E item, int pos)" benötigt
     * */
    private void add_intern(Node<E> item, int pos) {
        setSearched(pos);
        item.setNextNode(searchedElement);
        setSearched(pos - 1);
        searchedElement.setNextNode(item);
    }

    /**
     * Fügt das element "item" an der position "pos" der liste hinzu
     */
    /*
    * Bsp:
    * A -> B -> C
    * add(F, 1)
    * A -> F -> B -> C
    * */
    public void add(E item, int pos) {
        Node<E> node = new Node<>(item);
        if(pos == 0) {
            node.setNextNode(firstElement);
            firstElement = node;
        } else if(pos == getSize()) {
            append(item);
        } else {
            setSearched(pos);
            node.setNextNode(searchedElement);
            setSearched(pos - 1);
            searchedElement.setNextNode(node);
        }
    }

    /**
     * Entfernt das element an der position "pos"
     */
    /*
    * Bsp:
    * A -> B -> C
    * remove(1)
    * A -> C
    * */
    public void remove(int pos) {
        setSearched(pos + 1);
        Node<E> temp = searchedElement;
        setSearched(pos - 1);
        searchedElement.setNextNode(temp);
    }

    /**
     * Interne methode, welche das "searchedElement" setzt
     */
    private void setSearched(int pos) {
        if(pos > getSize())
            throw new IndexOutOfBoundsException();
        Node<E> item = firstElement;
        for (int i = 0; i < pos; i++) {
            item = item.getNextNode();
        }
        searchedElement = item;
    }

    public int getSize() {
        int size = 0;
        Node<E> temp = firstElement;
        while (temp != null) {
            temp = temp.getNextNode();
            size++;
        }
        return size;
    }
}

public class Node<T> {

    private final T item;

    private Node<T> nextNode;

    public Node(T item) {
        this.item = item;
    }

    public Node<T> getNextNode() {
        return nextNode;
    }

    public void setNextNode(Node<T> nextNode) {
        this.nextNode = nextNode;
    }

    public T getItem() {
        return item;
    }
}
```
:::
:::tab{title="Dokumentation mit Knoten"}
**void append(E item)**
Erstellt für das item einen Knoten und fügt diesen an das Ende der Liste hinzu

**E get(int index)**
Gibt das Element an der Position des "index" zurück

**void set(E item, int pos)**
Erstellt für das item einen Knoten und ersetzt das Element an der Position pos

**void add(E item, int pos)**
Erstellt für das item einen Knoten und fügt diesen an der Position in der Liste ein

**void remove(int pos)**
Entfernt das Element an der Position "pos" von der Liste

**int getSize()**
Gibt die Größe der Liste zurück
:::
::::
