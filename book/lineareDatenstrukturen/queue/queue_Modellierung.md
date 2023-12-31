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

:::tab{title="BStruktogram"}



Struktogram der Methode zum Anfügung eines Objektes.

::struktog{data="https://struktog.openpatch.org/#pako:eNqVVdtu3FYM_BVVTw5gFud-ceCHpCiQAkXRh_4AzyHpFaJojV25bhH430sjjh033UW1AvZBl-FwOJzzefy0J57Hq8_jROPVGILHVByBaSLgq-tAISHk4q1vlMbLcf37lvXNX5YjH9bf9Gu9J_t53t__PPMnXtZnMJ9rizURWBMJiqQEtbMFCS1LSPQC9gcePz5BrfyXIozvlnuejnfLzUl0U6kW3xhcVpbZMgK5UoEzkTOmb6KKJOyFM8TYKxQUgmS7BymGY4z2HNXbuzZPffhzP9GAy3HleeZluLj9HddJa7w5WbQXH4tnrdergxRrBetNhpwws16bOnCm6-TEAFFxOjkOYDB0SEwKF_y5Dp6YDvhxvXtkf_h641q7Oiw8vB1O1iVkJ5gJOKBAizZAE6s0EL0hsZuaEHLRZ4-QQi8Qstqmo60Ki4Kd6wvY-wMuffe6jUkuvtC9vh6Wu3k-rTwFVJNTgShYoWItylcHb8iI67X9P9KPNR70zcMd_7SbZnoZrNRmW2rgSoyAPXpwlZJaKoRo87bBMqLY7oLKoYNtMau2Vl2Sug1SKJ8b7JMcw1cvvj3txaiMPelyYkMIJqlzihGI1UZjcIsiD6qJ4Hz8lyjJR5vQEzSXoi5tUIPGFiBaCi0Zt0mU3o2Phhp03VqImRuk5B30QE2F-SZaPjDSr_v97Wth7pUaf-f3H294_TAtKy8Xb4Yfvpjo9FwalkcWYLFlcFFDUxsxwNXX3JvZ5KH-SiqOyFE0E3SlItRQEzh22mJpDYP126RKsWQvFdC0pn9dF5SdhcrG-ebknH-G_4qEc6qdNliV1nxJFWKXrNHUEui2q9WIrc-5bjtZSq5cSc0j4sA1aaAnQQA2obkqZ-P6O_rHZ_rPkX26DeRepPgAiCVAMU4PnKaB1RMH1yVt2pNvf5fjjqebnT50sVyO9xOtu_Gq1PzwD5bCYUk"}

:::

:::tab{title="Quellcode ohne Knoten"}
```java
public class PatientenWarteschlange 
{
    private Patient vorne;

    public PatientenWarteschlange()
    {

    }

    public Patient gibErsten(){
        return vorne; 
    }

    public void schickeErsten() {
        Patient aktuellerPatient = vorne ;
        if( vorne!= null){
            vorne = aktuellerPatient.getNachfolger();
        }
    }

    public void hintenAnstellen(Patient pPatient)
    {
        Patient aktuellerPatient = vorne;
        if (vorne == null){
            vorne = pPatient; 
        }
        else{
            while(aktuellerPatient.getNachfolger() != null) {
                aktuellerPatient = aktuellerPatient.getNachfolger();
            }
            aktuellerPatient.setNachfolger(pPatient);
        }
    }
}

public class Patient
{
    private Patient nachfolger;
    private String hatName;
    private int hatKrknummer;

    public Patient(String pName, int pKrknummer)
    {
        this.hatName = pName;
        this.hatKrknummer = pKrknummer;
    }

    public void setNachfolger(Patient pPatient) {
        nachfolger = pPatient;
    }

    public Patient getNachfolger() {
        return nachfolger;
    }

    public void setName(String pName){
        hatName= pName;
    } 

    public String getName(){
        return hatName; 
    }

    public void setKrknummer(int pKrknummer){
        hatKrknummer= pKrknummer;
    } 

    public int getKrknummer(){
        return hatKrknummer; 
    }
}
```
:::

:::tab{title="Quellcode mit Knoten"}
```java
public class PatientenWarteschlange<T>{
    private Knoten vorne;
    /*
     * Konstruktor
     * Erstellt leere Queue
     */
    public PatientenWarteschlange(){
        vorne = null;
    }
    /*
     * Gibt das erste Objekt der Queue zurück
     */
    public T gibErsten(){
        return vorne.getZeigeAuf();
    }
    /*
     * Ertfernt das erste Objekt aus der Queue
     */
    public void schickeErsten(){
        if( vorne.getNachfolger()!= null){
            vorne = vorne.getNachfolger();
        }
    }
    /*
     * Fügt ein neues Element am Ende der Queue hinzu
     */
    public void hintenAnstellen(T pPatient){
        Knoten aktuellerPatient = vorne;
        Knoten neuerPatient = new Knoten(pPatient);
        neuerPatient.setNachfolger(null);
        if (vorne == null){
            vorne = neuerPatient;
        }
        else{
            while(aktuellerPatient.getNachfolger() != null) {
                aktuellerPatient = aktuellerPatient.getNachfolger(); 
            }
            aktuellerPatient.setNachfolger(neuerPatient);
        }
    }
    
    private class Knoten{
        private T zeigeAuf;                             //Speichert das Objekt auf welches der Knoten zeigt
        private Knoten nachfolger;                      //Speichert den nachfolgenden Knoten
        
        public Knoten(T pZeigeAuf){
            zeigeAuf = pZeigeAuf;
        }
        public Knoten getNachfolger(){
            return nachfolger;
        }
        public void setNachfolger(Knoten pNachfolger){
            this.nachfolger = pNachfolger;
        }
        public T getZeigeAuf(){
            return zeigeAuf;
        }
    }
}

public class Patient
{
    private String hatName;
    private int hatKrknummer;

    public Patient(String pName, int pKrknummer){
        this.hatName = pName;
        this.hatKrknummer = pKrknummer;
    }

    public void setName(String pName){
        hatName = pName;
    } 

    public String getName(){
        return hatName; 
    }

    public void setKrknummer(int pKrknummer){
        hatKrknummer= pKrknummer;
    } 

    public int getKrknummer(){
        return hatKrknummer; 
    }
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

 
