---
name: List
index: 1
toc: show
---

# List

Eine Liste (englisch: **list**) ist ein Datenstrukturtyp der es ermöglicht, eine Sammlung von Elementen zu speichern und zu verwalten. Eine Liste ist ein dynamisches Datenstruktur, das heißt, dass ihre Größe und ihr Inhalt sich während der Laufzeit eines Programms ändern können.

In der Regel können in einer Liste Elemente unterschiedlicher Typen gespeichert werden, beispielsweise Zahlen, Zeichenketten oder andere Objekte.

Um Elemente in einer Liste zu speichern und zu verwalten, werden in der Regel mehrere Methoden bereitgestellt, wie beispielsweise **add()** oder **remove()** zum Hinzufügen oder Entfernen von Elementen, **get()** oder **set()** zum Abrufen oder Ändern von Elementen an bestimmten Indizes und viele andere.

::::tabs{id="List"}

:::tab{title="Video Liste" id="Video Liste"}
::youtube[02 Lineare Datenstrukturen:  List ohne Knoten ]{#zSad1XVQ0hg}
:::

:::
:::tab{title="Struktogramm List" id="Struktogramm List"}
::struktog{data="https://struktog.openpatch.org/#pako:eNqVVMuOEzEQ_JXIp0VKI7ffjsQRJC65wA1xsNttEjF5KJnVgqL8O71iN8siJTBzsdzdLlfVlHxSm13jQS1Oat3UQgWtsza2gEHvIUZmaM0ReDI2murVXI0_9yyTH7dHPoxLOS21vhuG3cP7gTe8HV_AggsZmwakEkBrrBBMJdmir4HSC9iH-y2N6932CW7kH4KiSmsCuV8VwZyrfTmUDY98OKrFl5Pa72RV-ndjKR3ZPU_P9pdz5_nzqH01un6ckvr56zX2NlisrXTh7BAipQYaEwN2a4mS-T8rtvfDcJ4rWq2HdoFOOcXqqoeigxXAlEHsbVCr0diYJ7msQ0WHqYIxSRC9D4KTCWI2BVvFF7DP5fj9tcNHHj9xOdCK25248ebqJS12w60xUBL8XrsHDBzAR64xWprEmDCIzqQh15aAqmbwtiBgicaHXm4xvvzZt8J9KbW745OAp1uua3DIhUwyEL3QT0Z3aDFZMOS7y2aahpqLo14d6CqGWKMz-NQL2BJr9RRvabjEdNzsZ-9mfwm4bhsj6Zo7dDIR0IYGLhWCQtGEnvUk_ugNRxtY1JcEmJqDmkKVRGbrW6gTUjODGd5Ijg5RO3LAPVcgSTe4niOYji42PS3rTV4k7STcGMVwF6hAb6E8IrpE_8r6K5sv-bkk6roGecRKK5hBwq_B--ggeC6AjmJPkSY8BX9-c7Xi9beVtIxzc_WwbuNKLVKO519eXbtd"}
:::

:::tab{title="Java List" id="Java List"}
```java
public class List
{
    private Elephant firstElement;
    private Elephant searchedElement;
    private Elephant lastElement;
    /**
     * Konstruktor
     */
    public List(Elephant pElephant){
        firstElement = pElephant;
        lastElement = pElephant;
    }
    /**
    *Füge ein Element am Ende der Liste hinzu
    *@param Elephant pElephant
    */
    public void append(Elephant pElephant){
        lastElement.setNext(pElephant);
        lastElement = lastElement.getNext();
    }
    /**
    * Erhalte den Wert von einem Element an einer pestimten Position
    * @param int pos
    * @return Elephant searchedElement
    */
    public Elephant get(int pos){
        setSearched(pos);
        return searchedElement;
    }
    /**
    * Ändere das Element an einer bestimten Position
    * @param Elephant pElephant
    * @param int pos
    */
    public void set(Elephant pElephant, int pos){
        setSearched(pos);
        pElephant.setNext(searchedElement.getNext());
        remove(pos);
        add(pElephant, pos);
    }
    /**
    * Füge ein Element an einer bestimmten Position in der Liste hinzu
    * @param Elephant pElephant
    * @param int pos
    */
    public void add(Elephant pElephant, int pos){
        setSearched(pos);
        pElephant.setNext(searchedElement);
        Elephant tmp = searchedElement;
        setSearched(pos - 1);
        searchedElement.setNext(pElephant);
    }
    /**
    * Entfernt ein Element an einer bestimmten Position in der Liste
    * @param int pos
    */
    public void remove(int pos){
        setSearched(pos + 1);
        Elephant tmp = searchedElement;
        setSearched(pos - 1);
        searchedElement.setNext(tmp);
    }
    /**
     * interne Funktion die ein gesuchtes Element in einer Methodenübergreifenden Variable
     */
    private void setSearched(int pos){
        Elephant ele = firstElement;
        for(int i = 0; i < pos; i++){
            ele = ele.getNext();
        }
        searchedElement = ele;
    }
}```

:::
::::






























































