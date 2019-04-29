# Matroska Hard-Linking
Hard-Linking ist die "einfachste" und "schwächste" Form, Matroska Dateien virtuell und nahtlos miteinander zu verbinden. Für dieses Verfahren werden die Elemente `PrevUID` und `NextUID` genutzt. Diese Elemente befinden sich in der Segment/Info Sektion einer Matroska Datei.

Beim Laden einer Matroska Datei muss ein Player diese untersuchen und prüfen, ob im Element `PrevUID` oder `NextUID` eine UID angegeben ist, welche zu einer anderen Matroska Datei gehört, die sich im selben Ordner befinden muss.

#### Kapitel und Hard-Linking
Wenn in den Matroska Dateien Kapitel enthalten sind, dann müssen die Kapitelzeiten für die Kapitelmarker angepasst/verschoben werden. Es werden nur die Startzeiten der Kapitel verwendet.

#### Schwaches Hard-Linking
Wenn eine reihenfolgentreue Version mit [Reihenfolgentreuen Kapiteln](OrderedChapters_ger.md) verwendet, dann wird das Hard-Linking ignoriert.

## Matroska Specs
Die Matroska Specs besagen, dass die 1. Matroska Datei keine `PrevUID` haben darf und die letzte Matroska Datei darf keine `NextUID` haben. Alle "zwischen liegenden" Dateien müssen beide Elemente verwenden.
Dadurch wird sichergestellt, dass egal welche Datei man im Player öffnet, der gesamte Inhalt aller verknüpften Dateien abgespielt wird.

Zu beachten ist, dass man keine Endlos-Schleifen Verknüpfung erzeugen darf/sollte. Theoretisch könnte ein Player das erkennen, und beim Einlesen der Daten abbrechen, wenn die verknüpfte Datei schon einmal in die virtuelle Zeitleiste aufgenommen wurde.

### Matroska Test Dateien
[Hard-Linking Specs](https://github.com/hubblec4/Matroska-Playback/blob/master/files/HardLinking/HardLinkingSpecs.zip)

## Hard-Linking in der Praxis
Zuerst einmal ein paar Überlegungen zum System Hard-Linking.
Ein Player untersucht die Matroska Datei und findet dabei ein `PrevUID` Element mit einer SegmentUID. Das führt dazu, dass eine "Rückwärts Suche" gestartet werden muss. Weiterhin muss das `NextUID` Element untersucht werden, wodurch dann eine "Vorwärst Suche" gestartet werden muss.

#### Rückwärts Suche
Zuerst sucht der Player nach dieser Datei im Ordner. Wenn die Datei vorhanden ist, wird wiederum das `PrevUID` Element untersucht, UND nicht das `NextUID` Element. Dies wiederholt sich solange bis die "erste" Matroska Datei erreicht ist, bei der es keine `PrevUID` gibt, oder die Datei nicht vorhanden ist.

#### Vorwärts Suche
Der Vorgang ist ähnlich wie bei der "Rückwärst Suche". Allerdings muss immer das `NextUID` Element untersucht werden.

### Weitere Hard-Linking Möglichkeiten
Alle Player die ich getestet habe, scheinen nach diesem Prinzip zu arbeiten. Daher habe ich mir weiter Hard-Linking Möglichkeiten einfallen lassen. In meinem [chapterEditor](https://forum.doom9.org/showthread.php?t=169984) Projekt kann man sehr bequem diese verschiedenen Varianten einrichten.

#### Hard-Linking nur mit dem `NextUID` Element
Ein Player wird somit immer nur in der Lage sein eine "Vorwärst Suche" zu starten. Nur wenn man die erste Matroska Datei öffnet, wird der gesamte Inhalt aller verknüpften Dateien abgespielt.

Zum Beispiel für eine Serie, bei der jede Folge als erstes, immer den gleichen Vorspann hat, und anschließend einen Rückblick. Vorspann, Rückblick und der Episodenteil liegen separat als Matroska Datei vor. Möchte man die komplette Folge sehen, dann startet man die Vorspann-Datei. Möchte man keinen Vorspann sehen aber den Rückblick, dann startet man die Rückblick-Datei. Und möchte man nur den Episodenteil sehen, dann eben diese Datei starten.

##### Matroska Test Dateien
[Hard-Linking NextUID](https://github.com/hubblec4/Matroska-Playback/blob/master/files/HardLinking/HardLinkingNextUID.zip)

#### Hard-Linking nur mit dem `PrevUID` Element
Ein Player wird somit immer nur in der Lage sein eine "Rückwärst Suche" zu starten. Nur wenn man die letzte Matroska Datei öffnet, wird der gesamte Inhalt aller verknüpften Dateien abgespielt.

Nutzen wir wieder unser Serien Beispiel, nur das wir diesmal einen Abspann als separate Datei haben. Wenn man die Apspann Datei startet wird die gesamte Folge abgespielt. Startet man nur die Episodenteil-Datei dann wird die Abspann Datei nicht verwendet.

##### Matroska Test Dateien
[Hard-Linking PrevUID](https://github.com/hubblec4/Matroska-Playback/blob/master/files/HardLinking/HardLinkingPrevUID.zip)