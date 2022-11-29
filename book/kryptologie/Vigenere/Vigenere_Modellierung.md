---
name: Modellierung
index: 2
toc: show
---

### Modellierung im Unterricht
Wir haben im Unterricht eine gemeimsame Klassendiagramm (also eine Schnittstellenvereinbarung) entwickelt. Zu einer Schnittstellenverinbarung gehört auch eine Dokumentation, damit eindeutig für alle beteiligten Entwickler festgelegt ist, was welche Methode leistet, wobei das "Wie" den Programmierern obliegt.

### Klassendiagramm der gemeinsamen Modellierungsphase
```mermaid
classDiagram
      class Vigenere{
          -String gt
          -String kt
          -String schluessel
          +Vigenere()
          +verschluesseln() void
          +entschluesseln() void
          -zahlenZuBuchstaben(int pWert):char
          -buchstabenZuZahlen(char pWert):int
          +getGt() String
          +setGt(String pGt) void
          +getKt() String
          +setKt(String pGt) void         
          +getSchluessek() String
          +setSchluessel(String pSchluessel) void
        }
 ```

### Dokumentation der gemeinsamen Modellierung (fehlt noch)
`Viginere()`

Ein Objekt der Klasse Viginere wird erzeugt. Hierbei wird der Klartext und der Geheimtext mit keinem Wert und der Schlüssel mit A (also Verschiebung um keinen Wert) initialisiert.

`void verschluesseln()`

Der Klartext wird mit Hilfe des Schluessels nach der Vigineremethode verschluesselt. Sind weder Schluessel und/oder Klartext gesetzt wird das "leere" Wort mit einem Schlüsselwert von 0 verschluesselt. Beim Verschlüsseln werden nur Grossbuchstaben verschlüsslelt.

`void entschluesseln()`

Der verschlüsselte Text (Geheimtext) wird nach der Vigineremethode entschlüsslet und speichert den entschlüssleten Text im Attribut für den Klartext (kt).

`char zahlenZuBuchstaben(int pWert)`

Die Anfrage liefert zu einem Zahlenwert den nach ASCII Tabelle passenden Buchstaben.

`int buchstabenZuZahlen(char pWert)`

Die Anfrage liefert zu einem Buchstaben den nach ASCII Tabelle passenden Zahlenwert.

`String getGt()`

Die Anfrage gibt den verschlüssleten Text (Geheimtext) wieder (Wert des Attributs gt).

`void setGt(String pGt)`

Setze Methode für den Geheimtext auf den Wert des Parameters pGt.

`String getKt()`

Die Anfrage gibt den unverschlüssleten Text (Klartext) wieder (Wert des Attributs kt).

`void setKt(String pKt)`

Setze Methode für den Klartext auf den Wert des Parameters pKt.

`String getSchluessel()`

Die Anfrage gibt den des Schlüssels wieder (Wert des Attributs schluessel).

`void setSchluessel(int pSchluessel)`

Setze Methode für den Schlüssel auf den Wert des Parameters pSchluessel.
