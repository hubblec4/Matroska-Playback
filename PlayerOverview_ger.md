# Matroska Player Übersicht
Diese Übersicht soll zeigen welche Player welche Matroska Funktionen nutzen.

## MPC-HC
MPC-HC nutzt intern den LAV Filter/Splitter. Dadurch addieren sich die genutzen Matroska Eigenschaften. Weiterhin können andere externe DirectShow Filter verwendet werden, wie zum Beispiel der Haali Splitter, wodurch weitere Matroska Eigenschaften genutzt werden können.

Matroska Eigenschaft | vorhanden | funktioniert | Bemerkung
---------------------|:---------:|:------------:|----------
[Basis Kapitel](BasicChapters_ger.md)| ja | sehr gut |
[Verschachtelte Kapitel](NestedChapters_ger.md)| ja | sehr gut |
[Reihenfolgentreue Kapitel](OrderedChapters_ger.md)| ja | sehr gut |
[Verschachtelte Reihenfolgentreue Kapitel](NestedOrderedChapters_ger.md)| ja | gut |
[Matroska Versionen](EditionEntry_ger.md)| ja | sehr gut |
Auswahl der Matroska Versionen | ja | gut | kein internes Versionen Menü, sehr guten Menü im Splitter (LAV oder Haali)
[Matroska Hard-Linking](HardLinking_ger.md)| ja | sehr gut |
[Matroska Medium-Linking (Kapitel-Segment-Verknüpfung)](ChapterSegmentLinking_ger.md)| ja | gut | `ChapterSegmentEditionUID` wird nicht unterstützt
[Matroska Soft-Linking (Matroska DVD Menü)](MatroskaMenu_ger.md#matroska-dvd-men%C3%BC-matroska-soft-linking)| nein | |
[Natives Matroska Menü](MatroskaMenu_ger.md#natives-matroska-men%C3%BC)| nein | |
