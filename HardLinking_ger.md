# Matroska Hard-Linking
Hard-Linking ist die einfachste Form, Matroska Dateien virtuell und nahtlos miteinander zu verbinden. Für dieses Verfahren werden die Elemente `PrevUID` und `NextUID` genutzt. Diese Elemente befinden sich in der Segment/Info Sektion einer Matroska Datei.

Beim Laden einer Matroska Datei muss ein Player diese untersuchen und prüfen ob im Element `PrevUID` oder `NextUID` eine UID angegeben ist, welche zu einer anderen Matroska Datei gehört, die sich im selben Ordner befinden muss.

Die Matroska Specs besagen, dass die 1. Matroska Datei keine `PrevUID` haben darf und die letzte Matroska Datei darf keine `NextUID` haben. Alle "zwischen liegenden" Dateien müssen beide Elemente verwenden.
Dadurch wird sichergestellt, dass egal welche Datei man im Player öffnet, der gesamte Inhalt aller verknüpften Dateien abgespielt wird.

### Matroska Test Dateien
[Hard-Linking Specs](https://github.com/hubblec4/Matroska-Playback/blob/master/files/HardLinking/HardLinkingSpecs.zip)