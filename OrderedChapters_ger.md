# Matroska Reihenfolgentreue Kapitel
Vorraussetzung: Der Versions Schalter "reihenfolgentreu" ist aktiv.

Bei dieser Art von Kapiteln muss eine Spieldauer für jedes Kapitel ermittelt werden (Endzeit minus Startzeit), die dann zu einer virtuellen Gesamtspieldauer addiert wird. Die Reihenfolge der Kapitel muss dabei eingehalten werden. Weiterhin müssen die Kapitelmarken(Anzeigepunkte auf der Zeitleiste) berechnet werden. Wenn ein reihenfolgentreues Kapitel unsichtbar ist, dann wird dessen Spieldauer zur nächsten Spieldauer eines sichtbaren Kapitels addiert.

Eine negative Spieldauer ist illegal und ein solches Kapitel wird vollkommen ignoriert.

Es gibt einen Spezialfall, bei dem die Spieldauer eines Kapitels 0 ist. Ein solches reihenfolgentreues Kapitel verhält sich dann wie ein Basis Kapitel. Die Startzeit muss innerhalb der Gesamtspieldauer liegen und wird als Kapitelmarke verwendet.

#### Test Dateien
[XML Kapitel Datei](https://github.com/hubblec4/Matroska-Playback/blob/master/files/BasicChapters/BasicChapters.xml)

[Matroska Datei](https://github.com/hubblec4/Matroska-Playback/blob/master/files/BasicChapters/BasicChapters.mkv)