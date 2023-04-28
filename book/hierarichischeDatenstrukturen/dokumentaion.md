---
name: Dokumentation Bäume
index: 5
---

# Baumklassen
Die folgenden Klassen BinaryTree und BinarySearchTree modellieren Binärbäume als nicht-lineare dynamische Datenstrukturen.

## Die generische Klasse BinaryTree
Mithilfe der generischen Klasse BinaryTree können beliebig viele Objekte vom Typ ContentType in einem Binärbaum verwaltet werden. Ein Objekt der Klasse stellt entweder einen leeren Baum dar oder verwaltet ein Inhaltsobjekt sowie einen linken und einen rechten Teilbaum, die ebenfalls Objekte der generischen Klasse BinaryTree sind.

### Dokumentation der Klasse BinaryTree<ContentType> BinaryTree()
**BinaryTree()**

Nach dem Aufruf des Konstruktors existiert ein leerer Binärbaum.

**BinaryTree(ContentType pContent)**

Wenn der Parameter pContent ungleich null ist, existiert nach dem Aufruf des Kon- struktors der Binärbaum und hat pContent als Inhaltsobjekt und zwei leere Teilbäume. Falls der Parameter null ist, wird ein leerer Binärbaum erzeugt.
Wenn der Parameter pContent ungleich null ist, wird ein Binärbaum mit pContent als Inhaltsobjekt und den beiden Teilbäume pLeftTree und pRightTree erzeugt. Sind pLeftTree oder pRightTree gleich null, wird der entsprechende Teilbaum als leerer Binärbaum eingefügt. Wenn der Parameter pContent gleich null ist, wird ein leerer Binärbaum erzeugt.

**boolean isEmpty()**

Diese Anfrage liefert den Wahrheitswert true, wenn der Binärbaum leer ist, sonst liefert sie den Wert false.
void setContent(ContentType pContent)
Wenn der Binärbaum leer ist, werden der Parameter pContent als Inhaltsobjekt sowie ein leerer linker und rechter Teilbaum eingefügt. Ist der Binärbaum nicht leer, wird das Inhaltsobjekt durch pContent ersetzt. Die Teilbäume werden nicht geändert. Wenn pContent null ist, bleibt der Binärbaum unverändert.

**ContentType getContent()**

Diese Anfrage liefert das Inhaltsobjekt des Binärbaums. Wenn der Binärbaum leer ist, wird null zurückgegeben.

**BinaryTree(ContentType pContent, BinaryTree<ContentType> pLeftTree, BinaryTree<ContentType> pRightTree)**

Wenn der Parameter pContent ungleich null ist, wird ein Binärbaum mit pContent als Inhaltsobjekt und den beiden Teilbäume pLeftTree und pRightTree erzeugt. Sind pLeftTree oder pRightTree gleich null, wird der entsprechende Teilbaum als leerer Binärbaum eingefügt. Wenn der Parameter pContent gleich null ist, wird ein leerer Binärbaum erzeugt.

**void setLeftTree(BinaryTree<ContentType> pTree)**

Wenn der Binärbaum leer ist, wird pTree nicht angehängt. Andernfalls erhält der Binärbaum den übergebenen Baum als linken Teilbaum. Falls der Parameter null ist, ändert sich nichts.

**void setRightTree(BinaryTree<ContentType> pTree)**

Wenn der Binärbaum leer ist, wird pTree nicht angehängt. Andernfalls erhält der Binärbaum den übergebenen Baum als rechten Teilbaum. Falls der Parameter null ist, ändert sich nichts.

**BinaryTree<ContentType> getLeftTree()**
Diese Anfrage liefert den linken Teilbaum des Binärbaumes. Der Binärbaum ändert sich nicht. Wenn der Binärbaum leer ist, wird null zurückgegeben.

**BinaryTree<ContentType> getRightTree()**

Diese Anfrage liefert den rechten Teilbaum des Binärbaumes. Der Binärbaum ändert sich nicht. Wenn der Binärbaum leer ist, wird null zurückgegeben.
  
## Die generische Klasse BinarySearchTree

Mithilfe der generischen Klasse BinarySearchTree können beliebig viele Objekte des Typs ContentType in einem Binärbaum (binärer Suchbaum) entsprechend einer Ordnungs- relation verwaltet werden.

Ein Objekt der Klasse BinarySearchTree stellt entweder einen leeren Baum dar oder verwaltet ein Inhaltsobjekt vom Typ ContentType sowie einen linken und einen rechten Teilbaum, die ebenfalls Objekte der Klasse BinarySearchTree sind.

Die Klasse der Objekte, die in dem Suchbaum verwaltet werden sollen, muss das generische Interface ComparableContent implementieren. Dabei muss durch Überschreiben der drei Vergleichsmethoden isLess, isEqual, isGreater (siehe Dokumentation dieses Interaces) eine eindeutige Ordnungsrelation festgelegt sein.

Beispiel einer Klasse, die das Interface ComparableContent implementiert: 

```java
public class Eintrag implements ComparableContent<Eintrag> {

private int wert; // weitere Attribute

public boolean isLess(Eintrag pEintrag) { 
    return this.gibWert() < pEintrag.gibWert();
}

public boolean isEqual(Eintrag pEintrag) { 
    return this.gibWert() == pEintrag.gibWert();
}

public boolean isGreater(Eintrag pEintrag) { 
    return this.gibWert() > pEintrag.gibWert();
}

public int gibWert() { 
    return this.wert;
}
  // weitere Methoden
}
``` 
Die Objekte der Klasse ContentType sind damit vollständig geordnet. Für je zwei Objekte c1 und c2 vom Typ ContentType gilt also insbesondere genau eine der drei Aussagen:

+ c1.isLess(c2)
+ c1.isEqual(c2)
+ c1.isGreater(c2)

(Sprechweise: c1 ist kleiner als c2) (Sprechweise: c1 ist gleichgroß wie c2) (Sprechweise: c1 ist größer als c2)
Alle Objekte im linken Teilbaum sind kleiner als das Inhaltsobjekt des Binärbaumes. Alle Objekte im rechten Teilbaum sind größer als das Inhaltsobjekt des Binärbaumes. Diese Bedingung gilt auch in beiden Teilbäumen.

### Dokumentation der Klasse BinarySearchTree<ContentType extends ComparableContent<ContentType>>

**BinarySearchTree()**

Der Konstruktor erzeugt einen leeren Suchbaum.

**boolean isEmpty()**
Diese Anfrage liefert den Wahrheitswert true, wenn der Suchbaum leer ist, sonst liefert sie den Wert false.

**void insert(ContentType pContent)**

Falls bereits ein Objekt in dem Suchbaum vorhanden ist, das gleichgroß ist wie pContent, passiert nichts. Andernfalls wird das Objekt pContent entsprechend der Ordnungsrelation in den Baum eingeordnet. Falls der Parameter null ist, ändert sich nichts.

**ContentType search(ContentType pContent)**
Falls ein Objekt im binären Suchbaum enthalten ist, das gleichgroß ist wie pContent, lie- fert die Anfrage dieses, ansonsten wird null zurückgegeben. Falls der Parameter null ist, wird null zurückgegeben.

**void remove(ContentType pContent)**

Falls ein Objekt im binären Suchbaum enthalten ist, das gleichgroß ist wie pContent, wird dieses entfernt. Falls der Parameter null ist, ändert sich nichts.

**ContentType getContent()**

Diese Anfrage liefert das Inhaltsobjekt des Suchbaumes. Wenn der Suchbaum leer ist, wird null zurückgegeben.

**BinarySearchTree<ContentType> getLeftTree()**

Diese Anfrage liefert den linken Teilbaum des binären Suchbaumes. Der binäre Suchbaum ändert sich nicht. Wenn er leer ist, wird null zurückgegeben.

**BinarySearchTree<ContentType> getRightTree()**

Diese Anfrage liefert den rechten Teilbaum des Suchbaumes. Der Suchbaum ändert sich nicht. Wenn er leer ist, wird null zurückgegeben.

### Das generische Interface ComparableContent<ContentType>

Das generische Interface ComparableContent muss von Klassen implementiert werden, deren Objekte in einen Suchbaum (BinarySearchTree) eingefügt werden sollen. Die Ord- nungsrelation wird in diesen Klassen durch Überschreiben der drei implizit abstrakten Methoden isGreater, isEqual und isLess festgelegt.

Das Interface ComparableContent gibt folgende implizit abstrakte Methoden vor:

**boolean isGreater(ContentType pComparableContent)**

Wenn festgestellt wird, dass das Objekt, von dem die Methode aufgerufen wird, bzgl. der gewünschten Ordnungsrelation größer als das Objekt pComparableContent ist, wird true geliefert. Sonst wird false geliefert.

**boolean isEqual(ContentType pComparableContent)**

Wenn festgestellt wird, dass das Objekt, von dem die Methode aufgerufen wird, bzgl. der gewünschten Ordnungsrelation gleich dem Objekt pComparableContent ist, wird true geliefert. Sonst wird false geliefert.

**boolean isLess(ContentType pComparableContent)**

Wenn festgestellt wird, dass das Objekt, von dem die Methode aufgerufen wird, bzgl. der gewünschten Ordnungsrelation kleiner als das Objekt pComparableContent ist, wird true geliefert. Sonst wird false geliefert.
