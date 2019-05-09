# Matroska ChapterTrack - Spurenauswahl per Kapitel
Das `ChapterTrack` Element kann nur in [Reihenfolgentreuen Kapiteln](OrderedChapters_ger.md) verwendet werden. Ist dieses Element nicht vorhanden, so werden alle Spuren für das Kapitel verfügbar sein. Für alle Spuren, die für ein Kapitel verwendet werden sollen, muss die entsprechende Spur UID im `ChapterTrackNumber` Element angegeben werden. Die Bezeichnung `ChapterTrackNumber` lässt vermuten, dass eine Spur Nummer verwendet werden soll, dem ist aber nicht so. Es muss die SpurUID verwendet werden.

Es gibt leider sehr wenig Information zu diesem Element und in der Praxis ist mir kein Player bekannt der das untersützt.

Die Idee ist, damit gezielt Spuren zu verwenden für verschiede Versionen. Es könnte so ähnlich benutzt werden wie [TRACKSETEX](TRACKSETEX_ger.md). Jedoch kann nur ein TrackSet je Kapitel angelegt werden.