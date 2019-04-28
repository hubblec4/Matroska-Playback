# Matroska Verschachtelte Reihenfolgentreue Kapitel
Diese Art von Kapitel ergibt sich automatisch aus der Kombination von [Verschachtelte Kapitel](NestedChapters_ger.md) und [Reihenfolgentreue Kapitel](OrderedChapters_ger.md).
In den Matroska Specs ist hierzu keinerlei Information zu finden.
In der Praxis verwenden die Player nur die Top-Level [Reihenfolgentreue Kapitel](OrderedChapters_ger.md) um die virtuelle Zeitleiste zu erstellen. Bei allen [Verschachtelten Kapiteln](NestedChapters_ger.md) wird nur die Startzeit des Kapitels verwendet.



### Test Dateien
[XML Kapitel Datei](https://github.com/hubblec4/Matroska-Playback/blob/master/files/NestedChapters/NestedChapters.xml)

[Matroska Datei](https://github.com/hubblec4/Matroska-Playback/blob/master/files/NestedChapters/NestedChapters.mkv)