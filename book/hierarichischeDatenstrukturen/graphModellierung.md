---
name: Graph Modellierung
index: 5
toc: show
---
# Modellierung der Klasse Graph

::::tabs

:::tab{title="ULM Diagram"}
```mermaid
classDiagram
Graph
Vertex

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