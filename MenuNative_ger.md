# Natives Matroska Menü
Für dieses System werden [Reihenfolgentreue Kapitel](OrderedChapters_ger.md) verwendet. Innerhalb eines Kapitels gibt es ein `ChapProcess` Element und dort muss im `ChapProcessCodecID` Element der Wert 0 angegeben werden. `ChapProcessCodecID` hat einen Standard Wert von 0 und muss daher nicht unbedingt vorhanden sein.

Momentan gibt es auch nur ein einziges Kommenado `GotoAndPlay(ChapterUID);`, bei dem zu einem bestimmten Kapitel gesprungen werden soll.

Nur im VLC ist natives Matroska Menü eingebaut wurden, aber nicht in alle Versionen. Für das Testen und erstellen einer solchen Matroska Datei hatte ich Version 3 benutzt.

In der Test Datei befindet sich im 5.Kapitel das `GotoAndPlay();` Kommando. Dabei soll bevor das 5.Kapitel abgespielt wird, zum 2.Kapitel gesprungen werden.

#### Test Dateien
[XML Matroska Kapitel Datei](https://github.com/hubblec4/Matroska-Playback/blob/master/files/MenuNative/GotoAndPlay.xml)

[Matroska Datei](https://github.com/hubblec4/Matroska-Playback/blob/master/files/MenuNative/GotoAndPlay.mkv)