---
name: Modellierung
index: 2
toc: show
---
# Modellierung der Klasse Graph

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