---
index: 2
toc: show
name: Programmierung
---

# ÜBerprüfung eines Wortes mit Hilfe eines Programma

Bei der PRogrammierung benötigen wir drei Klassen "Scanner", "Parser" und "Token", wobei der Scanner die lexigraphische 
Überprüfung übernimmt d.h. es wird überprüft, ob die Zeichen des Eingabestrings den Zeichen des Eingabealphabets entsprechen. 

Wenn nicht bricht die Überprüfung mit einem Fehler ab, sonst wird die grammatikalische Überprüfung mit Hilfe der erzeugten Token, die in einer Tokenliste gespeichert werden, angestoßen.

```mermaid
classDiagram

Scanner --> List~Token~ : -tokenliste
Scanner --> Token : -aktuellesToken
Parser --> List~Token~ : -tokenliste
Parser --> Token : -aktuellesToken
Analyse --> Scanner : -scanner
Analyse --> Parser : -parser
Analyse --> List~Token~ : -tokenliste

class Analyse {
    -eingabe String
    +Analyse(String pEingabe)
    +analysiere() void
}

class Token {
    -wert String
    -typ String
    +Token(String pWert, String pTyp)  
    +setWert(String pWert) void
    +getWert() String
    +setTypt(String pTyp) void
    +getTyp) String  
}

class Scanner {
    -fehler boolean
    -eingabe String
    +Scanner(String pEingabe, List~Token~ pTokenliste)
    +scanne() void
    -ausgbabe(boolean pFehler) void
    +getTokenliste()  List~Token~
}

class Parser {
    -fehler boolean
    +Parser(List~Token~ pTokenliste)
    +nextToken() Token
    +parse() boolean
    +pruefeS() boolena
    +pruefeA() boolean
    +pruefeb() boolean

}


``` 