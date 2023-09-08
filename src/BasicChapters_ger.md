# Matroska Basis Kapitel

Ein Basis Kapitel verwendet nur die Startzeit und den Kapitelnamen.
Wenn das Kapitel unsichtbar oder deaktiviert ist, dann werden keinerlei Daten von diesem Kapitel verwendet.  
Die Kapitelzeiten sollten aufsteigend in der Matroska Datei vorliegen. Wenn das nicht so ist, dann müssen die Kapitelzeiten sortiert werden.  
Kapitelzeiten die größer als die gesamte Spieldauer der Datei sind müssen ignoriert werden.

### Test Dateien

[XML Kapitel Datei](/files/BasicChapters/BasicChapters.xml)

[Matroska Datei](/files/BasicChapters/BasicChapters.mkv)

## Multiple Kapitelnamen

Matroska bietet die Möglichkeit für ein Kapitel mehrere Namen mit mehreren Sprachen zu vergeben. Die meisten Player nutzen immer nur den ersten Namen, egal welche Sprache dieser hat.

### Test Dateien

[XML Kapitel Datei](/files/BasicChapters/Multiple-Chapter-Names.xml)

[Matroska Datei](/files/BasicChapters/Multiple-Chapter-Names.mkv)

Die Matroska Testdatei enthält 3 Sprachen, English, Deutsch und Französisch, jeweils als Audio Spur und als Untertitel Spur.

Ein guter Player wechselt die Kapitelnamen automatisch anhand der verwendeten Audiospur und deren Sprache.