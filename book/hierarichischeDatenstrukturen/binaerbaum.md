---
name: Binärbäume
index: 1
---

# Binärbäume

Im Gegensatz zu Bäumen haben Binärbaume maximal zwei Nachfolgeknoten. Somit wergeben sich drei Möglichkeiten:

1. Binärbaum mit leeren Nachfolgeteilbäumen

![Keine Nachfolgebäume](/Bilder/baumstrukturen/BinärbaumKnotenMitKeinemNachfolger.svg)

2. Binärbaum mit einem leeren Nachfolgeteilbaum und einem Nachfolgeteilbaum

![Ein Nachfolgebum](/Bilder/baumstrukturen/BinärbaumKnotenMitEinemNachfolger.svg)

3. Binärbaum mit zwei Nachfolgeteilbäumen

![Zwei Nachfolgebäume](/Bilder/baumstrukturen/BinärbaumKnotenMitZweiNachfolger.svg)


## Modellierung eines Binärbaums im Kontext Ahnenbaum

Im Zentralabtur steht die Klasse BinaryTree() zur Verfügung (Dokumentation unter Dokumentation). Diese Klasse stellt drei Konstruktoren zur Verfügung mit denen ein leerer Teilbaum, ein Teilbaum bestehend aus einer Wurzel und keinen Nachfolgeknoten und eine Wurzel mit maximal zwei Teilbäumen (linker und rechter Teilbaum) erzeugt werden kann.

Binärbäume eignen sich um z.B. Ahnenbäume abzubilden, wobei weibliche Vorfahren immer als linker und männliche Vorfahren als rechter Teilbaum dargestellt werden.

Unten stehendes Bild verdeutlich die Situation.

![Ahnenbaum der Einhornfamilie](/Bilder/baumstrukturen/AhnenbaumDerEinhornfamilie.svg)

