# Matroska Verschachtelte Reihenfolgentreue Kapitel
Diese Art von Kapitel ergibt sich automatisch aus der Kombination von [Verschachtelten Kapiteln](NestedChapters_ger.md) und [Reihenfolgentreuen Kapiteln](OrderedChapters_ger.md).

In den Matroska Specs ist hierzu keinerlei Information zu finden.

In der Praxis verwenden die Player nur die Top-Level [Reihenfolgentreue Kapitel](OrderedChapters_ger.md) um die virtuelle Zeitleiste zu erstellen. Bei allen [Verschachtelten Kapiteln](NestedChapters_ger.md) wird nur die Startzeit verwendet für einen Kapitelmarker in der Zeitleiste. Es wird keine Spieldauer für das Kapitel berechnet.

#### Volle Verschachtelte Reihenfolgentreue Kapitel
In diesem Fall muss für jedes [Verschachtelte Kapitel](NestedChapters_ger.md) die Spieldauer berechnet werden.

Kapitel     | Start | Ende | Dauer | Aktuelle Gesamt Dauer
------------|-------|------|-------|----------------------
Kap 1       | 0s    | 10s  | 10s   | 10s
+Kap 1.1    | 10s   | 20s  | 10s   | 20s
+Kap 1.2    | 50s   | 60s  | 10s   | 30s
++Kap 1.2.1 | 20s   | 30s  | 10s   | 40s
Kap 2       | 30s   | 50s  | 20s   | 60s
+Kap 2.1    | 50s   | 60s  | 10s   | 70s

Die Matroska Test Datei wird in keinem Player so abgespielt, wie es hier beschrieben ist.

### Test Dateien
[XML Kapitel Datei](https://github.com/hubblec4/Matroska-Playback/blob/master/files/NestedOrderedChapters/NestedOrderedChapters.xml)

[Matroska Datei](https://github.com/hubblec4/Matroska-Playback/blob/master/files/NestedOrderedChapters/NestedOrderedChapters.mkv)