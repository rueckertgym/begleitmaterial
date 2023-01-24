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

:::tab{title="Video Liste"}
::youtube[02 Lineare Datenstrukturen:  List ohne Knoten ]{#zSad1XVQ0hg}
:::

:::
:::tab{title="Java List"}
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
:::tab{title="Dokumentation List"}
**void f(Node i)**
Fügt den Knoten "i" ans Ende der Liste hinzu und setzt den pointer "le" auf den Knoten
**Node g(int pos)**
Gibt den Knoten an der Position pos zurück
**void s(Node i, int p)**
asd
:::
::::
