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
