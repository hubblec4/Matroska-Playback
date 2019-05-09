# Matroska ChapterTrack - Spurenauswahl per Kapitel
Das `ChapterTrack` Element kann nur in [Reihenfolgentreuen Kapiteln](OrderedChapters_ger.md) verwendet werden. Ist dieses Element nicht vorhanden, so werden alle Spuren für das Kapitel verfügbar sein. Für alle Spuren, die für ein Kapitel verwendet werden sollen, muss die entsprechende Spur UID im `ChapterTrackNumber` Element angegeben werden. Die Bezeichnung `ChapterTrackNumber` lässt vermuten, dass eine Spur Nummer verwendet werden soll, dem ist aber nicht so. Es muss die Spur UID verwendet werden.

Es gibt leider sehr wenig Information zu diesem Element und in der Praxis ist mir kein Player bekannt der das untersützt.

Die Idee ist, für verschiedene [Versionen](EditionEntry_ger.md) nur die gewünschten Spuren zu verwenden. Es könnte so ähnlich benutzt werden wie [TRACKSETEX](TRACKSETEX_ger.md). Jedoch kann nur ein Spuren-Set je Kapitel angelegt werden. Außerdem sollten alle Kapitel einer [Version](EditionEntry_ger.md) das gleiche Spuren-Set verwenden.

### Test Dateien
In der Matroska Datei befinden sich zwei [reihenfolgentreue Versionen](EditionEntry_ger.md) mit je einem [Reihenfolgentreuen Kapitel](OrderedChapters_ger.md). Die Dauer des Kapitels ist gleich der Gesamtdauer der Datei. Es gibt zwei Video- und Audiospuren, sowie 4 Untertitelspuren.

In der ersten [Version](EditionEntry_ger.md) sollen nur die 1. Videospur, die 1. Audiospur und die 1. Untertitelspur verwendet werden. In der zweiten [Version](EditionEntry_ger.md) sollen nur die 2. Videospur, die 2. Audiospur und die 3. Untertitelspur verwendet werden.

Ein Player wählt nur diese Spuren aus und benutzt sie für die Wiedergabe.

Sollten mehrere Spuren eines Typs(zum Beispiel 3 Audiospuren) ausgewählt worden sein, dann sollte immer die erste Spur jedes Typs für die Wiedergabe verwendet werden. Ist bei einer der ausgewählten Spuren der `FlagDefault` Schalter aktiviert dann sollte diese Spur für die Wiedergabe benutzt werden. Manche Player können Spuren anhand der Sprache auswählen, und sollte eine Spur mit der bevorzugten Sprache vorhanden sein, dann wird diese für die Wiedergabe verwendet.

[XML Matroska Kapitel Datei](/files/ChapterTrack/ChapterTrack.xml)

[Matroska Datei](/files/ChapterTrack/ChapterTrack.mkv)