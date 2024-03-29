# Matroska Kapitel-Segment-Verknüpfung

Die offizielle Matroska Bezeichnung lautet Medium-Linking.

Bei einem [Reihenfolgentreuen Kapitel](OrderedChapters_ger.md) kann mittels dem `ChapterSegmentUID` Element eine Verknüpfung zu einer anderen Datei erstellt werden. Beim Erzeugen der virtuellen Zeitleiste, muss der Player den Inhalt aus der verknüpften Datei benutzen.

Weiterhin kann das Element `ChapterSegmentEditionUID` genutzt werden um gezielt den Inhalt einer [Version](EditionEntry_ger.md) zu verwenden.

## Verknüpfung nur mit der SegmentUID

Bei dieser Variante wird die Start- und Endzeit des Kapitels genutzt.
Beide Zeiten müssen sich innerhalb der Spieldauer der verknüpften Datei befinden.

### Test Dateien

[XML Kapitel Datei](/files/Chapter-Segment-Linking/Chapter-Segment-Linking.xml)

[Matroska Dateien](/files/Chapter-Segment-Linking/Chapter-Segment-Linking.zip)

Im zip-Ordner befinden sich mehrere "Linked.mkv" Dateien und eine _Main.mkv Datei. In der _Main.mkv befinden sich alle Kapitel, die zu den verknüpften Dateien führen.

## Verknüpfung mit einer zusätzlichen SegmentEditionUID

Wenn ein `ChapterSegmentEditionUID` Element verwendet wird, dann muss der gesamte Inhalt dieser verknüpften Version abgespielt werden. die Start- und End-zeiten eines solchen Kapitels werden hierbei ignoriert.
Eine Player muss dann die gesamte Spieldauer der Version für die virtuelle Zeitleiste integrieren.

### Test Dateien

[XML Kapitel Datei](/files/Chapter-Segment-Edition-Linking/Chapter-Segment-Edition-Linking.xml)

[Matroska Dateien](/files/Chapter-Segment-Edition-Linking/Chapter-Segment-Edition-Linking.zip)

Die Test Dateien nutzen eine einfache Weise um die Inhalte der Dateien zu verknüpfen.
Es gibt eine Vielzahl von Kombination der Verknüfpung, unter anderem auch eine Möglichkeit einer Endlos-Schleife. Dies sollte von einem Player abgefangen werden.
