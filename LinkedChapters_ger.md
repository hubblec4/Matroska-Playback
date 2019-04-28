# Matroska Verknüpfte Kapitel
Diese Bezeichung ist momentan nicht in den Matroska Specs enthalten.

Bei einem [Reihenfolgentreuen Kapitel](OrderedChapters_ger.md) kann mittels dem `ChapterSegmentUID` Element eine Verknüpfung zu einer anderen Datei erstellt werden. Beim Erzeugen der virtuellen Zeitleiste, muss der Player den Inhalt aus der verknüpften Datei benutzen.

Weiterhin kann das Element `ChapterSegmentEditionUID` genutzt werden um gezielt den Inhalt einer Version zu verwenden.

Alle Reihenfolgentreuen Kapitel und deren Kombination mit Verschachtelungen, sind dann ein verknüpfendes Kapitel, wenn eine SegmentUID im Element `ChapterSegmentUID` angegeben ist.