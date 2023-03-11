---
name: Bäume
index: 0
---

# Baumstrukturen

Eine Baumstruktur(Binary Tree) ist eine **hierarchische Datenstruktur**, die aus Knoten und Kanten besteht. Jeder Knoten hat in der Regel einen oder mehrere untergeordnete Knoten. Diese Knoten können ebenfalls untergeordnete Knoten haben.
Hierbei sind folgende Unterschiede/Gemeinsamkeiten zu linearen Datenstrukturen zu beachten:

**Gemeinsamkeiten**:

Alle drei Datenstrukturen haben ein Element, das an erster Stelle steht und auf das zugegriffen werden kann.
Die Elemente in allen drei Datenstrukturen sind in der Reihenfolge angeordnet, in der sie hinzugefügt wurden.
Alle drei Datenstrukturen unterstützen das Hinzufügen und Entfernen von Elementen.

**Unterschiede**:

Eine Liste ist eine lineare Datenstruktur, bei der jeder Knoten nur einen Nachfolger hat, während ein Baum eine hierarchische Struktur ist, bei der jeder Knoten mehrere untergeordnete Knoten haben kann.
Eine Schlange ist eine lineare Datenstruktur, bei der Elemente nur am Ende eingefügt und am Anfang entfernt werden können, während beim Baum Knoten an beliebigen Stellen eingefügt und entfernt werden können.
Ein Stapel ist ebenfalls eine lineare Datenstruktur, bei der Elemente nur am Anfang eingefügt und entfernt werden können, während beim Baum Knoten an beliebigen Stellen eingefügt und entfernt werden können.

Zusammenfassend lässt sich sagen, dass Bäume im Gegensatz zu Listen, Stapeln und Schlangen eine hierarchische Struktur aufweisen und sich dadurch besser eignen, um Daten mit komplexeren Beziehungen abzubilden.

**Wichtige Begriffe**:

**_Knoten_**: In einem Netzwerk ist ein Node (Netzwerkknoten oder Netzknoten) ein Verbindungspunkt. Das kann entweder ein Umverteilungspunkt oder ein Endpunkt bei der Datenübertragungen sein kann.

**_Kante_**: In einem Baum wird eine Verbindungslinie zwischen zwei Knoten als Kante bezeichnet.
Kanten werden als Linien dargestellt.

**_Pfad_**:Ein Pfad ist ein Weg in einem Baum, der von einem Startknoten über eine oder mehrere Kanten zu einem Endknoten verläuft.
Handelt es sich bei dem Startknoten um die Wurzel des Baums, spricht man von einem absoluten Pfad, andernfalls von einem relativen Pfad.

**_Wurzel_**: Die Wurzel eines Baums ist ein besonderer Knoten, zu dem keine Kante zeigt. Jeder Baum hat genau eine Wurzel. (Start Punkt)

**_Ebene_**: Ebene auf der sich die Knoten befinden. So befindet sich auf Ebene 1 z.B die Wurzel

**_Grad_**: Die höchste Anzahl an Kanten die in einem Pfad zu finden ist. Wenn der längste Pfad 4 Kanten hat, ist die Grad Anzahl 4

**Spiel Nim**:

Zu Beginn des Spiels wird ein Haufen von Spielsteinen auf dem Spielfeld platziert.

Die Spieler nehmen abwechselnd 1-3 Spielsteine vom Haufen weg. Die genaue Anzahl der 

Das Ziel des Spiels ist es, den letzten Spielstein vom Haufen zu nehmen und somit das Spiel zu gewinnen.

Wenn du als erster Spieler beginnst und der Haufen aus einer Anzahl von Spielsteinen besteht, die nicht durch 4 teilbar ist, kannst du das Spiel immer gewinnen, indem du eine bestimmte Strategie anwendest:

Beginne, indem du 1 Spielstein nimmst. Dies sorgt dafür, dass der Haufen nun aus einer Anzahl von Spielsteinen besteht, die durch 4 teilbar ist.

Unabhängig davon, welche Anzahl von Spielsteinen dein Gegner in seinem Zug nimmt, nehme so viele Spielsteine, dass die Anzahl der Spielsteine im Haufen am Ende deines Zuges durch 4 teilbar ist. Zum Beispiel, wenn dein Gegner 2 Spielsteine nimmt und der Haufen 6 Spielsteine enthält, nehme 2 Spielsteine und der Haufen wird auf 4 Spielsteine reduziert.

Setze diese Strategie fort, bis nur noch ein Spielstein übrig bleibt. Bei diesem letzten Zug kannst du den letzten Spielstein nehmen und das Spiel gewinnen.

Diese Strategie funktioniert, weil du sicherstellst, dass der Haufen immer durch 4 teilbar bleibt, während dein Gegner immer eine Anzahl von Spielsteinen nimmt, die den Haufen nicht durch 4 teilbar macht.

![Beispiel](/download/HölzerDiagramm.excalidraw.png "Binary Tree")





