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

::struktog{data="https://struktog.openpatch.org/#pako:eNqVVdtu00AQ_RXjpyJ10N4vrfoCQgIJEL8wuzNLLFwnSh0KQv13JkB6ARJhv1he27PnnDln9nt_vSYe-4vv_UD9Re-cxZAMgSqtgc2mArmAEJPVtlDoz_v524bly7fTDW_nD_K3rLX1OK5vX498zdN8X4wSoU3yNxtXITqjIJmsAHWphVp8XGyzO9Sa-auU6N_zvJKFi-4jzoNU7W5mHsdR7kNddTh1h-vo9smhjYgaolIWkKMB21oGQhN1CmURlxZMKYwWXLAMOuYMQSNBIkXZO3OSy2ZXxqF2X9YDCfKfRHjqzja_qT0_uquyLYeWGrBGD4V0gWxyAk6NUwxqEYVqqkuoiuhBUidUBspCBqMxpUZ9ksKhC_h53u3hbw8LV0JrO3F3ebwRJijtnfKgEmnIrhXphjwaZZVuDZc1goy30SIEVxO46Akq6gzFY8PK-aHYyy1OdfWUxtDOfsG9uuqm3Tgel54cSg4ogW-YIaOoTlgzKFLN1Pyf7tnvcSdfbnf8ajWM9NCMlosuoYBJ3gNWb8FkCmIq57yOcZkmjXPxWYIWqsQrmAboWQBnZ3T09mRnf-vRHdx4eXSbXJtuaB1wlO4lZbUEoUVAxcbXzAskuRNRGo43f6gSrNcBLUExQfwRnQPliwOvyZWgzDK_V2X93urVNgYfuUAI1kB1VELV9FDsDSO9W683T4W5FWj8l-FffOL5zTDNPJ097579ctFRCFww7VGAxhLBeBmsQkQBZ5tjLWqRieoTqdgj-5YNOGxeQpUDGDZCMZWCTttFUmlTUtqPmOC4icVdlnCGALHWZNiFkwbq_jUUTsl23GHVuaR8sBCJpGVEMrK9jD_lrKWY6sJ5ZykzNWikMlgr4U3Ja6jZeafNaVJ_4b-5x38_to_zSDZ5DFEOT5Jh5yXpUFXdH6PeStv9oqQ8vs77FQ-fVvLSxHje3w40r_qLlOPdD2yTask"}

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

