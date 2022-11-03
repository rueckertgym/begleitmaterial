---
name: Modellierung
index: 2
toc: show
---

### Modellierung im Unterricht
Wir haben im Unterricht ein gemeimsames Klassendiagramm (also eine Schnittstellenvereinbarung) entwickelt. Zu einer Schnittstellenverinbarung gehört auch eine Dokumentation, damit eindeutig für alle beteiligten Entwickler festgelegt ist, was welche Methode leistet, wobei das "Wie" den Programmierern obliegt.

Für Polybius findet ihr unten eine mögliche Modellierung basierend auf einem 2-dimensionalem Array. Informiert euch im Buch auf Seite 53 ff. über mehrdimensionale Arrays.

:::alert{info}
**Für die Schnellen:** Findet eine Lösung ohne die Verwendung eines 2-dimensionalen Arrays und auf der Basis eines Strings.
:::

### Klassendiagramm der gemeinsamen Modellierungsphase
```mermaid
classDiagram
    Kryptomat <|-- Caesar
    Kryptomat <|-- Vigenere
    Kryptomat <|-- Polybius
    <<Abstract>> Kryptomat
    Kryptomat : -String gt
    Kryptomat : -String kt
    Kryptomat: +verschluesseln()*
    Kryptomat: +entschlüsseln()*
    Kryptomat: -zahlenZuBuchstaben(int pWert) char
    Kryptomat: -BuchstabenZuZahlen(char pWert) int
    Kryptomat: +getGt() String
    Kryptomat: +setGt(String pGt) void
    Kryptomat: +getKt() String
    Kryptomat: +setKt(String pKt) void

    class Polybius{
      -alphabetQuadrat int [][]
      +Polybius()
      -bfmS() void
      +verschluesseln() void
      +entschluesseln() void
    }

    class Caesar{
      -int schluessel
      +Caesar()
      +getSchluessel() int
      +setSchluessel(int pSchluessel) void 
      +verschluesseln() void
      +entschluesseln() void
    }
    class Vigenere{
      -String schluessel
      +Vigenere()
      +getSchluessel() String
      +setSchluessel(String pSchluessel) void
    }
    
```


### Dokumentation der gemeinsamen Modellierung (fehlt noch)
