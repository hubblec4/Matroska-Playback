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