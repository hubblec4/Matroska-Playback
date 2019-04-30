# Matroska Hard-Linking
Hard-Linking ist die "einfachste" und "schwächste" Art von Verknüpfung, um Matroska Dateien virtuell und nahtlos miteinander zu verbinden. Für dieses Verfahren werden die Elemente `PrevUID` und `NextUID` genutzt. Diese Elemente befinden sich in der Segment/Info Sektion einer Matroska Datei.

Beim Laden einer Matroska Datei muss ein Player diese Elemente untersuchen und prüfen, ob im Element `PrevUID` oder `NextUID` eine UID angegeben ist, welche zu einer anderen Matroska Datei gehört, die sich im selben Ordner befinden muss.

#### Schwaches Hard-Linking
Wenn eine reihenfolgentreue Version mit [Reihenfolgentreuen Kapiteln](OrderedChapters_ger.md) verwendet wird, dann muss das Hard-Linking ignoriert werden.

[Hard-Linking "Schwach" Test Dateien](https://github.com/hubblec4/Matroska-Playback/blob/master/files/HardLinking/HardLinkingWeak.zip)

#### Kapitel und Hard-Linking
Wenn in den Matroska Dateien Kapitel enthalten sind, dann müssen die Kapitelzeiten für die Kapitelmarker angepasst/verschoben werden. Es werden nur die Startzeiten der Kapitel verwendet.

Welche Kapitel, aus welcher Version sollten verwendet werden.

Es kann vorkommen, dass mehrere Versionen in der geöffneten Datei vorhanden sind. Wie schon erwähnt darf die Version nicht reihenfolgentreu sein. Sagen wir mal die 2.Version muss vom Player verwendet werden. Dann sollte der Player auch aus allen verknüpften Dateien, die 2.Version benutzen. Falls es aber keine 2.Version in einer der verknüpften Dateien gibt, dann werden auch keine Kapitelmarker erstellt.

Wie und welche Kapitel von den verknüpften Dateien genutzt werden,  handhaben die aktuellen Player sehr unterschiedlich. Der LAV-Splitter zum Beispiel nutzt immer die 1.Version aus den verknüpften Dateien. Gibt es eine Version mit dem `EditionFlagDefault` Element, dann werden die Kapitel dieser Version verwendet.

Die erste Test Datei hat 2 Versionen und die 2. ist die Standard Version. Ebenso hat die zweite und letzte Test Datei 2 Versionen, aber keine ist als Standard defniert. Die anderen Test Dateien haben nur eine Version.

[Hard-Linking mehrere Versionen Test Dateien](https://github.com/hubblec4/Matroska-Playback/blob/master/files/HardLinking/HardLinkingWithMultipleEditions.zip)

## Matroska Specs
Die Matroska Specs besagen, dass die 1. Matroska Datei keine `PrevUID` haben darf und die letzte Matroska Datei darf keine `NextUID` haben. Alle "zwischen liegenden" Dateien müssen beide Elemente verwenden.
Dadurch wird sichergestellt, dass egal welche Datei man im Player öffnet, der gesamte Inhalt aller verknüpften Dateien abgespielt wird.

Zu beachten ist, dass man keine Endlos-Schleifen Verknüpfung erzeugen darf/sollte. Theoretisch könnte ein Player das erkennen, und beim Einlesen der Daten abbrechen, wenn die verknüpfte Datei schon einmal in die virtuelle Zeitleiste aufgenommen wurde.

[Hard-Linking Specs Test Dateien](https://github.com/hubblec4/Matroska-Playback/blob/master/files/HardLinking/HardLinkingSpecs.zip)

## Hard-Linking in der Praxis
Zuerst einmal ein paar Überlegungen zum System Hard-Linking.
Ein Player untersucht die Matroska Datei und findet dabei ein `PrevUID` Element mit einer SegmentUID. Das führt dazu, dass eine "Rückwärts Suche" gestartet werden muss. Weiterhin muss das `NextUID` Element untersucht werden, wodurch dann eine "Vorwärst Suche" gestartet werden muss.

#### Rückwärts Suche
Zuerst sucht der Player nach dieser Datei im Ordner. Wenn die Datei vorhanden ist, wird wiederum das `PrevUID` Element untersucht, aber NICHT das `NextUID` Element. Dies wiederholt sich solange bis die "erste" Matroska Datei erreicht ist, bei der es keine `PrevUID` gibt, oder die Datei nicht vorhanden ist.

#### Vorwärts Suche
Der Vorgang ist ähnlich wie bei der "Rückwärst Suche". Allerdings muss immer das `NextUID` Element untersucht werden.

### Weitere Hard-Linking Möglichkeiten
Alle Player die ich getestet habe, scheinen nach diesem Prinzip zu arbeiten. Daher habe ich mir weiter Hard-Linking Möglichkeiten einfallen lassen. In meinem [chapterEditor](https://forum.doom9.org/showthread.php?t=169984) Projekt kann man sehr bequem diese verschiedenen Varianten einrichten.

#### Hard-Linking nur mit dem `NextUID` Element
Ein Player wird somit immer nur in der Lage sein eine "Vorwärst Suche" zu starten. Nur wenn man die erste Matroska Datei öffnet, wird der gesamte Inhalt aller verknüpften Dateien abgespielt.

Zum Beispiel für eine Serie, bei der jede Folge als erstes, immer den gleichen Vorspann hat, und anschließend einen Rückblick. Vorspann, Rückblick und der Episodenteil liegen separat als Matroska Datei vor. Möchte man die komplette Folge sehen, dann startet man die Vorspann-Datei. Möchte man keinen Vorspann sehen aber den Rückblick, dann startet man die Rückblick-Datei. Und möchte man nur den Episodenteil sehen, dann eben diese Datei starten.

[Hard-Linking NextUID Test Dateien](https://github.com/hubblec4/Matroska-Playback/blob/master/files/HardLinking/HardLinkingNextUID.zip)

#### Hard-Linking nur mit dem `PrevUID` Element
Ein Player wird somit immer nur in der Lage sein eine "Rückwärst Suche" zu starten. Nur wenn man die letzte Matroska Datei öffnet, wird der gesamte Inhalt aller verknüpften Dateien abgespielt.

Nutzen wir wieder unser Serien Beispiel, nur das wir diesmal einen Episodenteil und einen Abspann als separate Dateien haben. Wenn man die Apspann Datei startet wird die gesamte Folge abgespielt. Startet man nur die Episodenteil-Datei dann wird die Abspann Datei nicht verwendet.

[Hard-Linking PrevUID Test Dateien](https://github.com/hubblec4/Matroska-Playback/blob/master/files/HardLinking/HardLinkingPrevUID.zip)

#### Hard-Linking gemischtes Nutzen der `NextUID` und `PrevUID` Elemente
Die folgenden drei Varianten nutzen auf sehr unterschiedliche Weise diese beiden Matroska Elemente. Es kommt dabei vor, dass eine Datei selbst keines der beiden Elemente nutzt, aber dennoch Bestandteil der Verknüpfungskette ist. Diese Varianten sind sehr hilfreich für Serien, bei denen die Folgen immer den gleichen Vor- und/oder Abspann haben.

##### Episoden mit Vorspann
Es gibt nur eine Vorspann Datei und viele weitere Episoden Dateien. Jede Episoden Datei nutzt die `PrevUID`, um die Vorspann Datei zu verknüpfen. Die Vorspann Datei nutzt keine Verknüpfungen und wird daher immer nur alleine abgespielt. Man könnte natürlich eine `NextUID` zuweisen, aber eben nur zu einer Episoden Datei.

[Hard-Linking Serien-Vorspann Test Dateien](https://github.com/hubblec4/Matroska-Playback/blob/master/files/HardLinking/HardLinkingSeriesIntro.zip)

##### Episoden mit Abspann
Es gibt nur eine Abspann Datei und viele weitere Episoden Dateien. Jede Episoden Datei nutzt die `NextUID`, um die Abspann Datei zu verknüpfen. Die Abspann Datei nutzt keine Verknüpfungen und wird daher immer nur alleine abgespielt. Man könnte natürlich eine `PrevUID` zuweisen, aber eben nur zu einer Episoden Datei.

[Hard-Linking Serien-Abspann Test Dateien](https://github.com/hubblec4/Matroska-Playback/blob/master/files/HardLinking/HardLinkingSeriesCredits.zip)

##### Episoden mit Vorspann und Abspann
Bei dieser Variante gibt es eine Vorspann und eine Abspann Datei, sowie auch weitere Episoden Dateien. Jede Episoden Datei nutzt die `NextUID`, um die Abspann Datei zu verknüpfen. Jede Episoden Datei nutzt die `PrevUID`, um die Vorspann Datei zu verknüpfen. Die Vor- und Abspann Datei haben keine Verknüpfungen und werden daher immer nur alleine abgespielt.

[Hard-Linking Serien-Vorspann-Abspann Test Dateien](https://github.com/hubblec4/Matroska-Playback/blob/master/files/HardLinking/HardLinkingSeriesIntroCredits.zip)