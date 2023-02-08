# Prüfungsvorbereitung alternative Lösung von Tim und Sarah

## a)
Eine Liste ist für die Modellierung einer Bowling-Rinne besser geeignet als eine Schlange, da die spielende Person nicht immer die erste Kugel wählen muss, sondern sich eine Aussuchen kann. Anders als das first-in-first-out Prinzip der Schlange ist das interagieren mit einem Liste nämlich felixbel.

---

## b)
```java
public class Kugel{
    
    private String farbe;
    private int gewicht;
    
    public Kugel(String farbe){
        switch(farbe){            
            case "blau":
                this.farbe = farbe;
                this.gewicht = 10;
                break;
                
            case "gelb":
                this.farbe = farbe;
                this.gewicht = 8;
                break;
                
            case "rosa":
                this.farbe = farbe;
                this.gewicht = 6;
                break;
                
            default:
                System.out.println("angegebene Farbe nicht verfügbar");
        }
    }
}
```
---
## c)
### Kursimplimentation
```java
import java.util.HashMap;

public class Bowlingbahn{
    
    private Q1Liste<Kugel> rinne = new Q1Liste();
    
    public Bowlingbahn(){
        
    }
    
    
    public void kugelHinzufuegen(Kugel pKugel){
        rinne.append(pKugel);
    }
    
    
    public void kugelEntfernen(){
        
    }
    
    
    public String haefigsteFrabe(){
        
        String haeufigsteFarbe = "";
        HashMap<String, Integer> anzahl = new HashMap();
        
        anzahl.put("rosa", 0);
        anzahl.put("gelb", 0);
        anzahl.put("blau", 0);
        
        for(int i = 0; i < rinne.getSize(); i++){
            String aktuelleFarbe = rinne.get(i).getFarbe();
            anzahl.put(aktuelleFarbe, anzahl.get(aktuelleFarbe) + 1);
        }
        
        String zuvorigeFarbe = "";
        
        for(String farbe : anzahl.keySet()){
            
            if(zuvorigeFarbe != ""){
                if(anzahl.get(farbe) > anzahl.get(zuvorigeFarbe)){
                    haeufigsteFarbe = farbe;
                }
            }
            else{
                haeufigsteFarbe = farbe;
            }
            zuvorigeFarbe = farbe;
        }
        
        return haeufigsteFarbe;
    }
    
    
}
```

### ZA-Implimentation
```java
import java.util.HashMap;

public class ZABowlingbahn{
    
    private ZAListe<Kugel> rinne = new ZAListe();
    
    public ZABowlingbahn(){
        
    }
    
    
    public void kugelHinzufuegen(Kugel pKugel){
        rinne.append(pKugel);
    }
    
    
    public void kugelEntfernen(){
        
    }
    
    
    public String haefigsteFrabe(){
        
        String haeufigsteFarbe = "";
        HashMap<String, Integer> anzahl = new HashMap();
        ZAListe<Kugel> tmp = rinne;
        
        anzahl.put("rosa", 0);
        anzahl.put("gelb", 0);
        anzahl.put("blau", 0);
        
        while(!tmp.isEmpty()){
            tmp.toFirst();
            String aktuelleFarbe = tmp.getContent().getFarbe();
            tmp.remove();
            anzahl.put(aktuelleFarbe, anzahl.get(aktuelleFarbe) + 1);
        }
        
        String zuvorigeFarbe = "";
        
        for(String farbe : anzahl.keySet()){
            
            if(zuvorigeFarbe != ""){
                if(anzahl.get(farbe) > anzahl.get(zuvorigeFarbe)){
                    haeufigsteFarbe = farbe;
                }
            }
            else{
                haeufigsteFarbe = farbe;
            }
            zuvorigeFarbe = farbe;
        }
        
        return haeufigsteFarbe;
    }
    
    
}
```
---
## d)
### Staender.java
```java
import java.util.Arrays;

public class Staender
{
    public Kugel[] vorrat = new Kugel[20];
    
    public Staender(){
        
    }
    
    public void setVorrat(Kugel[] pVorrat){
        vorrat = pVorrat;
    }
    public void vorratAusgeben(){
        System.out.println(Arrays.toString(vorrat));
    }
}

```
### Spieler.java
```java
public class Spieler
{
    public Spieler(){
        
    }
    
    private Kugel blau(){
            Kugel pblau = new Kugel("blau");
            return pblau;
    }
    
    private Kugel gelb(){
            Kugel pgelb = new Kugel("gelb");
            return pgelb;
    }
    
    private Kugel rosa(){
            Kugel prosa = new Kugel("rosa");
            return prosa;
    }
    
    public void setupAufgabe(){
        Kugel[] k1 = {new Kugel("gelb"),new Kugel("rosa"),new Kugel("gelb"),new Kugel("rosa"),new Kugel("rosa"),new Kugel("blau"),new Kugel("rosa"),new Kugel("rosa"),new Kugel("gelb"),new Kugel("rosa"),new Kugel("rosa"),new Kugel("rosa"),new Kugel("rosa"),new Kugel("gelb"),new Kugel("rosa"),new Kugel("rosa"),new Kugel("gelb"),new Kugel("gelb"),new Kugel("rosa"),new Kugel("rosa")};
        Kugel[] k2 = {new Kugel("rosa"),new Kugel("gelb"),new Kugel("rosa"),new Kugel("gelb"),new Kugel("rosa"),new Kugel("gelb"),new Kugel("rosa"),new Kugel("rosa"),new Kugel("rosa"),new Kugel("gelb"),new Kugel("rosa"),new Kugel("gelb"),new Kugel("rosa"),new Kugel("gelb"),new Kugel("rosa"),new Kugel("gelb"),new Kugel("rosa"),new Kugel("gelb"),new Kugel("rosa"),new Kugel("blau")};
        Kugel[] k3 = {new Kugel("gelb"),new Kugel("rosa"),new Kugel("rosa"),new Kugel("gelb"),new Kugel("blau"),new Kugel("rosa"),new Kugel("gelb"),new Kugel("rosa"),new Kugel("rosa"),new Kugel("rosa"),new Kugel("rosa"),new Kugel("rosa"),new Kugel("gelb"),new Kugel("rosa"),new Kugel("rosa"),new Kugel("rosa"),new Kugel("rosa"),new Kugel("rosa"),new Kugel("gelb"),new Kugel("gelb")};
        Kugel[] k4 = {new Kugel("rosa"),new Kugel("gelb"),new Kugel("rosa"),new Kugel("rosa"),new Kugel("gelb"),new Kugel("rosa"),new Kugel("gelb"),new Kugel("rosa"),new Kugel("blau"),new Kugel("rosa"),new Kugel("rosa"),new Kugel("gelb"),new Kugel("gelb"),new Kugel("rosa"),new Kugel("rosa"),new Kugel("rosa"),new Kugel("gelb"),new Kugel("gelb"),new Kugel("gelb"),new Kugel("rosa")};
        Kugel[] k5 = {new Kugel("rosa"),new Kugel("gelb"),new Kugel("gelb"),new Kugel("rosa"),new Kugel("rosa"),new Kugel("rosa"),new Kugel("rosa"),new Kugel("gelb"),new Kugel("gelb"),new Kugel("rosa"),new Kugel("rosa"),new Kugel("blau"),new Kugel("gelb"),new Kugel("gelb"),new Kugel("rosa"),new Kugel("gelb"),new Kugel("gelb"),new Kugel("rosa"),new Kugel("rosa"),new Kugel("gelb")};
        Staender steanderEins = new Staender();
        steanderEins.setVorrat(k1);
        Staender steanderZwei = new Staender();
        steanderZwei.setVorrat(k2);
        Staender steanderDrei = new Staender();
        steanderDrei.setVorrat(k3);
        Staender steanderVier = new Staender();
        steanderVier.setVorrat(k4);
        Staender steanderFuenf = new Staender();
        steanderFuenf.setVorrat(k5);
        Staender[] s = {steanderEins, steanderZwei, steanderDrei, steanderVier, steanderFuenf};
        methode1(s);
        for(int i = 0; i < s.length; i++){
            s[i].vorratAusgeben();
        }
    }
    
    
    public void methode1(Staender[] pStaender){
        for(int a = 0; a < 100; a++){
            for(int i = 0; i < pStaender.length; i++){
                for(int j = 0; j < 20; j++){
                    Kugel aktKugel = pStaender[i].vorrat[j];
                    if(aktKugel.getFarbe().equals("blau")){
                        if(j < 19){
                            Kugel hilf = aktKugel;
                            pStaender[i].vorrat[j] = pStaender[i].vorrat[j+1];
                            pStaender[i].vorrat[j+1] = hilf;
                        }
                        else{
                            if(i < pStaender.length - 1){
                                Kugel hilf = aktKugel;
                                pStaender[i].vorrat[j] = pStaender[i+1].vorrat[0];
                                pStaender[i+1].vorrat[0] = aktKugel;
                            }
                        }
                    }
                }
            }
        }
    }
}

```
### Kugel.java
```java
public class Kugel{
    
    private String farbe;
    private int gewicht;
    
    public Kugel(String farbe){
        switch(farbe){            
            case "blau":
                this.farbe = farbe;
                this.gewicht = 10;
                break;
                
            case "gelb":
                this.farbe = farbe;
                this.gewicht = 8;
                break;
                
            case "rosa":
                this.farbe = farbe;
                this.gewicht = 6;
                break;
                
            default:
                System.out.println("angegebene Farbe nicht verfügbar");
        }
    }
    
    public String getFarbe(){
        return this.farbe;
    }
    public int getGewicht(){
        return this.gewicht;
    }
    @Override
    public String toString(){
        return(this.farbe);
    }
}
```
## Ergebniss:

- [gelb, rosa, gelb, rosa, rosa, rosa, rosa, gelb, rosa, rosa, rosa, rosa, gelb, rosa, rosa, gelb, gelb, rosa, rosa, rosa]
- [gelb, rosa, gelb, rosa, gelb, rosa, rosa, rosa, gelb, rosa, gelb, rosa, gelb, rosa, gelb, rosa, gelb, rosa, gelb, rosa]
- [rosa, gelb, rosa, gelb, rosa, rosa, rosa, rosa, rosa, gelb, rosa, rosa, rosa, rosa, rosa, gelb, gelb, rosa, gelb, rosa]
- [rosa, gelb, rosa, gelb, rosa, rosa, rosa, gelb, gelb, rosa, rosa, rosa, gelb, gelb, gelb, rosa, rosa, gelb, gelb, rosa]
- [rosa, rosa, rosa, gelb, gelb, rosa, rosa, gelb, gelb, rosa, gelb, gelb, rosa, rosa, gelb, blau, blau, blau, blau, blau]
