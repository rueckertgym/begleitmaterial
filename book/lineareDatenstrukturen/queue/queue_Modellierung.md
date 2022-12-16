---
name: Modellierung
index: 2
toc: show
---


# Modellierung im Unterricht
Wir haben im Unterricht eine gemeimsame Klassendiagramm (also eine Schnittstellenvereinbarung) entwickelt. Zu einer Schnittstellenverinbarung gehört auch eine Dokumentation, damit eindeutig für alle beteiligten Entwickler festgelegt ist, was welche Methode leitet, wobei das "Wie" den Programmieren obliegt.

## Klassendiagramm der gemeinsamen Modellierungsphase
```mermaid
classDiagram
      class Caesar{
          -String gt
          -String kt
          -int schluessel
          +Caesar()
          +verschluesseln() void
          +entschluesseln() void
          -zahlenZuBuchstaben(int pWert) char
          -buchstabenZuZahlen(char pWert) int
          +getGt() String
          +setGt(String pGt) void
          +getKt() String
          +setKt(String pGt) void         
          +getSchluessel() int
          +setSchluessel(int pSchluessel) void
        }
 ```

## Dokumentation aus der gemeinsamen Modellierungsphase
### Klasse Caesar

**Queue**

Ein Objekt der Klasse Caesar wird erzeugt. Hierbei wird der Klartext und der Geheimtext mit keinem Wert initialisiert und der Wert für den Schlüssel auf 0 gesetzt.

**void verschluesseln()**

Der Klartext wird mit Hilfe des Schluessels nach der Caesarmethode verschluesselt. Sind weder Schluessel und/oder Klartext gesetzt wird das "leere" Wort mit einem Schlüsselwert von 0 verschluesselt. Beim Verschlüsseln werden nur Grossbuchstaben verschlüsslelt.

**void entschluesseln()**

Der verschlüsselte Text (Geheimtext) wird nach der Caesarmethode entschlusslet und speichert den entschlüssleten Text im Attribut für den Klartext (kt).


**char zahlenZuBuchstaben(int pWert)**

Die Anfrage liefert zu einem Zahlenwert den nach ASCII Tabelle passenden Buchstaben.

**int buchstabenZuZahlen(char pWert)**

Die Anfrage liefert zu einem Buchstaben den nach ASCII Tabelle passenden Zahlenwert.

**String getGt()**

Die Anfrage gibt den verschlüssleten Text (Geheimtext) wieder (Wert des Attributs gt).

**void setGt(String pGt)**

Setze Methode für den Geheimtext auf den Wert des Parameters pGt.

**String getKt()**

Die Anfrage gibt den unverschlüssleten Text (Klartext) wieder (Wert des Attributs kt).

**void setKt(String pKt)**

Setze Methode für den Klartext auf den Wert des Parameters pKt.

**int getSchluessel()**

Die Anfrage gibt den des Schlüssels wieder (Wert des Attributs schluessel).

**void setSchluessel(int pSchluessel)**

Setze Methode für den Schlüssel auf den Wert des Parameters pSchluessel.
