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
[Verschachtelte Reihenfolgentreue Kapitel](NestedOrderedChapters_ger.md)| ja | gut | nur Startzeiten werden verwendet
[Matroska Versionen](EditionEntry_ger.md)| ja | sehr gut |
[Auswahl der Matroska Versionen](EditionEntry_ger.md#versionen-auswahl-im-player) | ja | gut | kein internes Versionen Menü, sehr gutes Menü im Splitter (LAV oder Haali)
[Matroska Hard-Linking](HardLinking_ger.md)| ja | sehr gut | Videospur wird perfekt nahtlos verbunden
[Matroska Medium-Linking (Kapitel-Segment-Verknüpfung)](ChapterSegmentLinking_ger.md)| ja | sehr gut | `ChapterSegmentEditionUID` wird nicht unterstützt
[Matroska Soft-Linking (Matroska DVD Menü)](MatroskaMenu_ger.md#matroska-dvd-men%C3%BC-matroska-soft-linking)| nein | |
[Natives Matroska Menü](MatroskaMenu_ger.md#natives-matroska-men%C3%BC)| nein | |
[Video Rotation](Rotate_ger.md)| ja | sehr gut | nur mit den Matroska Tags, `ProjectionPoseRoll` wird nicht unterstützt
[TRACKSETEX](TRACKSETEX_ger.md)| nein | sehr gut | nur mit dem Haali Splitter
[Spurenauswahl per Kapitel](ChapterTrack_ger.md)| nein | |

## MPC-BE
Für das Testen wird der interne Matroska Splitter verwendet. MPC-BE kann auch externe Splitter laden, wie zum Beispiel den LAV oder Haali Splitter und würde sich dann wie der MPC-HC Player verhalten.

Test Version ist MPC-BE.1.5.4.4545.x64

Matroska Eigenschaft | vorhanden | funktioniert | Bemerkung
---------------------|:---------:|:------------:|----------
[Basis Kapitel](BasicChapters_ger.md)| ja | gut | keine Anzeige in der Zeitleiste, umständliche Kapitelauswahl in Untermenüs, Kapitel Schalter werden nicht beachtet
[Verschachtelte Kapitel](NestedChapters_ger.md)| ja | gut | Kapitel Anzeige entspricht dem üblichen Standard
[Reihenfolgentreue Kapitel](OrderedChapters_ger.md)| nein | | nur Startzeiten werden verwendet
[Verschachtelte Reihenfolgentreue Kapitel](NestedOrderedChapters_ger.md)| nein | |
[Matroska Versionen](EditionEntry_ger.md)| nein | | es wird immer die 1. Version verwendet
[Auswahl der Matroska Versionen](EditionEntry_ger.md#versionen-auswahl-im-player) | nein | |
[Matroska Hard-Linking](HardLinking_ger.md)| nein | |
[Matroska Medium-Linking (Kapitel-Segment-Verknüpfung)](ChapterSegmentLinking_ger.md)| nein | |
[Matroska Soft-Linking (Matroska DVD Menü)](MatroskaMenu_ger.md#matroska-dvd-men%C3%BC-matroska-soft-linking)| nein | |
[Natives Matroska Menü](MatroskaMenu_ger.md#natives-matroska-men%C3%BC)| nein | |
[Video Rotation](Rotate_ger.md)| ja | | nur mit den Matroska Tags, `ProjectionPoseRoll` wird nicht unterstützt
[TRACKSETEX](TRACKSETEX_ger.md)| nein | |
[Spurenauswahl per Kapitel](ChapterTrack_ger.md)| nein | |

## VLC
Der VLC Player besitzt einen internen Matroska Demuxer/Splitter der von Matroska Gründer Steve Lhomme programmiert wurde.

Test Version ist vlc-3.0.7-20190514-0510-win64

Matroska Eigenschaft | vorhanden | funktioniert | Bemerkung
---------------------|:---------:|:------------:|----------
[Basis Kapitel](BasicChapters_ger.md)| ja | gut | Kapitelauswahl in einem Untermenü, Kapitel Schalter `ChapterFlagEnabled` wird nicht beachtet
[Verschachtelte Kapitel](NestedChapters_ger.md)| ja | gut | Kapitel Anzeige entspricht dem üblichen Standard
[Reihenfolgentreue Kapitel](OrderedChapters_ger.md)| ja | gut | Spieldauer ist nicht korrekt wenn deaktivierte Kapitel vorhanden sind
[Verschachtelte Reihenfolgentreue Kapitel](NestedOrderedChapters_ger.md)| ja | gut | nur Startzeiten werden verwendet
[Matroska Versionen](EditionEntry_ger.md)| ja | sehr gut |
[Auswahl der Matroska Versionen](EditionEntry_ger.md#versionen-auswahl-im-player) | ja | schlecht | Versionen wechseln funktioniert nicht richtig
[Matroska Hard-Linking](HardLinking_ger.md)| ja | gut | Probleme mit der Kapitel Anzeige, beim Serien-Intro-Abspann Test stürtze VLC ab, Zeitleiste stimmt nicht
[Matroska Medium-Linking (Kapitel-Segment-Verknüpfung)](ChapterSegmentLinking_ger.md)| ja | gut | `ChapterSegmentEditionUID` wird nicht unterstützt, Probleme mit der Kapitel Anzeige
[Matroska Soft-Linking (Matroska DVD Menü)](MatroskaMenu_ger.md#matroska-dvd-men%C3%BC-matroska-soft-linking)| ja | nicht mehr | funktionierte nur in einer sehr frühen Version des VLC
[Natives Matroska Menü](MatroskaMenu_ger.md#natives-matroska-men%C3%BC)| ja | sehr gut |
[Video Rotation](Rotate_ger.md)| nein | |
[TRACKSETEX](TRACKSETEX_ger.md)| nein | |
[Spurenauswahl per Kapitel](ChapterTrack_ger.md)| nein | |

## mpv
Der [mpv Player](https://mpv.io) ist ein Open-Source Projekt an dem zur Zeit sehr viel gearbeitet wird.

Test Version ist mpv-x86_64-20190513-git-64cdc36

Matroska Eigenschaft | vorhanden | funktioniert | Bemerkung
---------------------|:---------:|:------------:|----------
[Basis Kapitel](BasicChapters_ger.md)| ja | schlecht | kein Kapitelauswahl Menü, keine Kapitelnamen in der Zeitleiste, Kapitel Schalter `ChapterFlagEnabled` und `ChapterFlagHidden` werden nicht beachtet
[Verschachtelte Kapitel](NestedChapters_ger.md)| nein | |
[Reihenfolgentreue Kapitel](OrderedChapters_ger.md)| ja | gut | Spieldauer ist nicht korrekt wenn deaktivierte Kapitel vorhanden sind
[Verschachtelte Reihenfolgentreue Kapitel](NestedOrderedChapters_ger.md)| nein | |
[Matroska Versionen](EditionEntry_ger.md)| ja | gut | welche Version verwendet wird ist nicht ersichtlich
[Auswahl der Matroska Versionen](EditionEntry_ger.md#versionen-auswahl-im-player) | ja | gut | umständlich, ein mpv Kommando muss benutzt werden
[Matroska Hard-Linking](HardLinking_ger.md)| nein | |
[Matroska Medium-Linking (Kapitel-Segment-Verknüpfung)](ChapterSegmentLinking_ger.md)| ja | gut | `ChapterSegmentEditionUID` wird unterstützt
[Matroska Soft-Linking (Matroska DVD Menü)](MatroskaMenu_ger.md#matroska-dvd-men%C3%BC-matroska-soft-linking)| nein | |
[Natives Matroska Menü](MatroskaMenu_ger.md#natives-matroska-men%C3%BC)| nein | |
[Video Rotation](Rotate_ger.md)| nein | |
[TRACKSETEX](TRACKSETEX_ger.md)| nein | |
[Spurenauswahl per Kapitel](ChapterTrack_ger.md)| nein | |