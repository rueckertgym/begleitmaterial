---
name: List Modellierung
index: 1
toc: show
---

# Schülereigene Modellierung

Eine Liste (englisch: **list**) ist ein Datenstrukturtyp, der es ermöglicht, eine Sammlung von Elementen zu speichern und zu verwalten. Eine Liste ist ein dynamisches Datenstruktur, das heißt, dass ihre Größe und ihr Inhalt sich während der Laufzeit eines Programms ändern können.

In der Regel können in einer Liste Elemente unterschiedlicher Typen gespeichert werden, beispielsweise Zahlen, Zeichenketten oder andere Objekte, wobei man sich vorher auf einen Datentyp festlegen muß.

Um Elemente in einer Liste zu speichern und zu verwalten, werden in der Regel mehrere Methoden bereitgestellt, wie beispielsweise **add()** oder **remove()** zum Hinzufügen oder Entfernen von Elementen, **get()** oder **set()** zum Abrufen oder Ändern von Elementen an bestimmten Indizes und viele andere.

::::tabs


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

# Zentralabiturklasse List des Landes NRW
## Die generische Klasse List
Objekte der generischen Klasse List verwalten beliebig viele, linear angeordnete Objekte vom Typ ContentType. Auf höchstens eins der verwalteten Objekte, aktuelles Objekt ge- nannt, kann jeweils zugegriffen werden. Wenn eine Liste leer ist, vollständig durchlaufen wurde oder das aktuelle Objekt am Ende der Liste gelöscht wurde, gibt es kein aktuelles Objekt. Das erste oder das letzte Objekt einer Liste können durch einen Auftrag zum aktuellen Objekt gemacht werden. Außerdem kann das dem aktuellen Objekt folgende Listenobjekt zum neuen aktuellen Objekt werden.
Das aktuelle Objekt kann gelesen, verändert oder gelöscht werden. Außerdem kann vor dem aktuellen Objekt ein Listenobjekt eingefügt werden.

### Dokumentation der Klasse List<ContentType> List()
Eine leere Liste wird erzeugt.

**boolean isEmpty()**

Die Anfrage liefert den Wert true, wenn die Liste keine Objekte enthält, sonst liefert sie den Wert false.

**boolean hasAccess()**

Die Anfrage liefert den Wert true, wenn es ein aktuelles Objekt gibt, sonst liefert sie den Wert false.

**void next()**

Falls die Liste nicht leer ist, es ein aktuelles Objekt gibt und dieses nicht das letzte Objekt der Liste ist, wird das dem aktuellen Objekt in der Liste folgende Objekt zum aktuellen Ob- jekt, andernfalls gibt es nach Ausführung des Auftrags kein aktuelles Objekt, d.h. hasAccess() liefert den Wert false.

**void toFirst()**

Falls die Liste nicht leer ist, wird das erste Objekt der Liste aktuelles Objekt. Ist die Liste leer, geschieht nichts.

**void toLast()**

Falls die Liste nicht leer ist, wird das letzte Objekt der Liste aktuelles Objekt. Ist die Liste leer, geschieht nichts.

**ContentType getContent()**

Falls es ein aktuelles Objekt gibt (hasAccess() == true), wird das aktuelle Objekt zu- rückgegeben. Andernfalls (hasAccess() == false) gibt die Anfrage den Wert null zurück.

**void setContent(ContentType pContent)**

Falls es ein aktuelles Objekt gibt (hasAccess() == true) und pContent ungleich null ist, wird das aktuelle Objekt durch pContent ersetzt. Sonst bleibt die Liste unverändert.

**void append(ContentType pContent)**

Ein neues Objekt pContent wird am Ende der Liste eingefügt. Das aktuelle Objekt bleibt unverändert. Wenn die Liste leer ist, wird das Objekt pContent in die Liste eingefügt und es gibt weiterhin kein aktuelles Objekt (hasAccess() == false). Falls pContent gleich null ist, bleibt die Liste unverändert.

**void insert(ContentType pContent)**

Falls es ein aktuelles Objekt gibt (hasAccess() == true), wird ein neues Objekt pContent vor dem aktuellen Objekt in die Liste eingefügt. Das aktuelle Objekt bleibt un- verändert. Falls die Liste leer ist und es somit kein aktuelles Objekt gibt (hasAccess() == false), wird pContent in die Liste eingefügt und es gibt weiterhin kein aktuelles Objekt. Falls es kein aktuelles Objekt gibt (hasAccess() == false) und die Liste nicht leer ist oder pContent == null ist, bleibt die Liste unverändert.

**void concat(List<ContentType> pList)**

Die Liste pList wird an die Liste angehängt. Anschließend wird pList eine leere Liste. Das aktuelle Objekt bleibt unverändert. Falls es sich bei der Liste und pList um dasselbe Objekt handelt, pList == null oder eine leere Liste ist, bleibt die Liste unverändert.

**void remove()**

Falls es ein aktuelles Objekt gibt (hasAccess() == true), wird das aktuelle Objekt ge- löscht und das Objekt hinter dem gelöschten Objekt wird zum aktuellen Objekt. Wird das Objekt, das am Ende der Liste steht, gelöscht, gibt es kein aktuelles Objekt mehr (hasAccess() == false). Wenn die Liste leer ist oder es kein aktuelles Objekt gibt (hasAccess() == false), bleibt die Liste unverändert.

