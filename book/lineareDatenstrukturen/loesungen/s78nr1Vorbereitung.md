---
name: Prüfungsvorbereitung S. 78 Nr. 1
index: 1
toc: show
---

# Prüfungsvorbereitung Lösung von <Zagros>
a) Die Datenstruktur ist deshalb der Schlange vorzuziehen, weil in einer Rinne beim Bowling mehrere Kugeln zu Verfügung stehen und man sich eine aussuchen kann. Da die Datenstruktur Schlange mit dem First-in-Fist-out-Prinzip funktioniert, hätte man bei der Wahl der Schlange nur eine Kugel, die man nehmen könnte.   
b)
```java

/**
 * Beschreiben Sie hier die Klasse Kugel.
 * 
 * @author (Ihr Name) 
 * @version (eine Versionsnummer oder ein Datum)
 */
public class Kugel
{
    private String farbe;
    private int gewicht;
    
    public Kugel(String farbe, int gewicht)
    {
        if(farbe.equals("Gelb")&&gewicht == 8 || farbe.equals("Blau")&&gewicht == 10 || farbe.equals("Rose")&&gewicht == 6){
            this.farbe = farbe;
            this.gewicht = gewicht;
        }
        else{
            throw new IllegalArgumentException("Diese Kugel gibt es nicht");
        }
    }
}
```
