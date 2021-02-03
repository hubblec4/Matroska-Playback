# Rotation einer Videospur
Matroska bietet die Möglichkeiten eine Videospur um die z-Achse während des Abspielens zu drehen. Natürlich nur, wenn der Player die Anweisungen auslesen und verarbeiten kann.

##  Mit dem Matroska Element `ProjectionPoseRoll`
Das Element ist in den Kopfdaten der Videospur enthalten und kann Werte von -180 bis 180 enthalten. Bei negativen Werten wird das Video gegen den Uhrzeigersinn gedreht und bei postiven Werten im Uhrzeigersinn.

Das Rotationsergebnis für die Werte -180 und 180 ist gleich. Die Bilder stehen dann auf dem Kopf.

Anfang Februar 2021 hat MPC-BE als erster Player die Unterstützung für das `ProjectionPoseRoll` Element eingebaut.
Es werden aber nur Werte für die Rotation berücksichtigt die ein vielfaches von 90 sind. (-180, -90, 90 180)

[Matroska Test Datei: Rotation -90](https://github.com/hubblec4/Matroska-Playback/blob/master/files/Rotate/RotateProjectionPoseRoll_-90.mkv)
[Matroska Test Datei: Rotation +90](https://github.com/hubblec4/Matroska-Playback/blob/master/files/Rotate/RotateProjectionPoseRoll_+90.mkv)
[Matroska Test Datei: Rotation 180](https://github.com/hubblec4/Matroska-Playback/blob/master/files/Rotate/RotateProjectionPoseRoll.mkv)

## Mit Matroska Tags
Es können auch Matroska Tags verwendet werden um das Video zu "drehen". Allerdings ist dies nicht offiziell in den Matroska Specs dokumentiert und nur ein paar wenige Player können die Matroska Tags auslesen. Ein Software Entwickler sollte diese Variante nicht bevorzugt verwenden.

Der Wert für die Rotation ist eine ganzzahlige Zahl und kann nur positiv sein. (0 < Rotation < 360)
Ein Wert von 270 entspricht einem Wert von -90 mit dem `ProjectionPoseRoll` Element.

#### Test Dateien
[XML Matroska Tags Datei](https://github.com/hubblec4/Matroska-Playback/blob/master/files/Rotate/Rotate_Tags.xml)

[Matroska Datei](https://github.com/hubblec4/Matroska-Playback/blob/master/files/Rotate/Rotate_Tags.mkv)