# Matroska EditionEntry
Die wortwörtliche Übersetzung wäre "Ausgabe-Eintrag". Ich verwende den Begriff "Version" in der Beschreibung.

Alle Kapitel befinden sich immer innerhalb einer Version und es können mehere Versionen vorhanden sein. Ebenso kann eine Version reihenfolgentreu sein und eine andere nicht.

Es gibt momentan 3 Schalter(0=nein, 1=ja) für die Version. Allerdings sind die Matroska Specs nicht klar definiert und es gibt Unstimmigkeiten im Umgang mit den Schaltern.

## `EditionFlagOrdered`
Wenn bei diesem Element der Wert 1 gesetzt wird, dann ist die Version reihenfolgentreu und verwendet [Reihenfolgetreue Kapitel](#OrderedChapters.md).

## `EditionFlagHidden`
Wenn bei diesem Element der Wert 1 gesetzt wird, dann ist die Version unsichtbar und es werden keine Kapitelmarker für die Zeitleiste generiert. Weiterhin sollte ein Player diese Version NICHT "anzeigen", dass bedeutet der Benutzer kann diese Version weder sehen noch auswählen.

## `EditionFlagDefault`
Wenn bei diesem Element der Wert 1 gesetzt wird, dann ist die Version
die Standard Version und soll vom Player bevorzugt verwendet werden.

Leider kann dieses Element in jeder Version vorkommen und man hätte dann mehrere Standard Versionen. Hinzu kommt, dass festgelegt worden ist, dass das `EditionFlagHidden` Element eine "höhere" Wertigkeit hat. Dadurch wird bei gewissen Einstellungen das `EditionFlagDefault` Element negiert und eine NICHT Standard Version ist dann trotzdem die Standard Version. 

Das ist meiner Meinung nach alles sehr viel Verwirrung und ich hatte vollgendes vorgeschlagen für die Matroska Specs.

Das `EditionFlagDefault` Element muss in die Ebene 1 verschoben werden und ist dann nur noch einmal vorhanden und müsste vielleicht umbenannt werden zu `EditionDefaultUID`.

### Meine Empfehlung für einen Player
Die "erste" Version bei der das `EditionFlagDefault` Element gefunden wurde und den Wert 1 hat, ist die Standard Verison. Diese Version MUSS dann verwendet werden auch wenn sie unsichtbar ist.

Ein guter Matroska Player sollte ein schnell zu erreichendes Auswahlmenü für die Versionen besitzen. Ähnlich wie wenn man die Audiospur oder Untertitelspur wechseln kann.