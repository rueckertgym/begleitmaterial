---
name: Abstrakte Klassen
index: 5
toc: show
---

# Abstrakte Klassen und abstrakte Methoden
Nicht immer soll eine Klasse sofort ausprogrammiert werden. Dies ist der Fall, wenn die Oberklasse lediglich Methoden für die Unterklassen vorgeben möchte, aber nicht weiß, wie sie diese implementieren soll.

## Abstrakte Klassen
Bisher haben wir Vererbung eingesetzt und jede Klasse konnte Objekte bilden. Das ist allerdings nicht immer sinnvoll, nämlich genau dann, wenn eine Klasse nur in einer Vererbungshierarchie existieren soll. Sie kann dann als Modellierungsklasse eine Ist-eine-Art-von-Beziehung ausdrücken und Signaturen (=“Vorgaben für die Methoden“) für die Unterklassen vorgeben. Eine Oberklasse besitzt dabei Vorgaben für die Unterklasse, das heißt, alle Unterklassen erben die Methoden. Ein Exemplar der Oberklasse selbst muss nicht existieren.
Um das in Java auszudrücken, setzen wir den Modifizierer abstract an die Typdefinition der Oberklasse. Von dieser Klasse können dann keine Exemplare gebildet werden. Ansonsten verhalten sich die abstrakten Klassen wie normale, sie enthalten die gleichen Eigenschaften und können auch selbst von anderen Klassen erben. Abstrakte Klassen sind das Gegenteil von konkreten Klassen.

_Beispiel:_ Wir wollen die Klasse Gebaeude als Oberklasse für konkrete Gebäude abstrakt machen.

```java
public abstract class Gebaeude
{
    private int zQuadratmeter;

    public Gebaeude()
    {
        zQuadratmeter = 0;
    }
    
    public int gibQuadratmeter()
    {
        return zQuadratmeter;
    }
    
    public void setzeQuadratmeter(int pQm)
    {
        zQuadratmeter = pQm;
    }
}
```

Mit dieser abstrakten Klasse Gebaeude drücken wir aus, dass es eine allgemeine Klasse ist, zu der keine konkreten Objekte existieren. Es gibt in der realen Welt schließlich keine allgemeinen und unspezifizierten Gebäude, sondern nur spezielle Unterarten von Gebäuden, zum Beispiel Diskotheken, Kirchen und so weiter. Es ergibt also keinen Sinn, ein Exemplar der Klasse Gebaeude zu bilden. Die Klasse soll nur in der Hierarchie auftauchen, um alle konkreten Unterklassen von Gebaeude darzustellen. Das zeigt, dass Oberklassen allgemeiner gehalten sind und Unterklassen weiter spezialisieren. Ein Versuch, ein Objekt der abstrakten Klasse zu bilden, führt zu einem Fehler.
Die abstrakten Klassen werden normal in der Vererbung eingesetzt. Eine Klasse kann die abstrakte Klasse erweitern und auch selbst wieder abstrakt sein.

## Abstrakte Methoden
Das Schlüsselwort abstract leitet die Definition einer abstrakten Klasse ein. Eine Klasse kann ebenso abstrakt sein wie eine Methode. Eine abstrakte Methode definiert lediglich die Signatur und eine Unterklasse implementiert dann irgendwann diese Methode. Die Klasse ist dann nur für den Kopf der Methode zuständig, während die Implementierung an anderer Stelle erfolgt. Durch abstrakte Methoden wird ausgedrückt, dass die Oberklasse keine Ahnung von der Implementierung hat und dass sich die Unterklassen darum kümmern müssen.
Zum Beispiel wäre es schon, wenn man Gebäude mit gibTyp() nach einer Benennung fragen könnte. Könnten wir Exemplare der Klasse Gebaeude bilden (was nicht geht!), so könnten diese nicht auf die Anfrage antworten, da sie noch nicht näher spezifiziert sind. 
Aber jede von Gebaeude abgeleitet Klasse soll auf die Anfrage antworten können müssen. Daher wird das Gebaeude die Methode gibTyp() abstrakt definiert, sie also – mit ihrer Signatur – vorgeben und damit die Implementation für jede konkrete Unterklasse erzwungen. 

```java
public abstract class Gebaeude
{
    private int zQuadratmeter;

    public Gebaeude()
    {
        zQuadratmeter = 0;
    }
    
    public abstract String gibTyp();
    
    public int gibQuadratmeter()
    {
        return zQuadratmeter;
    }
    
    public void setzeQuadratmeter(int pQm)
    {
        zQuadratmeter = pQm;
    }
}
```
Damit haben wir die Unterklassen – von denen wir TDisko und TKirche definieret haben – automatisch dazu aufgefordert, die Funktion zu überschreiben, damit sich überhaupt konkrete Exemplare bilden lassen. Ist mindestens eine Methode abstrakt, so ist es automatisch die ganze Klasse. Deshalb müssen wir das Schlüsselwort abstract ausdrücklich vor den Klassennamen schreiben. Vergessen wir das Schlüsselwort abstract bei einer solchen Klasse, erhalten wir einen Compilerfehler. Eine Klasse mit einer abstrakten Methode muss abstrakt sein, da sonst irgendjemand ein Exemplar konstruieren und genau diese Methode aufrufen könnte.
Versuchen wir, ein Exemplar einer abstrakten Klasse zu erzeugen, so bekommen wir ebenfalls einen Fehler. 

```java
public class Disko extends Gebaeude
{
    private int zAktuelleAnzahlMenschen;
    private int zMaximaleAnzahlMenschen;

    public Disko()
    {
        super();
        zAktuelleAnzahlMenschen = 0;
        zMaximaleAnzahlMenschen = 0;
    }

    public String gibTyp()
    {
      return "Diskothek";
    }
…
}
```

## Vererben von abstrakten Methoden
Wenn wir von einer Klasse abstrakte Methoden erben, so haben wir zwei Möglichkeiten:
1. Wir überschreiben alle abstrakten Methoden und implementieren sie. Dann muss die Unterklasse nicht mehr abstrakt sein (wobei sie es auch weiterhin sein kann). Von der Unterklasse kann es ganz normale Exemplare geben.
2. Wir überschreiben die abstrakte Methode nicht, sodass sie normal vererbt wird. Das bedeutet: Eine abstrakte Methode bleibt in unserer Klasse, und die Klasse muss wiederum abstrakt sein.


## Exkurs - Interfaces

Das Konzept der Einfachvererbung wird durch die Verwendung von Interfaces etwas aufgeweicht, denn eine Klasse kann neben der Vererbung durch seine Oberklasse noch ein oder mehrere Interfaces implementieren, also zusätzlich die Methoden des Interfaces erben. 

Konflikte, die normalerweise bei Mehrfachvererbung entstehen können (zwei gleichnamige Methoden mit verschiedenen Definitionen erben), werden dabei vermieden, da die Methoden im Interface gar nicht definiert sind. Der Hauptnutzen eines Interfaces besteht also nicht in der Vererbung von konkreten Inhalten, sondern in der Beschreibung einer abstrakten Funktionalität. Jede Klasse, die das Interface implementiert, muss diese abstrakte Funktionalität durch konkrete Inhalte ausfüllen.


Folgendes sollte man beim Umgang mit Interfaces beachten: 
+ Das Schlüsselwort interface muss (an Stelle von class) vor der Definition stehen. 
+ Alle Methoden eines Interfaces sind public, d.h. private und protected sind verboten. 
+ Alle Methoden eines Interfaces sind abstract
+ Ein Interface ist nicht instanziierbar und darf keinen Konstruktor haben. 
+ Die Implementation einer Schnittstelle wird durch eine gestrichelte Linie mit geschlossener, nicht ausgefüllter Pfeilspitze dargestellt. 

**Aufgabe:**
Erstellt ein UML-Klassendiagramm mit den Klassen TCaesar, TVigenere und der abstrakten Oberklasse TKryptomat.
