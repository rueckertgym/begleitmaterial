---
name: List S. 75 Nr. 2
index: 2
toc: show
---

# List Lösung von <Zagros und Marouane>
```java
import java.util.Scanner;

public class Vokabeltrainer
{
    public void main(){
        Scanner sc = new Scanner(System.in);
        List<Vocabulary> vocList = new List<>();
        List<Vocabulary> vocList2 = new List<>();
        while(true){
            System.out.println("Wähle eine Option:");
            System.out.println("1) Vokabel hinzufügen");
            System.out.println("2) Vokabel abfragen");
            System.out.println("3) Vokabeltrainer beenden");
            int option = sc.nextInt();
            sc.nextLine();
            if(option == 1){
                System.out.println("Deutsches Wort: ");
                String gerWord = sc.nextLine();
                System.out.println("Übersetzung: ");
                String translation = sc.nextLine();
                Vocabulary vocabulary = new Vocabulary(gerWord, translation);
                vocList.append(vocabulary);
                System.out.println("Vokabel hinzugefügt\n");
            }
            else if (option == 2) {
                for(int i = 0; i<vocList.getSize(); i++){
                    Vocabulary vocabulary = vocList.get(i);
                    System.out.println(vocabulary.getGerWord());
                    System.out.println("Übersetzung: ");
                    String translation = sc.nextLine();
                    if(vocabulary.getTranslation().equals(translation)){
                        System.out.println("Richtig!\n");
                    }
                    else{
                        System.out.println("Leider falsch; richtig wäre: "+vocabulary.getTranslation()+"\n" );
                        vocList2.append(vocList.get(i));
                    }
                }
                for(int j = 0; j<vocList2.getSize(); j++){
                    Vocabulary vocabulary = vocList2.get(j);
                    System.out.println(vocabulary.getGerWord());
                    System.out.println("Übersetzung: ");
                    String translation = sc.nextLine();
                    if(vocabulary.getTranslation().equals(translation)){
                        System.out.println("Richtig!\n");
                    }
                    else{
                        vocList2.append(vocList.get(j));
                    }
                }
            }
            else if (option == 3) {
                break;
            } 
            else {
                System.out.println("Ungültige Option");
            }

        }
    }
}

public class Vocabulary
{
    private String gerWord;
    private String translation;
    
    public Vocabulary(String gerWord, String translation){
        this.gerWord = gerWord;
        this.translation = translation;
    }
    
    public String getGerWord(){
    return gerWord;
    }
    
    public String getTranslation(){
    return translation;
    }
}


```
