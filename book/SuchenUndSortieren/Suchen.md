---
name: Suchen
toc: show
index: 1
---
# Suchen 
In der Informatik versteht man unter **Suchen** ein Verfahren zur Untersuchung einer Datenstruktur (in unserem Fall momentan die Datenstruktur array) auf einen **bestimmten** Inhalt.

## lineare Suche

### Erklärung:
Die **lineare Suche** ist allgemein der einfachste Suchalgorithmus. Dabei wird ein Element in einem Array gesucht und es ist irrelevant, onb der Array sortiert ist oder nicht den die lineare Suche beginnt am Anfang des Arrays und durchläuft ihn ohne hin.

Sozusagen wächst die Suche linear mit der Anzahl an Elementen und sucht solange bis er das gesuchte Element gefunden hat, also im bestcase ist es das erste Element im worstcase das letzte.

Wenn die Anzahl der Elemente in einer Liste klein ist, dann ist es oft auch das effizienteste Verfahren.
### Beispiel Anwendung:
| [0] | [1] | [2] | [3] | [4] | [5] | [6] | [7] | [8] | [9] | ges. Zahl |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |:-:| :-: | :-: |
| **16** | 78 | 11 | 9 | 0 | 777 | 45 | 109 | 8 | 90 | **11** |

Als Beispiel wird die Zahl **9** gesucht. angefangen wird zunächst an der Stelle 0 im Array. An dieser Stelle befindet sich die Zahl **16**, da diese nicht die gesuchte Zahl ist gehen wir ein Fach im Array weiter.

| [0] | [1] | [2] | [3] | [4] | [5] | [6] | [7] | [8] | [9] | ges. Zahl |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |:-:| :-: | :-: |
| **16** | 78 | 11 | 9 | 0 | 777 | 45 | 109 | 8 | 90 | **11** |
| ~~16~~ | **78** | 11 | 9 | 0 | 777 | 45 | 109 | 8 | 90 | **11** |

Nach der **16** kommt die **78** die ist ebenfalls noch nicht die gesuchte Zahl somit wird sich weiter bewegt.

| [0] | [1] | [2] | [3] | [4] | [5] | [6] | [7] | [8] | [9] | ges. Zahl |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |:-:| :-: | :-: |
| **16** | 78 | 11 | 9 | 0 | 777 | 45 | 109 | 8 | 90 | **11** |
| ~~16~~ | **78** | 11 | 9 | 0 | 777 | 45 | 109 | 8 | 90 | **11** |
| ~~16~~ | ~~78~~ | **11** | 9 | 0 | 777 | 45 | 109 | 8 | 90 | **11** |

Nach der **78** kommt die gesuchte Zahl **11** und die Suche ist mit der Wiedergabe der gefundenen Informationen beendet.

### Struktorgramm und Java Quellcode
::::tabs{id="Lineare Suche"}
:::tab{title="Lineare Suche" id="Struktog. lineare"}
:::
:::tab{title="Java lineare Suche" id="Java lineare Suche"}
```java
    public boolean lineareSuche(int pZahl)
    {      
        boolean gefunden = false;
        for (int i = 0 ; i < zZahlenarray.length ; i++)
        {
            if ( zZahlenarray[i] == pZahl ) 
            {
                gefunden = true;
            }
        }
        return false;
    }
```
:::
:::tab{title="Lineare Suche optimiert" id="Struktog. lineare optimiert"}
:::
:::tab{title="Java lineare Suche optimiert" id="Java lineare Suche optimiert"}
```java
    public boolean lineareSuche(int pZahl)
    {      
        boolean gefunden = false;
        int i = zZahlenarray.length-1;
        do
        {
            if ( zZahlenarray[i] == pZahl )
            {
                gefunden = true;
                i++;
            }
        }
        while (gefunden == false);
        return gefunden;
    }
```
:::
::::
## binäre Suche

### Erklärung:
Eine binäre Suche ist eine schnelle und effiziente Methode, um einen bestimmten Zielwert aus einer Reihe von bestellten Artikeln zu ermitteln. Indem Sie in der Mitte der zu sortierten Datenstruktur (in unserem Fall ein array) beginnen, können Sie den Suchraum effektiv halbieren, indem Sie anhand des Medianwerts im Vergleich zum Zielwert festlegen, ob die Liste auf- oder absteigend sein soll.

Bei der binären Suche musste das Ziel nur mit drei Werten verglichen werden. Im Vergleich zu einer linearen Suche hätte die Suche vom ersten Wert an begonnen und sich nach oben bewegt, wobei das Ziel mit acht Werten verglichen werden musste. Eine binäre Suche ist nur mit einem geordneten Datensatz möglich; Wenn die Daten zufällig angeordnet sind, liefert eine lineare Suche die ganze Zeit über Ergebnisse, während eine binäre Suche wahrscheinlich in einer Endlosschleife stecken bleibt.
### Beispiel Anwendung
| [0] | [1] | [2] | [3] | [4] | [5] | [6] | [7] | [8] | [9] | ges. Zahl |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |:-:| :-: | :-: |
| **0** | 8 | 9 | 11 | 16 | 17 | 45 | 78 | 90 | 109 | 777 |

### Struktorgramm und Java Quellcode
::::tabs{id="Binäre Suche"}
:::tab{title="Binäre Suche" id="Struktog. binäre"}
:::
:::tab{title="Java binäre Suche" id="Java binäre Suche"}
```java
    
```
:::
:::tab{title="Binäre Suche optimiert" id="Struktog. binäre optimiert"}
:::
:::tab{title="Java binäre Suche optimiert" id="Java binäre Suche optimiert"}
```java
    
```
:::
::::