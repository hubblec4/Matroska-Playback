# Matroska Verschachtelte Kapitel
Verschachtelte Kapitel verhalten sich ähnlich wie die [Basis Kapitel](BasicChapters_ger.md) wenn der Versions Schalter "reihenfolgentreu" inaktiv ist. Es gibt aber zwei Bedingungen die beachtet werden sollten.

1. Bedingung: Die Startzeiten der verschachtelten Kapitel dürfen nicht kleiner als die Starzeit des Eltern Kapitels sein.
2. Bedingung: Die Startzeiten müssen kleiner als die Startzeit vom nächsten Eltern Kapitel sein.

#### Deaktiviertes Eltern Kapitel
In diesem Fall müssen alle verschachtelten Kapitel ignoriert werden.

#### Unsichtbares Eltern Kapitel
Die aktuellen Matroska Specs besagen, dass dann alle verschachtelten Kapitel ebenfalls unsichtbar sind, auch wenn dessen eigener Schalter "unsichtbar" nicht aktiviert ist. Allerdings ist dies nicht der Fall für die Praxis. Alle Player die ich ausprobiert habe zeigen alle verschachtelten Kapitel, die selbst sichtbar sind, an.
Dieses Verhalten ist sehr nützlich/wichtig für das Erstellen von Matroska Menu Strukturen auf der Basis von Kapitel-Segment-Verknüpfung.

#### Presentation der verschachtelten Kapitel im Player
Die meisten Player benutzen ein "+" vor dem Kapitelnamen um das Level der Verschachtelung anzuzeigen. Ein Kapitel welches in der 2.ten Verschachtelungsebene liegt hat zwei "+" vor dem Namen.

Eltern Kapitel  
+Verschachteltes Kapitel Level 1  
++Verschachteltes Kapitel Level 2

Dies ist die meist genutzte Form, wenn alle Kapitel auf einer Ebene dargestellt werden. Zum Beispiel in einem Popup Menü.

Eine weitere Möglichkeit wäre, die Verschachtelungsstruktur in einem Popup Menü nachzubilden, so dass verschachtelte Kapitel in einem Untermenü angezeigt werden.
Für ein Matroska Menü auf der Basis von Kapitel-Segment-Verknüpfung, werden oft sehr viele Kapitel benutzt, manchmal fast 1000. Diese Anzahl dann in einer einzigen Ebene darzustellen ist nicht möglich. Man muss dann sehr viel suchen und scrollen im Kapitel Menü, um den gewünschten Kapitel zu finden.

### Test Dateien
[XML Kapitel Datei](/files/NestedChapters/NestedChapters.xml)

[Matroska Datei](files/NestedChapters/NestedChapters.mkv)