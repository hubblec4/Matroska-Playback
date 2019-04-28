# Matroska Reihenfolgentreue Kapitel
Vorraussetzung: Der Versions Schalter "reihenfolgentreu" ist aktiv.

Bei dieser Art von Kapiteln muss eine Spieldauer für jedes Kapitel ermittelt werden (Endzeit minus Startzeit), die dann zu einer virtuellen Gesamtspieldauer addiert wird. Die Reihenfolge der Kapitel muss dabei eingehalten werden. Weiterhin müssen die Kapitelmarken(Anzeigepunkte auf der Zeitleiste) berechnet werden. Wenn ein reihenfolgentreues Kapitel unsichtbar ist, dann wird dessen Spieldauer zur nächsten Spieldauer eines sichtbaren Kapitels addiert.

Eine negative Spieldauer ist illegal und ein solches Kapitel wird vollkommen ignoriert.

Es gibt einen Spezialfall, bei dem die Spieldauer eines Kapitels 0 ist. Ein solches reihenfolgentreues Kapitel verhält sich dann wie ein [Basis Kapitel](BasicChapters_ger.md). Die Startzeit muss innerhalb der Gesamtspieldauer liegen und wird als Kapitelmarke verwendet.

##### Deaktivierte Kapitel

Das Kapitel mit dem Namen "disabled" ist deaktiviert und wird nicht verwendet. Daher ist die Gesamtspieldauer nur 55 Sekunden und nicht 60 Sekunden(Datei-Spieldauer).

#### Test Dateien
[XML Kapitel Datei (geordnete Kapitelzeiten)](https://github.com/hubblec4/Matroska-Playback/blob/master/files/OrderedChapters/OrderedChapters_ordered.xml)

Bei diesem Beispiel wird das Video "normal" von vorn nach hinten abgespielt. Version 1 in der Matroska Datei.

[XML Kapitel Datei (nicht geordnete Kapitelzeiten)](https://github.com/hubblec4/Matroska-Playback/blob/master/files/OrderedChapters/OrderedChapters_unordered.xml)

Bei diesem Beispiel wird das Video teilweise von hinten nach vorn abgespielt, da die Kapitelzeiten vertauscht sind. Version 2 in der Matroska Datei.

[Matroska Datei](https://github.com/hubblec4/Matroska-Playback/blob/master/files/OrderedChapters/OrderedChapters.mkv)

Die 1.Version startet automatisch. Die 2.Version kann im Player ausgewählt werden, wenn der Player Matroska Versionen unterstützt.