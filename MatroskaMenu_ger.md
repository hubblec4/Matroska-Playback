# Matroska Menü
Für das Matroska Menü werden [Reihenfolgentreue Kapitel](OrderedChapters_ger.md) und ein "Chapter CODEC" verwendet. Innerhalb eines Kapitels gibt es ein `ChapProcess` Element. In diesem Master Element werden (fast) alle notwendigen Daten für das Matroska Menü gespeichert.

#### Chapter CODEC
Ein Chapter CODEC ist eine Software, welche alle Matroska Menü Kommandos kennt und diese verarbeiten kann. Die Kommandos müssen empfangen und gesendet werden können.

Es gibt momentan zwei existierende Menüsysteme und ein drittes ist in Planung.

## Natives Matroska Menü
Um dieses System zu nutzen muss im `ChapProcessCodecID` Element der Wert 0 verwendet werden. `ChapProcessCodecID` hat einen Standard Wert von 0 und muss daher nicht unbedingt vorhanden sein.

Momentan gibt es nur ein einziges Kommenado `GotoAndPlay(ChapterUID);`, bei dem zu einem bestimmten Kapitel gesprungen werden soll.

Nur im VLC ist natives Matroska Menü eingebaut wurden, aber nicht in alle Versionen. Für das Testen einer solchen Matroska Datei hatte ich Version 3 benutzt.

In der Test Datei befindet sich im 5.Kapitel das `GotoAndPlay();` Kommando. Dabei soll bevor das 5.Kapitel abgespielt wird, zum 2.Kapitel gesprungen werden.

#### Test Dateien
[XML Matroska Kapitel Datei](https://github.com/hubblec4/Matroska-Playback/blob/master/files/MatroskaMenu/Native/GotoAndPlay.xml)

[Matroska Datei](https://github.com/hubblec4/Matroska-Playback/blob/master/files/MatroskaMenu/Native/GotoAndPlay.mkv)

## Matroska DVD Menü
Um dieses System zu nutzen muss im `ChapProcessCodecID` Element der Wert 1 verwendet werden.

Matroska borgt sich das DVD Menü System. Dabei werden die Strukturen des Menüs, die DVD Kommandos und die VOB-Butons verwendet. Weitehin wird noch ein "Control Track" für die Interaktionen genutzt.

In der Segment/Info(`ChapterTranslate` und `SegmentFamily`) und in den Tracks(`TrackTranslate`) gibt es weitere Elemente die zu diesem System gehören.

Nur im VLC ist dieses System eingebaut, allerdings funktioniert es in den heutigen Versionen nicht mehr.

[DVDMenuXtractor](https://github.com/Matroska-Org/dvdmenuxtractor) kann zwar eine DVD in seine Bestandteile zerlegen, aber es ist sehr veraltet und funktioniert mit dem heutigen MKVToolNix nicht mehr.

Ich habe für die Test Dateien eine StarTrek TNG DVD genommen. Es sind nur die XML Dateien und die VOB-Buton Datei im zip enthalten.

[Matroska DVD Menü Test Dateien](https://github.com/hubblec4/Matroska-Playback/blob/master/files/MatroskaMenu/DVD/MatroskaDVDMenuTNG-S6-D1.zip)