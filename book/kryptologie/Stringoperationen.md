---
name: Zeichenketten in Java
index: 0
toc: show
---

# Exkurs: Die Klasse String und String Operationen in Java

In den Vorgaben für das Zentralabitur werden explizit Operationen und
Methoden für Datentypen und Klassen
angeben[\[1\]](https://www.standardsicherung.schulministerium.nrw.de/cms/zentralabitur-gost/faecher/getfile.php?file=5438).
Für Strings wird der sichere Umgang mit rechts stehenden Methoden
erwartet.

![Stringoperationen](/Bilder/stringoperationen/image1.png)

## Was muss man sich unter einem String vorstellen?

Ein Array ist im Prinzip eine Aneinanderreihung von Zeichen (Charakter =
char; char ist ein in Java eingebauter Datentyp, mit dem man genau ein
Zeichen („Charakter") speichern kann), wobei man über einen Index (eine
Zahl) auf jedes Zeichen direkt zugreifen kann: 

**(Achtung: Die Indizierung beginnt bei 0!)**


|  Index  |   0   | 1 |   2   |   3   |   4   |   5   | 6 |   7   |   8   |   9   |   10  |   11  |  12   |
|:-------:|:-----:|:-:|:-----:|:-----:|:-----:|:-----:|:-:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|
| Zeichen | **a** |   | **l** | **o** | **n** | **g** |   | **s** | **t** | **r** | **i** | **n** | **g** |

## String ist Klasse!

Uns war bei der Programmierung schon immer aufgefallen, dass der String
der zunächst einzige Datentyp ist, der groß geschrieben wird (String
antwort = „Hallo"). Dies ist schon ein erster Hinweis darauf, dass es
sich bei Strings nicht(!) um einen so genannten *einfachen
Datentyp* sondern um eine eigene *Klasse* handelt.

In Java werden Datentypen in zwei Kategorien unterteilt, in
die **einfachen Datentypen** und in die Referenztypen
(**Klassentypen**). Einfache Datentypen (wie z.B. int, char, double,
boolean, ...) sind in eine Programmiersprache eingebaut, während die
Referenztypen als Objekte verwaltet werden. Die Programmiersprache
Smalltalk kennt beispielsweise gar keine einfachen Datentypen, sondern
organisiert alles über Objekte.

**Zeichenketten (Strings) sind in Java Objekte**. Eine Variable vom
Referenztyp String enthält nicht die Zeichenkette selbst, sondern die
Speicheradresse eines Objekts der Klasse String. Sie kann auch NULL
enthalten, eine sogenannte Nullreferenz.

## Erzeugen von Zeichenketten

|    Erklärung     |         Java Synthax    |
|-----------------------------------------------------------------------------|:------------------------------------:|
|    Zeichenketten-Objekte können in Java auf verschiedene Arten erzeugt werden: Einfache Variante mit Initialisierung wie wir sie verwenden                                  | String sName = “Kolmer“; |
| Erzeugen eines Objekts mit dem Konstruktor                                  | String sName = new String(“Kolmer“); |

## Vergleich von Zeichenketten

Da Zeichenketten Objekte sind, ist ein simpler Vergleich wie  if (sName
== "Kolmer")  nicht möglich, da so nur die Adressen der Objekte
verglichen würde. Dafür gibt es in der String-Klasse die Methoden equals
und compareTo. Hier soll die Methode equals genügen.

In der Klassendokumentation der Klasse java.lang.String kann folgender
Eintrag entnommen werden:

| Datentyp | Erläuterung |
|:-------:|:----------------------------------------------------------------------:|
|boolean| equals(Object anObject)  Compares this string to the specified object.
Als kleines Beispiel soll die folgende Methode dienen, die als
Parameterwert einen Usernamen erhält und testen soll, ob es "Kolmer"
ist. 

```md
public boolean pruefeUser(String pUsername)
{
  String sName = "Kolmer";
  boolean bErIstEs = false;
  
  if (pUsername.equals(sName))
  {
    bErIstEs = true;
  }
    return bErIstEs;

    // Anmerkung: Statt der Verzweigung ginge auch kürzer:
    // bErIstEs = pUsername.equals(sName);
    // Selbstverständlich ginge auch:
    // bErIstEs = sName.equals(pUsername);
}
``` 

## Weitere Stringoperationen 

Mit Hilfe verschiedener Methoden der String-Bibliothek können Anfragen
an einen String gestellt werden. Für die folgenden Beschreibungen dieser
Methoden sei angenommen, dass die folgenden Variablen deklariert seien
(siehe Kasten rechts). Die Operation ...

| Java Synthax                           |           Erläuterung                                                           |
|----------------------------------------|----------------------------------------------------------------------------------|
|i = s.length();                         | liefert die Anzahl der Zeichen im String s.  **Achtung:** Hat ein String die Länge 5, so ist er von 0 bis 4 indiziert  |
| ch = s.charAt(3);                      | liefert das Zeichen mit dem Index 3 aus dem String s, also hier ein ”o“. Die Indizierung beginnt bei 0. |
| i = s.compareTo("also a long string"); | liefert -1, weil s vor dem angegebenen String in der lexikographischen Ordnung liegt. Der Wert 0 ergibt sich bei Gleichheit und der Wert +1, wenn der angegebene String hinter dem String s steht.    |
| i = s.indexOf("ng") + s.indexOf(’a’);  | liefert die Position des ersten Vorkommens von „ng“ in s oder -1, falls „ng“ nicht gefunden wurde. Hier erhält man also 4 + 1. Man sieht, dass man auch eine char-Konstante als Parameter übergeben kann. |
| i = s.indexOf("ng",5);                 | liefert die Position des ersten Vorkommens von „ng“ in s, beginnt die Suche aber erst ab Position 5. Im Beispiel wird also 11 zurück geliefert |
| s2 = s.substring(2);                   | liefert den Teilstring von s ab der Position 2, hier „long string“.   |
| s2 = s.substring(2,6);                 | liefert den Teilstring von s ab der Position 2 und bis ausschließlich 6, hier „long“ |
| s2 = s+“!!!“;                          | Liefert „a long string!!!”. Mit „+“ kann man zwei Strings verbinden. |

Alle Methoden findet man in der vollständigen Klassendokumentation.

**Aufgabe:**

Überführe folgendes Klassendiagramm in Java Quellcode mit Hilde der Online-IDE und implementiere
die Methoden vollständig inkl. Dokumentation und PAP oder Struktogramm
für die Methoden *palindromTest()* und *ZeichenkettenUmkehren().* 

Teste anschließend die
Methoden *palindromTest()* und *ZeichenkettenUmkehren().*

![Klasse Tester](/Bilder/stringoperationen/image2.png)

:::onlineide

```markdown Tipp
## Tip:

Tipps werden in einer einfachen Markdown-Syntax
verfasst, die **Fettschrift** u.ä. ermöglicht, aber
auch Syntax-Highlighting im Fließtext (`class Quadrat extends Rectangle { }`) und in ganzen Absätzen:

```java

double v = Math.random()\*8 + 2; // Amount of speed between 2 and 10

double w = Math.random()*2*Math.PI; // angle between 0 and 2\*PI

vx = v \* Math.cos(w);

vy = v \* Math.sin(w);

```
```

```java Feuerwerk.java

new Feuerwerk();

class Feuerwerk extends Actor {

   public void act() {
      if(Math.random() < 0.03) {

         int funkenzahl = Math.floor(Math.random() * 50 + 30);
         int farbe = Color.randomColor(128);

         double x = Math.random() * 400 + 200;
         double y = Math.random() * 600;
         double lebensdauer = 60 + Math.random() * 60;
         for (int i = 0; i < funkenzahl; i++) {
            new Funke(x, y, farbe, lebensdauer);
         }
         Sound.playSound(Sound.cannon_boom);

      }
   }

}

class Funke extends Circle {
   double vx;
   double vy;
   double lebensdauer;           // lebensdauer in 1/30 s

   Funke(double x, double y, int farbe, double lebensdauer) {
      super(x, y, 4);
      double winkel = Math.random() * 2 * Math.PI;
      double v = Math.random() * 15 + 5;
      vx = v * Math.cos(winkel);
      vy = v * Math.sin(winkel);
      setFillColor(farbe);
      this.lebensdauer = lebensdauer;
   }

   public void act() {
      lebensdauer--;
      move(vx, vy);
      vy = vy + 0.2;
      if(lebensdauer < 30) {
         setAlpha(lebensdauer / 30);
      }
      if(isOutsideView() || lebensdauer < 0) {
         destroy();
      }
   }

}

```

:::


## Klassendokumentation Tester

Die Klasse Tester werden einfache Zeichenkettenoperationen auf Basis der
Klasse String durchgeführt.

**Konstruktor**

**Tester()**

Ein Objekt wird erzeugt und die beiden Attribute zEingabe
und zAusgabe initialisiert.

**Anfrage**

**getZEingabe():String** 

Die Anfrage liefert den Wert von zEingabe
zurück

**Anfrage**

**getZAusgabe():String** 

Die Anfrage liefert den Wert von zAusgabe
zurück

**Auftrag**

**setZEingabe(pEingabe:String)** 

Der Auftrag setzt den Wert von zEingabe auf pEingabe.

**Auftrag**

**setZAusgabe(pEingabe:String)** 

Der Auftrag setzt den Wert von zAusgabe auf pEingabe.

**Anfrage**

**zeichenketteUmkehren():String** 

Die Anfrage kehrt die Zeichenabfolge von zEingabe herum, speichert die neue Zeichenkette in zAusgabe und gibt diesen Wert zurück.

**Anfrage**

**palimdromTest():boolean** 

Die Anfrage testet den Wert von zEingabe auf ein Palimdrom und gibt wahr zurück, wenn ein Palindrom gespeichert ist, sonst falsch.

**Hilfe**

http://www.standardsicherung.nrw.de/abitur-gost/fach.php?fach=15

http://openbook.rheinwerk-verlag.de/javainsel/javainsel_04_004.html#dodtp7f11b4f3-2973-47a1-9c29-5043481df6f4
