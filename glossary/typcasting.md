---
name: Typasting
index: 2
toc: show
---
# Typasting

An dieser Stelle schauen wir uns der Typumwandlung etwas genauer an. 

Hin und wieder benötigen wir Möglichkeitenen einen int Wert in einen String oder ähnlich umzuwandeln.

## String zu int
Es gibt mehre Möglichkeiten einen String in einen int zu konvertieren.

Integer.​toString(i)

Integer.toString(int i, int base)

i + ""

String.format() i

```java
public String entschluesseln()
{
        kt = "";
        int zeile = 0;
        int spalte = 0;
        for(int i = 0; i < gt.length()-1; i= i+2)
        {
            String substr1 = gt.substring(i, i+1);
            String substr2 = gt.substring(i+1, i+2);
            //int spalte = (int)substr.charAt(1) -49;
            zeile = Integer.parseInt(gt.charAt(i)+""); //substr1);
            spalte = Integer.parseInt(gt.charAt(i+1)+"");//substr2);
            
            
            //int spalte = (int)substr.charAt(1) -49;
            kt = kt + this.zahlenZuBuchstaben(Quadrat[zeile][spalte]);
            //kt += (char)Quadrat[zeile][spalte];
        }
        return kt;
}
```   

## int zu String

## char zu int

## int zu char
