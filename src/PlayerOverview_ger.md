# Matroska Player Übersicht
Diese Übersicht soll zeigen welche Player welche Matroska Eigenschaften nutzen.

## MPC-HC
MPC-HC nutzt intern den LAV Filter/Splitter. Dadurch addieren sich die genutzen Matroska Eigenschaften. Weiterhin können andere externe DirectShow Filter verwendet werden, wie zum Beispiel der Haali Splitter, wodurch weitere Matroska Eigenschaften genutzt werden können.

[Test Version ist MPC-HC 1.8.6(clsid)](https://github.com/clsid2/mpc-hc/releases/tag/1.8.6)

Matroska Eigenschaft | vorhanden | funktioniert | Bemerkung
---------------------|:---------:|:------------:|----------
[Basis Kapitel](BasicChapters_ger.md)| ja | sehr gut |
[Verschachtelte Kapitel](NestedChapters_ger.md)| ja | sehr gut |
[Reihenfolgentreue Kapitel](OrderedChapters_ger.md)| ja | sehr gut |
[Verschachtelte Reihenfolgentreue Kapitel](NestedOrderedChapters_ger.md)| ja | gut |
[Matroska Versionen](EditionEntry_ger.md)| ja | sehr gut |
Auswahl der Matroska Versionen | ja | gut | kein internes Versionen Menü, sehr gutes Menü im Splitter (LAV oder Haali)
[Matroska Hard-Linking](HardLinking_ger.md)| ja | sehr gut | Videospur wird perfekt nahtlos verbunden
[Matroska Medium-Linking (Kapitel-Segment-Verknüpfung)](ChapterSegmentLinking_ger.md)| ja | sehr gut | `ChapterSegmentEditionUID` wird nicht unterstützt
[Matroska Soft-Linking (Matroska DVD Menü)](MatroskaMenu_ger.md#matroska-dvd-men%C3%BC-matroska-soft-linking)| nein | |
[Natives Matroska Menü](MatroskaMenu_ger.md#natives-matroska-men%C3%BC)| nein | |
[Video Rotation](Rotate_ger.md)| ja | sehr gut | nur mit den Matroska Tags, `ProjectionPoseRoll` wird nicht unterstützt
[TRACKSETEX](TRACKSETEX_ger.md)| nein | sehr gut | nur mit dem Haali Splitter
[Spurenauswahl per Kapitel](ChapterTrack_ger.md)| nein | |
