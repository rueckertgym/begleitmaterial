---
name: Modellierung
index: 2
toc: show
---
# Schülereigene Modellierung der Warteschlange

::::tabs

:::tab{title="ULM Diagram"}
```mermaid
classDiagram
Patient -->  Patient : - nachfolger
Warteschlange --> Patient : - vorne
      class Warteschlange{
          +patientenWarteschlange()
          +Patient gibErsten()
          +schickeErsten():void
          +hintenAnstellen(Patient pPatient):void        
        }
        class Patient{
        - String hatName
        -int hatKrknummer
          +Patient()
          +setNachfolger(Patient pPatient):void
          +getNachfolger()
          +setName(String pName):void
          +getName()
          +setKrknummer(int pKrknummer):void
          +getKrknummer():void
          }
 ```
:::

:::tab{title="Konstruktor"}

```java
    public Schulgraph()
    {
        // Aufbau des Schulgraphen in Form 18.04.2023
        g = new Graph();
        
        //alle Kanten und Knoten werden deklariert und initialisiert
        Vertex rueckertstr = new Vertex("Rückertstraße");
        Vertex lz = new Vertex("LZ");
        Edge rueckertstrLz = new Edge(rueckertstr, lz, 140);
        Vertex sekretariat = new Vertex("Sekretariat");
        Edge rueckSekr = new Edge(rueckertstr, sekretariat, 251);
        Vertex stundenplanerin = new Vertex("Stundenplanerin");
        Edge sekrStund = new Edge(sekretariat, stundenplanerin, 16);
        Vertex hausmeister = new Vertex("Hausmeister");
        Edge sekrHaus = new Edge(sekretariat, hausmeister, 44);
        Vertex mensa = new Vertex("Mensa");
        Edge hausMensa = new Edge(hausmeister, mensa, 103); 
        Vertex oberstufenbuero = new Vertex("Oberstufenbüro");
        Edge hausOber = new Edge(hausmeister, oberstufenbuero, 32);
        Edge oberMensa = new Edge(oberstufenbuero, mensa, 65);
        Vertex raum_1070 = new Vertex("Raum 1070");
        Edge ober_1070 = new Edge(oberstufenbuero, raum_1070, 66);
        Vertex schulleitung_rh = new Vertex("Schulleitung RH");
        Edge stundenSchul = new Edge(stundenplanerin, schulleitung_rh, 8);
        Vertex robotikraum = new Vertex("Robotikraum");
        Vertex sporthalle = new Vertex("Sporthalle");
        Edge roboSport = new Edge(robotikraum, sporthalle, 253);
        Vertex raum__1029 = new Vertex("Raum -1029");
        Edge sekr_1029 = new Edge(sekretariat, raum__1029, 174);
        Edge sport_1029 = new Edge(sporthalle, raum__1029, 277);
        Vertex schulleitung_pz = new Vertex("Schulleitung PZ");
        Edge schul_1029 = new Edge(schulleitung_pz, raum__1029, 168);
        Vertex sporthalle2 = new Vertex("Sporthalle 2");
        Edge sport2_1029 = new Edge(sporthalle2, raum__1029, 211);
        Vertex wasserspender = new Vertex("Wasserspender");
        Edge wasserRH = new Edge(wasserspender, schulleitung_rh, 30);
        Vertex koordinatoren = new Vertex("Koordinatoren Ober_ und Mittelstufe");
        Edge wasserKoor = new Edge(wasserspender, koordinatoren, 50);
        Vertex tischtennisplatte = new Vertex("Tischtennisplatte");
        Edge wassertennis = new Edge(wasserspender, tischtennisplatte, 130);
        Vertex klettergeruest = new Vertex("Klettergerüst");
        Edge kletter_1029 = new Edge(klettergeruest, raum__1029, 207);
        Edge robo_1029 = new Edge(robotikraum, raum__1029, 6);
        Vertex franzstr = new Vertex("St. Frankziskus Str.");
        Edge rueckertfranz = new Edge(rueckertstr, franzstr, 269);
        Edge franzkletter = new Edge(klettergeruest, franzstr, 70);
        Vertex bistro = new Vertex("Bistro");
        Edge bistroMensa = new Edge(mensa, bistro, 6);
        Edge bistro_1029 = new Edge(raum__1029, bistro, 140);
        Vertex archiv = new Vertex("Archiv");
        Vertex fahrradkeller = new Vertex("Fahrradkeller");
        Vertex raum_1013 = new Vertex("Raum 1013");
        Edge schulleitungen = new Edge(schulleitung_rh, schulleitung_pz, 18);
        Edge schularchiv = new Edge(schulleitung_rh, archiv, 120);
        Edge fahrradarchiv = new Edge(fahrradkeller, archiv, 7);
        Edge fahrrad_1013 = new Edge(fahrradkeller, raum_1013, 130);

        //die Knoten und Kanten werden dem Graphen hinzugefügt
        g.addVertex(rueckertstr);
        g.addVertex(lz);
        g.addVertex(sekretariat);
        g.addVertex(stundenplanerin);
        g.addVertex(hausmeister);
        g.addVertex(mensa);
        g.addVertex(oberstufenbuero);
        g.addVertex(raum_1070);
        g.addVertex(schulleitung_rh);
        g.addVertex(robotikraum);
        g.addVertex(sporthalle);
        g.addVertex(raum__1029);
        g.addVertex(schulleitung_pz);
        g.addVertex(sporthalle2);
        g.addVertex(wasserspender);
        g.addVertex(koordinatoren);
        g.addVertex(tischtennisplatte);
        g.addVertex(klettergeruest);
        g.addVertex(franzstr);
        g.addVertex(bistro);
        g.addVertex(archiv);
        g.addVertex(fahrradkeller);
        g.addVertex(raum_1013);

        g.addEdge(rueckertstrLz);
        g.addEdge(rueckSekr);
        g.addEdge(sekrStund);
        g.addEdge(sekrHaus);
        g.addEdge(hausMensa);
        g.addEdge(hausOber);
        g.addEdge(oberMensa);
        g.addEdge(ober_1070);
        g.addEdge(stundenSchul);
        g.addEdge(roboSport);
        g.addEdge(sekr_1029);
        g.addEdge(sport_1029);
        g.addEdge(schul_1029);
        g.addEdge(sport2_1029);
        g.addEdge(wasserRH);
        g.addEdge(wasserKoor);
        g.addEdge(wassertennis);
        g.addEdge(kletter_1029);
        g.addEdge(robo_1029);
        g.addEdge(rueckertfranz);
        g.addEdge(franzkletter);
        g.addEdge(bistroMensa);
        g.addEdge(bistro_1029);
        g.addEdge(schulleitungen);
        g.addEdge(schularchiv);
        g.addEdge(fahrradarchiv);
        g.addEdge(fahrrad_1013);
    }

```

:::


:::tab{title="Adjazensmatrix"}
```java

  public double[][] admatrixRueckgabe()
    {
        this.admatrix = new double[zaehleKnoten()][zaehleKnoten()];
        List<Vertex> hilfe = new List<Vertex>();
        hilfe = g.getVertices();
        hilfe.toFirst();
        int z = 0;
        List<Edge> Knotenhelfer = new List<Edge>();
        Knotenhelfer = g.getEdges(hilfe.getContent());
        Knotenhelfer.toFirst();

        List<Vertex> nachfolger = new List<Vertex>();
        while(hilfe.hasAccess())
        {
            nachfolger.append(hilfe.getContent());
            hilfe.next();
        }
        hilfe.toFirst();
        nachfolger.toFirst();
        Vertex aktueller = hilfe.getContent();
        Vertex naechsterVertex = nachfolger.getContent(); 
        for (int i = 0; i<zaehleKnoten(); i++)
        {
            for(int j = 0; j<zaehleKnoten(); j++)
            {               
                aktueller = hilfe.getContent();
                naechsterVertex = nachfolger.getContent(); 
                Edge kante =g.getEdge(aktueller, naechsterVertex);
                if (kante!= null)
                {
                    admatrix [i][j] = kante.getWeight();
                }
                else 
                {
                    admatrix [i][j] = -1.0;
                }
                nachfolger.next();               
            }
            hilfe.next();
            //hilfe.toFirst();
            nachfolger.toFirst();
            //int u = i;
            //while(u<i)
            //{
            //nachfolger.next();
            //}
        }        
        return admatrix;
    }
    ```
:::

:::tab{title="Breitensuche"}
```java
    public List<Vertex> breitensuche(String pStart)
    {
        Vertex gesuchterKnoten = g.getVertex(pStart);
        return breitensucheIntern(gesuchterKnoten);
    }
    
    private List<Vertex> breitensucheIntern(Vertex pStart) {       
        List<Vertex> ergebnisListe = new List<Vertex>();  
        Queue<Vertex> schlange = new Queue<Vertex>();
        pStart.setMark(true);
        schlange.enqueue(pStart);
        while (!schlange.isEmpty()) {
            Vertex aktuellerKnoten = (Vertex) schlange.front();
            schlange.dequeue();
            ergebnisListe.append(aktuellerKnoten);
            List<Vertex> nachbarListe = g.getNeighbours(aktuellerKnoten);
            nachbarListe.toFirst();
            while (nachbarListe.hasAccess()) {
                Vertex knoten = (Vertex) nachbarListe.getContent();
                if (!knoten.isMarked()) {
                    knoten.setMark(true);  
                    schlange.enqueue(knoten);
                }
                nachbarListe.next();  
            }
        }
        return ergebnisListe;
    }

```
:::

:::tab{title="Tiefensuche"}
```java
    private List<Vertex> tiefendurchlaufIntern(Vertex pStart) {       
        List<Vertex> ergebnisListe = new List<Vertex>();
        if (!pStart.isMarked()) {
            pStart.setMark(true);
            ergebnisListe.append(pStart);
            List<Vertex> nachbarliste = g.getNeighbours(pStart);
            nachbarliste.toFirst();
            while (nachbarliste.hasAccess()) {
                Vertex nV = (Vertex) nachbarliste.getContent();
                ergebnisListe.concat(tiefendurchlaufIntern(nV));
                nachbarliste.next();
            }
        }
        return ergebnisListe;
    }
    
    public List<Vertex> tiefendurchlauf(String pStart)
    {
        Vertex gesuchterKnoten = g.getVertex(pStart);       
        return tiefendurchlaufIntern(gesuchterKnoten);
    }
```
:::
::::
## Klassendokumentation 

###  ohne Knoten
**Klasse Warteschlange**

**patientenWarteschlange()**

Ein Objekt der Klasse Warteschlange wird erzeugt.

**Patient gibErsten()**

Der erste Patient in der Warteschlange zurückgegeben.

**void schickeErsten()**

Der erste Patient wird gelöscht bzw. aus der Warteschlange entlassen. Der zweite wird dann der erste Patient, der dritte wird der zweite usw.

**void hintenAnstellen(Patient pPatient)**

Die Methode sucht den Patient, der keinen Patienten mehr hinter sich hat. Dort wird der pPatient anghängt und ist nun der letzte. Wenn kein Patient in der Warteschlange ist, dann wird der pPatient der erste in der Warteschlange.

**Klasse Patient**

**Patient()**

**void setNachfolger(Patient pPatient)**

Setze Methode für den Nachfolger eines Patienten durch einen weiteren Patienten pPatient.

**getNachfolger()**

Die Anfrage gibt den Nachfolger des aktuellen Patienten wieder.

**void setName(String pName)**

Setze Methode für den Namen auf den Wert des Parameters pName.

**getName()**

Die Anfrage gibt den Namen des Patienten Text wieder.

**setKrknummer(int pKrknummer)**

Setze Methode für die Krknummer auf den Wert des Parameters pKrknummer.

**void getKrknummer()**

Die Anfrage gibt die Krknummer des Patienten wieder.

### mit Knoten
**Queue**

# Zentralbiturklasse Queue des Landes NRW
## Dokumentation der generischen Klasse Queue
Objekte der generischen Klasse Queue (Schlange) verwalten beliebige Objekte vom Typ ContentType nach dem First-In-First-Out-Prinzip, d. h., das zuerst abgelegte Objekt wird als erstes wieder entnommen. Alle Methoden haben eine konstante Laufzeit, unabhängig von der Anzahl der verwalteten Objekte.

### Dokumentation der Klasse Queue<ContentType> Queue()
Eine leere Schlange wird erzeugt. Objekte, die in dieser Schlange verwaltet werden, müssen vom Typ ContentType sein.

**boolean isEmpty()**

Die Anfrage liefert den Wert true, wenn die Schlange keine Objekte enthält, sonst liefert sie den Wert false.

**void enqueue(ContentType pContent)**

Das Objekt pContent wird an die Schlange angehängt. Falls pContent gleich null ist, bleibt die Schlange unverändert.

**void dequeue()**

Das erste Objekt wird aus der Schlange entfernt. Falls die Schlange leer ist, wird sie nicht verändert.

**ContentType front()**

Die Anfrage liefert das erste Objekt der Schlange. Die Schlange bleibt unverändert. Falls die Schlange leer ist, wird null zurückgegeben.

## Implementation
Die Implementation der ZA Klasse Queue findet ihr auf der Seite der standardsicherung oder im Kapitel ["Unser Fahrplan bis zum Abitur 2024](/formales/01_Unser_Fahrplan_zum_Abitur_2024.md).

 
