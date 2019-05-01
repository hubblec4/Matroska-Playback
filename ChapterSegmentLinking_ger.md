# Matroska Kapitel-Segment-Verknüpfung
Die offizielle Matroska Bezeichnung lautet Medium-Linking.

Bei einem [Reihenfolgentreuen Kapitel](OrderedChapters_ger.md) kann mittels dem `ChapterSegmentUID` Element eine Verknüpfung zu einer anderen Datei erstellt werden. Beim Erzeugen der virtuellen Zeitleiste, muss der Player den Inhalt aus der verknüpften Datei benutzen.

Weiterhin kann das Element `ChapterSegmentEditionUID` genutzt werden um gezielt den Inhalt einer Version zu verwenden.

## Verknüpfung nur mit der SegmentUID
Bei dieser Variante wird die Start- und Endzeit des Kapitels genutzt.
Beide Zeiten müssen sich innerhalb der Spieldauer der verknüpften Datei befinden.

### Test Dateien
[XML Kapitel Datei](https://github.com/hubblec4/Matroska-Playback/blob/master/files/Chapter-Segment-Linking/Chapter-Segment-Linking.xml)

[Matroska Dateien](https://github.com/hubblec4/Matroska-Playback/blob/master/files/Chapter-Segment-Linking/Chapter-Segment-Linking.zip)

Im zip-Ordner befinden sich mehrere "Linked.mkv" Dateien und eine _Main.mkv Datei. In der _Main.mkv befinden sich alle Kapitel, die zu den verknüpften Dateien führen.

## Verknüpfung mit einer zusätzlichen SegmentEditionUID
TODO