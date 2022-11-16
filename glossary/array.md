---
name: Arrays in Java
index: 0
toc: show
---
# Arrays
Arrays (Felder) benutzt man, um eine vorher bestimme Anzahl Daten eines einzelnen Datentyps (zum Beispiel Zahlen) zu speichern und auf diese über eine Indizierung zugreifen zu können. 
Man kann sich ein Array wie eine Kommode (mit einem Namen) und einer durchnummerierten, festen Anzahl Schubfächer vorstellen. Die Nummerierung beginnt bei 0. Jedes Schubfach ist ein gewöhnlicher Speicher, jedoch darf man in dieser Kommode nur Dinge gleicher Art (gleichen Typs) aufbewahren. Über den Namen der Kommode und die Nummer des Faches gelangt man direkt an den Speicher (siehe Abb. rechts ). 
Der Zugriff auf die Elemente eines Arrays erfolgt also mittels Arraynamen, sowie einem Index am Ende in eckigen Klammern. 
![Array](/Bilder/01_SuchenUndSortieren/chest_of_drawers_array.gif "Array")
Quelle: http://www.problem-hilfe.de/linux/images/chest_of_drawers_array.gif

## Arrays in Java 
### Array-Variablen deklarieren
Durch `int [] zahlenspeicher` wird eine Array-Variable deklariert. Das syntaktische Erkennungsmerkmal bei der Deklaration einer Array-Variablen sind eckige Klammern als Teil des Typnamens: `int[]`. 
Dies besagt, dass die Variable `zahlenspeicher` vom Typ Array (Feld) von Ganzzahlen ist. Man sagt, dass `int` der Basistyp dieses speziellen Feldes (Arrays) ist. Die Deklaration einer Array-Variablen sollte nicht mit der sehr ähnlich aussehenden Deklaration einer einfachen Variablen verwechselt werden:

`int zahl;`

`int[] zahlenspeicher;`

Die Variable `zahl` kann den Wert einer einzelnen ganzen Zahl speichern, während `zahlenspeicher` „nur“ die Adresse auf ein Array-Objekt wird, sobald dieses erzeugt ist. Allein durch die oben geschehene Deklaration ist noch kein Objekt erzeugt werden, sondern dies – das wissen wir schon – geschieht erst durch die new-Anweisung (wie bei anderen Objekten auch).

### Array-Objekte erzeugen
Der nächste Schritt muss nun sein, eine Array-Variable mit einem Array-Objekt zu verknüpfen – so, wie immer schon unsere Variablen mit Objekten verknüpft wurden. Dies geschieht mit der new-Anweisung:
`zahlenspeicher = new int[24]`
Obige Zeile erzeugt nun ein Array-Objekt, in dem 24 unterschiedliche int-Werte gespeichert werden können, und lässt die Array-Variable zahlenspeicher darauf verweisen. Folgende Grafik veranschaulicht die Situation:

![Array 24 Werte](/Bilder/01_SuchenUndSortieren/Array_mit_24_Werten.png "Array 24 Werte")
Quelle: Angelehnt an Barnes/Kölling, „Java lernen mit Bluej“, Pearson-Verlag, Seite 157-159
 

Die Zahl 24 in den eckigen Klammern bei der Erzeugung des Array-Objekts hat also die Anzahl Elemente festgelegt, die in dem Array gespeichert werden können.
Wir hatten gesehen, dass man die Deklaration von Objekten und die Erzeugung in einer Zeile machen kann; dies funktioniert auch bei Arrays:

`TWuerfel meinWuerfel = new TWuerfel();`

`char[] schueler = new char[25];`

Die zweite Zeile erzeugt ein Array-Objekt zur Speicherung von 25 Zeichen und deklariert die Array-Variable `schueler` für dieses Array.

### Array-Objekte benutzen
Auf die einzelnen Elemente eines Arrays wird über den Index zugegriffen. Der Index tritt dabei auch in den markanten eckigen Klammern auf:
Über `zahlenspeicher[5]` greift man zum Beispiel auf die sechste(!) Zahl zu, so dass zum Beispiel mit 

`zahlenspeicher[5] = 17;`

ein schreibender Zugriff auf den Speicher erfolgt.

Der **Vorteil** von Arrays ist die komfortable Art Daten zu speichern. So kann man sie zum Beispiel sehr bequem im Zusammenhang mit Schleifen nutzen:
```java
int[] a = new int[100];
for (int i = 0; i < 100; i ++)
{
   a[i] = i * i;
}
```
**Nachteil** ist jedoch ein hoher Speicherverbrauch bei falscher Anwendung. Außerdem kann die Größe zur Laufzeit nicht geändert werden. 

**Fallstrick:** Zwei Fehler, die häufig im Zusammenhang mit Arrays auftreten, sind zum einen die Annahme, dass die gültigen Indizes bei 1 beginnen, und zum anderen der Zugriff auf ein Element mit dem Index, der der Größe des Arrays entspricht. Greift man zum Beispiel bei obigem Array auf `zahlenspeicher[24]` zu, so führt dies zu einem Laufzeitfehler, der `ArrayIntOutOfBoundsException` genannt wird.
