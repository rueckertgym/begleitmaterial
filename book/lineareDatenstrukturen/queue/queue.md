---
name: Queue
index: 1
toc: show
---

# Queue

Eine Queue (deutsch: Warteschlange) ist eine dynamische Datenstrucktur. Die Warteschlange funktioniert nach dem First-In-First-Out Prinzip (abgekürzt: FIFO). Das bedeutet, dass das Element, das zuerst gespeichert wird auch zuerst die Queue wieder verlässt. 





::::tabs

:::tab{title="Video"}
[Link](#) zum Video

:::

:::tab{title="ULM Diagram"}
```mermaid
classDiagram
Warteschlange <|-- Patient
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


::struktog{data="https://struktog.openpatch.org/#pako:eNqVVMtu1EAQ_BXLp0RKo3n0vDbaCwgJDiBunHtmenZXON7I8RJQlH-nA4RA0K5i39yeqa6uqvZdf7WvPPSru35X-1WPaMlHU0Hl1sAmU6CiJwjRapur7y_6-fs1y8n34w1P80e5LbW2H4b97duBr3ic_4DVWMlGuc0GCwQ0CqJJCkjnkmsLf4NdHx6xZv4mEP0HnrdSWHWfebPhLY9H20QkG4g0BKUsEAcDtrUElUzQ0edFnIspGEllAasZki8MNVkGCsbkEvRJzp9o3glYR1_mAw8DT4-Fdfd1P43cXXZHGxuvtEPlQMWqIWHLMoq8GmWVbo0WTdGqcTZYAo8lAgZXoZBOkB01KpyewF5PNJbtv2Ps2tkvuut1Nx6G4fy4w0gSlhrBNUqQKEVRvSRQVTVT0gulf-hxLyenA7_Z7ob6ZEZLWWefwUTngIqzYFL14DWi0yEs06Rxyi5JGn2RDHrTgBwL4YRGB2dPOjvxfJjGn2pcHu2QStONLAIHMS4qq0GHFoAUG1cSL1DjXvRoNNw8E8Rbpz3ZCtl4iUZABOUygtMVs1dmkSDa5Bg1OQkJN7EMk4TNewilRMPoTwrS_U70-r-wv9rw_G43zjyenR_XqiBG5byFUCuDq1WW1kWhgdbWEMuiSQz7YCox5Car6q1vwC4hoJHtqexeYu3zMU6sajbc0LQHnyWMqZYCKkT5ueWgvdVhkc-Pz0W_5d1mKx90wov-dlfnbb-KKdz_AKM7vSc"}

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
