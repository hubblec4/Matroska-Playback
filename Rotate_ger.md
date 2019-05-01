# Rotation einer Videospur
Matroska bietet die Möglichkeiten eine Videospur um die z-Achse während des Abspielens zu drehen. Natürlich nur, wenn der Player die Anweisungen auslesen und verarbeiten kann.

##  Mit dem Matroska Element `ProjectionPoseRoll`
Seit kurzem erst ist diese Element direkt in der Videospur enthalten und sollte von nun an genutzt werden.

[Matroska Test Datei](https://github.com/hubblec4/Matroska-Playback/blob/master/files/Rotate/RotateProjectionPoseRoll.mkv)

## Mit Matroska Tags
Es können auch Matroska Tags verwendet werden um das Video zu "drehen". Allerdings ist dies nicht offiziell in den Matroska Specs dokumentiert und nur ein paar wenige Player können die Matroska Tags auslesen. Ein Software Entwickler sollte diese Variante nicht bevorzugt verwenden.

#### Test Dateien
[XML Matroska Tags Datei](https://github.com/hubblec4/Matroska-Playback/blob/master/files/Rotate/Rotate_Tags.xml)

[Matroska Datei](https://github.com/hubblec4/Matroska-Playback/blob/master/files/Rotate/Rotate_Tags.mkv)