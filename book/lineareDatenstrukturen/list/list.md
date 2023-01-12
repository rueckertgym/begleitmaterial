---
name: List
index: 1
toc: show
---

# List

Eine Liste (englisch: **list**) ist ein Datenstrukturtyp der es ermöglicht, eine Sammlung von Elementen zu speichern und zu verwalten. Eine Liste ist ein dynamisches Datenstruktur, das heißt, dass ihre Größe und ihr Inhalt sich während der Laufzeit eines Programms ändern können.

In der Regel können in einer Liste Elemente unterschiedlicher Typen gespeichert werden, beispielsweise Zahlen, Zeichenketten oder andere Objekte.

Um Elemente in einer Liste zu speichern und zu verwalten, werden in der Regel mehrere Methoden bereitgestellt, wie beispielsweise **add()** oder **remove()** zum Hinzufügen oder Entfernen von Elementen, **get()** oder **set()** zum Abrufen oder Ändern von Elementen an bestimmten Indizes und viele andere.

::::tabs{id="List"}

:::tab{title="Video Liste" id="Video Liste"}
::youtube[02 Lineare Datenstrukturen:  List ohne Knoten ]{#zSad1XVQ0hg}
:::

:::
:::tab{title="Struktogramm List" id="Struktogramm List"}
::struktog{data="https://struktog.openpatch.org/#pako:eNqVVMuOEzEQ_JXIp0VKI7ffjsQRJC65wA1xsNttEjF5KJnVgqL8O71iN8siJTBzsdzdLlfVlHxSm13jQS1Oat3UQgWtsza2gEHvIUZmaM0ReDI2murVXI0_9yyTH7dHPoxLOS21vhuG3cP7gTe8HV_AggsZmwakEkBrrBBMJdmir4HSC9iH-y2N6932CW7kH4KiSmsCuV8VwZyrfTmUDY98OKrFl5Pa72RV-ndjKR3ZPU_P9pdz5_nzqH01un6ckvr56zX2NlisrXTh7BAipQYaEwN2a4mS-T8rtvfDcJ4rWq2HdoFOOcXqqoeigxXAlEHsbVCr0diYJ7msQ0WHqYIxSRC9D4KTCWI2BVvFF7DP5fj9tcNHHj9xOdCK25248ebqJS12w60xUBL8XrsHDBzAR64xWprEmDCIzqQh15aAqmbwtiBgicaHXm4xvvzZt8J9KbW745OAp1uua3DIhUwyEL3QT0Z3aDFZMOS7y2aahpqLo14d6CqGWKMz-NQL2BJr9RRvabjEdNzsZ-9mfwm4bhsj6Zo7dDIR0IYGLhWCQtGEnvUk_ugNRxtY1JcEmJqDmkKVRGbrW6gTUjODGd5Ijg5RO3LAPVcgSTe4niOYji42PS3rTV4k7STcGMVwF6hAb6E8IrpE_8r6K5sv-bkk6roGecRKK5hBwq_B--ggeC6AjmJPkSY8BX9-c7Xi9beVtIxzc_WwbuNKLVKO519eXbtd"}::
:::

:::tab{title="Java List" id="Java List"}
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
::::






























































# Caesarverschlüsselung [1]

[1] Nach: Albrecht Beutelspacher: Geheimsprachen (C:H. Beck), teilweise verändert

Obwohl der Caesar-Code zu den unsichersten Verschlüsselungsverfahren der Weltgeschichte gehört, kann man behaupten, dass mit diesem Code die Kryptographie begonnen hat. Der Name leitet sich von seinem „Erfinder“ C. J. Caesar (100 – 44 v. Chr.) ab.

## Keine Geheimzeichen!
Entgegen anderer Verfahren, die zum Beispiel Buchstaben oder ganze Wörter durch Codes oder Geheimzeichen ersetzen, liegt bei der Caesar-Verschlüsselung eine radikale Entscheidung zugrunde: Die Klartextzeichen und die Geheimtextzeichen sind dieselben, für beide werden die Buchstaben benutzt.
## Eingebaute Variabilität!
Zudem hatte das Caesar-Verfahren, welches nachweislich auch schon vor mehr als zweitausend Jahren ge-nutzt wurde, schon den Aspekt berücksichtigt, dass man nach einer bestimmten Zeit die Verschlüsselung ändern können müsse. Sein „Code” besteht nämlich nicht nur aus einer einzigen Übersetzungsvorschrift, sondern aus einer ganzen Menge. Der Wechsel der einzelnen Vorschriften ist sozusagen in das System eingebaut. Wir werden das später durch den Begriff „Schlüssel” beschreiben.

Übrigens bezeichnet man in der Kryptographie – auch in nichtmilitärischen Situationen – jeden Unbefugten, der versucht, einen Code zu analysieren, als Angreifer (manchmal auch als Kryptoanalytiker). Der Angreifer spielt eine wichtige Rolle; tatsächlich kann man jedes kryptographische Verfahren als ein Dreipersonenspiel betrachten: Sender und Empfänger versuchen, sich gegen den Angreifer zu schützen, während es die Aufgabe des Angreifers ist, den Schutzwall von Sender und Empfänger zu durchbrechen.

Nun müssen wir Cäsars Idee aber beschreiben. Man benutzt zwei Alphabete, das Klartextalphabet (das ist das Alphabet in natürlicher Reihenfolge; zur Abkürzung nennen wir es KTA) und das Geheimtextalphabet (GTA), das wir darunter schreiben:

`KTA:	A B C D E F G H I J K L M N O P Q R S T U V W X Y Z`

`GTA:	D E F G H I J K L M N O P Q R S T U V W X Y Z A B C`

Das Geheimtextalphabet ist ebenfalls das gewöhnliche Alphabet, nur um ein paar Stellen verschoben. In unserem Beispiel beginnen wir unter dem Klartext-A mit dem Geheimtextbuchstaben D, setzen dann das Alphabet wie gewohnt mit E, F, G, ... fort, bis wir am Ende angelangt sind und beginnen dann wieder vorne, bis wir alle Buchstaben untergebracht haben. Die Variabilität kommt darin zum Vorschein, dass wir nicht festlegen, um wie viele Stellen das Geheimtextalphabet verschoben wird.

**Wie wird mit diesem Schema verschlüsselt?** 

Ganz einfach, indem wir einen Klartextbuchstaben durch den darunter stehenden Geheimtextbuchstaben ersetzen. So wird A zu D, B zu E usw. Aus dem Satz 

`KT: D A S I S T U N K N A C K B A R` wird dadurch der scheinbar undurchsichtige Buchstabensalat

`GT: G D V L V W X Q N Q D F N E D U`

## Entschlüsseln
Das Entschlüsseln ist kein bisschen schwieriger: Anstatt die beiden Zeilen von oben nach unten zu lesen, lesen wir sie von unten nach oben. So wird aus D wieder A, aus E wird B usw.

Natürlich ist es mühsam, immer wieder ein Geheimtextalphabet unter ein Klartextalphabet zu schreiben. Daher war es sehr nützlich, dass lange nach Cäsar, im 16. Jahrhundert, kleine „Maschinchen” erfunden wurden, mit denen man das Ver- und Entschlüsseln zum Teil automatisieren konnte. Das Bild zeigt eine solche Maschine.

Es handelt sich um zwei konzentrische Scheiben, von denen jede das Alphabet in gewöhnlicher Reihenfolge enthält. Die Scheiben sind gegeneinander drehbar, und jede Einstellung der Scheiben ergibt eine konkrete Verschlüsselungsvorschrift. Verschlüsselt wird, indem man von außen nach innen liest, und entschlüsselt, indem man von innen nach außen liest.
An dieser Maschine (die Caesar nicht hatte) kann man besonders schön die eingebaute Variabilität des Cäsar-Codes sehen: Es gibt eine ganze Reihe von verschiedenen Einstellungen der Scheiben; ihre Anzahl ist genauso groß wie die Anzahl der Buchstaben des Alphabets, also 26. Jede Einstellung ergibt eine andere Verschlüsselungsvorschrift. Wenn ein Wort verschlüsselt wird, so hängt der Geheimtext von der Einstellung der Scheiben ab: Bei verschiedenen Einstellungen ergeben sich unterschiedliche Geheimtexte.

Beim Cäsar-Chiffre handelt es sich um eine **monoalphabetische Substitution** (=Ersetzung), die zu den so genannten **symmetrischen** Verfahren zählt. Dabei wird jedem Buchstaben eines Textes ein anderer eindeutiger Buchstabe zugeordnet. Diese Zuordnung ist allerdings nicht willkürlich, sondern basiert auf der zyklischen Rotation des Alphabets um **_k_** Zeichen, dabei folgt auf z wieder a. Das **_k_** ist dann der **Schlüssel**, mit dem ver- bzw. entschlüsselt wird. Praktisch verschiebt man das Alphabet um **_k_** Zeichen (z.B. 4).

|verschlüsseln	|	entschlüsseln|
|:-:            |:-:             |
|  KLARTEXT     |    NODUWHAW    |
|+ DDDDDDDD     | - DDDDDDDD     |
|  NODUWHAW	 	|  KLARTEXT      |

  
Mathematisch entspricht diese Verschlüsselung einer buchstabenweisen _"Addition"_ des Schlüssel-Buchstaben zu jedem Buchstaben des Klartextes. Entsprechend muss für die Entschlüsselung der Schlüssel-Buchstabe vom Geheimtext abgezogen werden, um wieder den Klartext zu erhalten. 
Um aus dem Geheimtext den Klartext zu erhalten, muss der Empfänger wissen, mit welchem Algorithmus verschlüsselt wurde (hier: Addition, denkbar auch Multiplikation) und er muss den Schlüssel kennen, um den verschoben wurde. Durch Umkehrung des Algorithmus (also Subtraktion oder Division) - bei Benutzung des richtigen Schlüssels - ergibt sich dann wieder der Klartext. 

## Was heißt „Verschlüsseln”?
Das Verschlüsselungsverfahren Cäsars besticht durch seine Einfachheit; daher eignet es sich auch besonders gut dazu, die grundlegenden Prinzipien der Kryptographie zu erklären. Dadurch werden wir auch den Begriff „Sicherheit” genauer fassen können. Und dies wird uns dann wieder ermöglichen, den Cäsar-Code als besonders unsicher zu entlarven.

Ein Verschlüsselungsschema besteht aus zwei Komponenten, dem Algorithmus und dem Schlüssel. Der Algorithmus ist die allgemeine Vorschrift, wie aus einem Klartext ein Geheimtext gemacht werden kann. Der Algorithmus ist in der Regel eine komplexe Vorschrift, die heute häufig in Form eines Computerprogramms vorliegt und früher oft durch eine Maschine realisiert wurde. Beim Cäsar-Verfahren kann man sich den Algorithmus durch die Maschine aus den beiden Scheiben realisiert vorstellen.

Der Schlüssel ist demgegenüber die Angabe, wie denn nun ein Klartext konkret in einen Geheimtext übersetzt werden soll. Nur die Cäsar-Maschine zu haben, reicht nicht, man muss auch wissen, wie die Scheiben eingestellt sind. Beim Cäsar-Verfahren ist der Schlüssel also die Einstellung der Scheiben; diese kann durch einen Buchstaben angegeben werden: Zum Beispiel durch den Buchstaben, der dem Klartext-A, oder durch den Buchstaben, der dem Klartext-E entspricht.

## Wie können wir Caesars-Verfahren heutzutage an modernen Computern umsetzen? 
:::alert{info}
## Aufgabe:
- Ihr findet bei edugit ein Vorlage um den Umgang mit Objekten der Klasse Zeichenkette ("String") zu erproben. Fertigt auch wieder eine Kopie der Klasse unter eurem Namen an und arbeitet mit eurer Kopie weiter.
- Modelliert (Klassendiagramm auf Papier, Struktogramm und umgangssprachlicher Algorithmus für die benötigten Methoden digital) und implementiert eine Klasse „Caesar“, die das Verfahren zum **verschlüsseln** von Caesar auf einen Eingabestring umsetzen kann. 
-	Testet Eure Klasse in BlueJ aus.

**Hilfen:**

+ Ein Grundgerüst der Programmierung habe ich bei Edugit eingestellt. Legt wieder eine Kopie unter euren Namen an, mit der ihr anschließend weiterarbeitet.
+ Sinnvoll ist sicherlich eine Umrechnung der einzelnen Zeichen in ASCii-Code beispielsweise unter http://www.planet3dnow.de/vbulletin/showthread.php?t=249309 
+ Eine ASCii-Code Tabelle findet ihr hier: http://www.torsten-horn.de/techdocs/ascii.htm

**_Vertiefung:_**
Wenn Ihr Eure Modellierung, Euer Programm und die zugehörige **Dokumentation** fertig gestellt habt, könnt Ihr die Klasse Caesar um das Entschlüsseln und Knacken des Caesar-Codes erweitern.
:::
