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
Ein Player untersucht die Matroska Datei und findet dabei ein `PrevUID` Element mit einer UID. Das führt dazu, dass eine "Rückwärts Suche" gestartet werden muss. Weiterhin muss das `NextUID` Element untersucht werden, wodurch dann eine "Vorwärst Suche" gestartet werden muss.

#### Rückwärts Suche
Zuerst sucht der Player nach dieser Datei im Ordner. Wenn die Datei vorhanden ist, wird wiederum das `PrevUID` Element untersucht, UND nicht das `NextUID` Element. Dies wiederholt sich solange bis die "erste" Matroska Datei erreicht ist, bei der es keine `PrevUID` gibt, oder die Datei nicht vorhanden ist.

#### Vorwärts Suche
Der Vorgang ist ähnlich wie bei der "Rückwärst Suche". Allerdings muss immer das `NextUID` Element untersucht werden.