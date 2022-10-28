---
name: Casear Modellierung
index: 2
toc: show
---

### Modellierung im Unterricht
Wir haben im Unterricht eine gemeimsame Klassendiagramm (also eine Schnittstellenvereinbarung) entwickelt. Zu einer Schnittstellenverinbarung gehört auch eine Dokumentation, damit eindeutig für alle beteiligten Entwickler festgelegt ist, was welche Methode leitet, wobei das "Wie" den Programmieren obliegt.

### Klassendiagramm der gemeinsamen Modellierungsphase
```java
classDiagram
      class Caesar{
          -String gt
          -String kt
          -int schluessel
          +Caesar()
          +verschluesseln() void
          +entschluesseln() void
          -zahlenZuBuchstaben(int pWert) char
          -buchtsabenZuZahlen(char pWert) int
          +getGt() String
          +setGt(String pGt) void
          +getKt() String
          +setKt(String pGt) void         
          +getzchluessek() int
          +setSchluessel(int pSchluessel) void
        }
 ```

### Dokumentation aus der gemeinsamen Modellierungsphase
#### Klasse Caesar (Diese Dokumentation muss noch hinzugefügt werden)

