# Matroska Verschachtelte Kapitel
Verschachtelte Kapitel verhalten sich ähnlich wie die [Basis Kapitel](BasicChapters_ger.md) wenn der Versions Schalter "reihenfolgentreu" inaktiv ist. Es gibt aber zwei Bedingungen die beachtet werden sollten.

1. Bedingung: Die Startzeiten der verschachtelten Kapitel dürfen nicht kleiner als die Starzeit des Eltern Kapitels sein.
2. Bedingung: Die Startzeiten müssen kleiner als die Startzeit vom nächsten Eltern Kapitel sein.

#### Deaktiviertes Eltern Kapitel
In diesem Fall müssen alle verschachtelten Kapitel ignoriert werden.

#### Unsichtbares Eltern Kapitel
Die aktuellen Matroska Specs besagen, dass dann alle verschachtelten Kapitel ebenfalls unsichtbar sind, auch wenn dessen eigener Schalter "unsichtbar" nicht aktiviert ist. Allerdings ist dies nicht der Fall für die Praxis. Alle Player die ich ausprobiert habe zeigen alle verschachtelten Kapitel die selbst nicht "unsichtbar" sind an.

#### Presentation der verschachtelten Kapitel im Player
Die meisten Player benutzen ein "+" vor dem Kapitelnamen um das Level der Verschachtelung anzuziegen. Ein Kapitel welches in der 2.ten Verschachtelungsebene liegt hat zwei "+" vor dem Namen.

Eltern Kapitel
+Verschachteltes Kapitel Level 1
++Verschachteltes Kapitel Level 2

Dies ist die meist genutze Form wenn alle Kapitel auf einer Ebene dargestellt werden. Zum Beispiel in einem Popup Menü.

Eine weitere Möglichkeit wäre, die Verschachtelungsstruktur in einem Popup Menü nachzubilden, so dass verschachtelte Kapitel ein Untermenü öffnen.