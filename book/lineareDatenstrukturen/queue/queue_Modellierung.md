---
name: Modellierung
index: 2
toc: show
---


::::tabs

:::tab{title="Video"}

::youtube[01 Lineare Datenstrukturen:  Queue ohne Knoten ]{#fd2Ty1Jkw00}
:::

:::

:::tab{title="ULM Diagram"}
```mermaid
classDiagram
      class Warteschlange{
      - Patient vorne
          +patientenWarteschlange()
          +Patient gibErsten()
          +schickeErsten():void
          +hintenAnstellen(Patient pPatient):void        
        }
        class Patient{
        -Patient nachfolger
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

:::tab{title="Struktogram"}

Das Struktogram für wenn der erste die Queue verlässt.


::struktog{data="https://struktog.openpatch.org/#pako:eNqVVE1vE0EM_SvRnlqpRvPl-UiVCwgJDiAOSJw9M3ay6naDthsKqvrfmUBLoShRM6eVZ_Y9-_nZd931tvLQLe-6vnbLzjlLPpoKKouATaZAdZ4gRKttrr676OYfX7m9fD_e8DR_bH-3mGyHYXv7duBrHuc_YDaaKMoWsNU5UBwDJNdgVcLgvPkL7DPdXD1Azfy9IXQfeN60wHLxhddr3vB4kCWToYrVQ3RioOhEkD0psMUHb5hOSrmQNVGlAFStA6T2ZdqBKGQM1nIs5U809w1rQVfzjoeBp8fAavFtO428uFwc5I0GfawhA2sJoIwv4HLN4FTURkw4qQipBm2wBN6VCC5ghUI6QUYSKpyewF5PNJbNv2X0cvY73dVqMe6G4fwgT3XUrFIjoFCCRClCpZJAVSWmpPyypPcc9-3ltOM3m36oT72QlHX2GUxEBCpowaTWZ6-dQx1O0wSLWCPsIYg0JZgsWNekjkk3dMXHGjvxvJvGX2JcHiTQbDEZrg3WZahJNdP4Zvu4Hx2ReoIY900OoeHmmR7eovZkK2TjEUzYzxTm5lJdXfbKnOYR1iRiLSQuDkiShhBMBMHKIjod02Px4OfVf1Z_teb5XT_OPJ6dH5bKB4uYiwLxjVazctBagVBiMVViOqkQ3RaJU9xWS0TfpKnY1lZEyFFFLKxf0NjnVRyZU1ds0gk1cGlut1T2ls8aitOEjHJSlx_PRbfhfr1pFzq5i-62r_OmW8YU7n8Cs8K5-A"}

Das Struktogram, für wenn entwas hinten angehängt wird. 

::struktog{data="https://struktog.openpatch.org/#pako:eNqVVdtu3FYM_BVVTw5gFud-ceCHpCiQAkXRh_4AzyHpFaJojV25bhH430sjjh033UW1AvZBl-FwOJzzefy0J57Hq8_jROPVGILHVByBaSLgq-tAISHk4q1vlMbLcf37lvXNX5YjH9bf9Gu9J_t53t__PPMnXtZnMJ9rizURWBMJiqQEtbMFCS1LSPQC9gcePz5BrfyXIozvlnuejnfLzUl0U6kW3xhcVpbZMgK5UoEzkTOmb6KKJOyFM8TYKxQUgmS7BymGY4z2HNXbuzZPffhzP9GAy3HleeZluLj9HddJa7w5WbQXH4tnrdergxRrBetNhpwws16bOnCm6-TEAFFxOjkOYDB0SEwKF_y5Dp6YDvhxvXtkf_h641q7Oiw8vB1O1iVkJ5gJOKBAizZAE6s0EL0hsZuaEHLRZ4-QQi8Qstqmo60Ki4Kd6wvY-wMuffe6jUkuvtC9vh6Wu3k-rTwFVJNTgShYoWItylcHb8iI67X9P9KPNR70zcMd_7SbZnoZrNRmW2rgSoyAPXpwlZJaKoRo87bBMqLY7oLKoYNtMau2Vl2Sug1SKJ8b7JMcw1cvvj3txaiMPelyYkMIJqlzihGI1UZjcIsiD6qJ4Hz8lyjJR5vQEzSXoi5tUIPGFiBaCi0Zt0mU3o2Phhp03VqImRuk5B30QE2F-SZaPjDSr_v97Wth7pUaf-f3H294_TAtKy8Xb4Yfvpjo9FwalkcWYLFlcFFDUxsxwNXX3JvZ5KH-SiqOyFE0E3SlItRQEzh22mJpDYP126RKsWQvFdC0pn9dF5SdhcrG-ebknH-G_4qEc6qdNliV1nxJFWKXrNHUEui2q9WIrc-5bjtZSq5cSc0j4sA1aaAnQQA2obkqZ-P6O_rHZ_rPkX26DeRepPgAiCVAMU4PnKaB1RMH1yVt2pNvf5fjjqebnT50sVyO9xOtu_Gq1PzwD5bCYUk"}

:::

::::

# Quellcode
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
# Klassendokumentation 

**patientenWarteschlange()**

Ein Objekt der Klasse Warteschlange wird erzeugt.

**Patient gibErsten()**

Der erste Patient in der Warteschlange zurückgegeben.



**void schickeErsten()**

Der erste Patient wird gelöscht bzw. aus der Warteschlange entlassen. Der zweite wird dann der erste Patient, der dritte wird der zweite usw.

**void hintenAnstellen(Patient pPatient)**

Die Methode sucht den Patient, der keinen Patienten mehr hinter sich hat. Dort wird der pPatient anghängt und ist nun der letzte. Wenn kein Patient in der Warteschlange ist, dann wird der pPatient der erste in der Warteschlange.

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

**Queue**

