---
name: Queue S. 64 Nr. 2 - 2. Lösung
index: 1
toc: show
---

# Queue Lösung von Yassin und Leo


S.64  

Aufgabe Nr 2 

Die Methode „methode1“, welche in der Unterklasse ErweiterteQueue ist, welche eine abstrakte Klasse von Queue ist, fügt die Queue pSchlange an eine neue Queue, wodurch pSchlange an die andere Queue angeheftet wird. 

1.
Als erstes wird in der while Schleife geprüft ob pSchlange befüllt ist, solange es true ist, werden Schritt 2&3 ausgeführt.

2.
Im zweiten Schritt wird die neue Queue das erste Element von pSchlange hinten angehängt.

3.
Dieses Element wird dann durch die Methode dequeue aus der pSchlange gelöscht


Am Ende wird aus zwei verschiedenen Queues (pSchlange & der aktuellen Schlange ) eine lange Queue. In der aktuellen Queue sind die selben Elementen in der  selben Reihenfolge gespeichert wie in pSchlange  jedoch auch Elemente welche vorher schon gegeben waren, pSchlange ist nun leer. 
