# Matroska EditionEntry
Die wortwörtliche Übersetzung wäre "Ausgabe-Eintrag". Ich verwende den Begriff "Version" in der Beschreibung.

Alle Kapitel befinden sich immer innerhalb einer Version und es können mehrere Versionen vorhanden sein. Ebenso kann eine Version reihenfolgentreu sein und eine andere nicht.

Es gibt momentan 3 Schalter(0=nein, 1=ja) für die Version. Allerdings sind die Matroska Specs nicht klar definiert und es gibt Unstimmigkeiten im Umgang mit den Schaltern.

## `EditionFlagOrdered`
Wenn bei diesem Element der Wert 1 gesetzt wird, dann ist die Version reihenfolgentreu und verwendet [Reihenfolgetreue Kapitel](OrderedChapters_ger.md).

## `EditionFlagHidden`
Wenn bei diesem Element der Wert 1 gesetzt wird, dann ist die Version unsichtbar und es werden keine Kapitelmarker für die Zeitleiste generiert. Weiterhin sollte ein Player diese Version NICHT "anzeigen", dass bedeutet der Benutzer kann diese Version weder sehen noch auswählen.

## `EditionFlagDefault`
Wenn bei diesem Element der Wert 1 gesetzt wird, dann ist die Version
die Standard Version und soll vom Player bevorzugt verwendet werden.

Leider kann dieses Element in jeder Version vorkommen und man hätte dann mehrere Standard Versionen. Hinzu kommt, dass festgelegt worden ist, dass das `EditionFlagHidden` Element eine "höhere" Wertigkeit hat. Dadurch wird bei gewissen Einstellungen das `EditionFlagDefault` Element negiert und eine NICHT Standard Version ist dann trotzdem die Standard Version.

Das ist meiner Meinung nach alles sehr viel Verwirrung und ich hatte folgendes vorgeschlagen für die Matroska Specs.

Das `EditionFlagDefault` Element muss in die Ebene 1 verschoben werden und ist dann nur noch einmal vorhanden und müsste vielleicht umbenannt werden zu `EditionDefaultUID`.

### Meine Empfehlung für einen Player
Die "erste" Version bei der das `EditionFlagDefault` Element gefunden wurde und den Wert 1 hat, ist die Standard Verison. Diese Version MUSS dann verwendet werden auch wenn sie unsichtbar ist.

Ein guter Matroska Player sollte ein schnell zu erreichendes Auswahlmenü für die Versionen besitzen. Ähnlich wie wenn man die Audiospur oder Untertitelspur wechseln kann.

## Test Dateien
Es gibt immer zwei Versionen und nur die zweite ist reihenfolgentreu und das dritte Kapitel ist deaktiviert. Dadurch fehlen 10 Sekunden des Videos und man kann schneller erkennen welche Version nach dem Starten verwendet wird. Ich habe ein paar Beipiele, für die zahlreichen Möglichkeiten, die durch die Kombinationen der Versions Schalter entstehen, vorbereitet.

#### Version 1 nicht reihenfolgentreu - Version 2 reihenfolgentreu
Der Player sollte die 1. Version abspielen.

[XML Matroska Kapitel Datei](/files/EditionEntry/E1nonOrdered-E2Ordered.xml)

[Matroska Datei](/files/EditionEntry/E1nonOrdered-E2Ordered.mkv)

#### Version 1 nicht reihenfolgentreu - Version 2 reihenfolgentreu Standard
Der Player sollte die 2. Version abspielen.

[XML Matroska Kapitel Datei](/files/EditionEntry/E1nonOrdered-E2OrderedDefault.xml)

[Matroska Datei](/files/EditionEntry/E1nonOrdered-E2OrderedDefault.mkv)

#### Version 1 nicht reihenfolgentreu - Version 2 reihenfolgentreu unsichtbar Standard
Alle getesteten Player spielen die 1. Version ab, weil die 2. Version unsichtbar ist. Ein Player sollte aber die 2. Version abspielen, weil sie die Standard Version ist.

[XML Matroska Kapitel Datei](/files/EditionEntry/E1nonOrdered-E2OrderedHiddenDefault.xml)

[Matroska Datei](/files/EditionEntry/E1nonOrdered-E2OrderedHiddenDefault.mkv)

#### Version 1 nicht reihenfolgentreu unsichtbar - Version 2 reihenfolgentreu
Der Player sollte die 2. Version abspielen, weil die 1. Version unsichtbar ist.

[XML Matroska Kapitel Datei](/files/EditionEntry/E1nonOrderedHidden-E2Ordered.xml)

[Matroska Datei](/files/EditionEntry/E1nonOrderedHidden-E2Ordered.mkv)

#### Version 1 nicht reihenfolgentreu unsichtbar Standard - Version 2 reihenfolgentreu Standard
Alle getesteten Player spielen die 2. Version ab, weil die 1. Version unsichtbar ist. Ein Player sollte aber die 1. Version abspielen, weil sie die erste Standard Version ist.

[XML Matroska Kapitel Datei](/files/EditionEntry/E1nonOrderedHiddenDefault-E2OrderedDefault.xml)

[Matroska Datei](/files/EditionEntry/E1nonOrderedHiddenDefault-E2OrderedDefault.mkv)

## Versions Name
Leider fehlt ein solches Unterelement in der Versionsstruktur und man muss die Matroska Tags benutzen.

Für jede Version muss ein `Tag` Element benutzt werden. Im `Targets` Elment wird im `TagEditionUID` Element (im XML nur `EditionUID`) die entsprechende UID eingetragen. Im `SimpleTag` (im XML nur `Simple`) wird im `TagName` (im XML nur `Name`) der offizielle Matroska Tag "TITLE" eingegeben und im `TagString` Element (im XML nur `String`) wird ein Name für die Version gespeichert.

In den Matroska Test Dateien haben die Versionen einen Namen, der in den Matroska Tags enthalten ist.