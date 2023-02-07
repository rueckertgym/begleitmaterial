---
name: Prüfungsvorbereitung S. 78 Nr. 1
index: 1
toc: show
---

# Prüfungsvorbereitung Lösung von Zagros und Marouane
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
        if(farbe.equals("gelb")&&gewicht == 8 || farbe.equals("blau")&&gewicht == 10 || farbe.equals("rosa")&&gewicht == 6){
            this.farbe = farbe;
            this.gewicht = gewicht;
        }
        else{
            throw new IllegalArgumentException("Diese Kugel gibt es nicht");
        }
    }
}
```
c) 
```java
public String haeufigsteFarbe()
    {
        String haeufigsteFarbe = null;
        int rosaKugeln = 0;
        int blaueKugeln = 0;
        int gelbeKugeln = 0;
        for(int i = 0; i<kugeln.getSize(); i++){
            Kugel kugel = kugeln.get(i);
            String farbe = kugel.getFarbe();
            if (farbe.equals("rosa")) {
                rosaKugeln++;
            } else if (farbe.equals("blau")) {
                blaueKugeln++;
            } else if (farbe.equals("gelb")) {
                gelbeKugeln++;
            }
        }
        if (rosaKugeln > blaueKugeln){
            if(rosaKugeln > gelbeKugeln){
                haeufigsteFarbe = "rosa";
            }
            else{
                haeufigsteFarbe = "gelb"; //Da gelbe Kugeln schwerer sind als rosa Kugeln, ist es immer gelb, auch wenn die Anzahl der Kugeln gleich ist
            }
        }
        else if(blaueKugeln >= gelbeKugeln){
            haeufigsteFarbe = "blau"; //Da blaue Kugeln die schwersten sind, ist es immer blau
        }
        else{
            haeufigsteFarbe = "gelb";
        }
        return haeufigsteFarbe;
    }
```
d) 
Nach dem Ausführen der Methode befinden sich alle blauen Kugeln am Ende des fünften Ständers.
Dabei werden in der Methode blaue Kugeln durch den folgenden Teil an das Ende eines Ständers befördert:  
 if (j<19){  
                            Kugel hilf = aktKugel;  
                            pStaender[i].vorrat[j] = pStaender[i].vorrat[j+1];  
                            pStaender[i].vorrat[j+1] = hilf;
            ...}  
Der darauf folgende Teil sorgt dann dafür, dass die Kugel und die erste Kugel des nächsten Ständers tauschen. Dies geschieht solange, bis die erste blaue Kugel ans Ende des letzten Ständers angekommen ist. Anschließend wird alles durch die erste for-Schleife wiederholt und zwar 100-Mal. Am Ende sind also die fünf blauen Kugeln in der letzten Reihe des fünften Ständers.

