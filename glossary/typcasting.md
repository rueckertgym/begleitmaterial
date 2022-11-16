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
Die einfachste und schnellste Möglichkeit einen int Wert in einen String zu konvertieren ist das anhängen eines leeren String:

### Kurzbeispiel
´´´java
int i = 7;
String s = "James Bond 00";
String s = i + "";
System.out.println(s);
´´´
Hier ergibt die Ausgabe der Stringvariable s: James Bond007

### Langbeispiel
´´´java
public class Konvertierer
{
   public Konvertierer() {

       int hilfsZahl = 5;
       //  Java int zu String
       String hilfsText = hilfsZahl + "";
       //  Ergebnis ausgeben
       System.out.println("Int zu String umwandeln in Java: " + hilfsText);
       //  int ausgeben
       System.out.println("Unser int: " + hilfsZahl);
       //  Das „Addieren“ eines int und eines Strings ergibt einen neuen String
       System.out.println("Addieren eines int (5) und eines String (\"5\"). Das Ergebnis ist ein neuer String: " + hilfsText + hilfsZahl);
       //  Integer zu String in Java
       Integer hilfsZahl2 = 7;
       String hilfsText2 = hilfsZahl2 + "";
       System.out.println("nteger zu String umwandeln: " + hilfsText2);
       System.out.println("Unser Integer: " + hilfsZahl2);
       System.out.println("Addieren eines Integer (7) und eines String (\"7\"). Das Ergebnis ist ein neuer String: " + hilfsZahl2 + hilfsText2);
   }
}
´´´
## char zu int
Im Rahmen der Kryptologie haben wir die Methode ´public char zahlenZuBuchstaben(int pZahl)´ und ´public int buchstabenZuZahlen(char pBuchstabe)´ genutzt um einem int in einen char bzw. einen char in einen int Wert zu konvertieren. 
Für unser Projekt haben wir uns zunutze gemacht, dass die Rückgabe der Methoden auf Basis der ASCII Tabelle erfolgte.
::::tabs
:::tab{title="Zahlen zu Buchstaben"}
```java
public char zahlenZuBuchstaben(int pZahl)
{
    return (char)pZahl;
}
```

Der Aufruf der Methode ´zahlenZuBuchstaben(65)´ gibt das Zeichen A wieder, da dieser Buchstabe laut ASCII Tabelle mit 65 als Dezimalzahl kodiert ist.
:::
:::tab{title="Buchstaben zu Zahlen"}
```java
public int buchstabenZuZahlen(char pBuchstabe)
{
    return (int)pBuchstabe;
}
```
Der Aufruf der Methode ´buchstabenZuZahlen('B') gibt den Zahlenwert 66 wieder, da B das 66. Zeichen laut ASCII Tabelle ist.
:::
::::




Wenn nun der numerische Wert eines Zeichen gesucht wird, nutzt man am besten die ´getNumericValue(…)-Methode´ der Klasse Character.

```java
char c = '7';
int i = Character.getNumericValue(c);
System.out.println(i);
```
Die Ausgabe auf der Konsole ist 7.

## int zu char
