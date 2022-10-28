---
name: Verschlüsselung
index: 1
toc: show
---

# Viginère Verschlüsselung

Die Vigenère-Verschlüsselung zählt zu den polyalphabetischen Chiffren. Der französische Diplomat Blaise de Vigenère erfand 1586 ein Chiffresystem, dessen Grundidee einfach und zu-gleich sehr effektiv ist: Den Wechsel zwischen mehreren monoalphabetischen Chiffrierungen. Um eine Vigenère-Chiffre zu erzeugen, braucht man zum einen ein Schlüsselwort und zum anderen ein **Vigenère-Quadrat**, welche auch **Trithemius-Tafel** genannt wird:

![Vigenère Quadrat](/Bilder/Kryptologie/vigenerequadrat.png "Vigenère Quadrat")


## Verwendung dieses Quadrates
Man schreibt die zu verschlüsselnde Botschaft auf und darunter das Schlüsselwort. Das Schlüsselwort wird solange hintereinander aufgeschrieben, bis es mindestens die Länge der zu verschlüsselnden Botschaft hat (Leerzeichen werden dabei ignoriert). 

Nun sucht man sich den Buchstaben der Botschaft, der gerade verschlüsselt werden soll in der ersten Zeile des Vigenère-Quadrates. Von dort aus geht man in dieser Spalte soweit hinunter, bis man ganz links den Buchstaben des Schlüsselwortes, der unter dem zu verschlüsselnden Buchstaben steht, gefunden hat. So ergibt sich nach und nach die verschlüsselte Botschaft.

Klartext: 
Schlüssel:

Geheimtext:

:::alert{info}
**Merke:**
1. Die erste Zeile steht für das Klartextalphabet.
2. Die erste Spalte steht für das Schlüsselalphabet.
3. Das Geheimtextalphabet steht in der Mitte des Quadrats.
:::
