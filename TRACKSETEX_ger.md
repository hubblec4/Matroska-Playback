# TRACKSETEX - Erweiterte Spurenauswahl
Mit TRACKSETEX können mehrere vordefinierte Spuren mit einer Aktion gewechselt werden. Zusätzlich kann noch eine Versionen UID angegeben werden, damit diese dann verwendet wird.

TRACKSETEX ist kein offizieller Bestandteil der Matroska Specs und kann nur mit den Matroska Tags realisiert werden.

[Haali Splitter](https://haali.su/mkv/) ist die einzigste Software die TRACKSETEX unterstützt.

## TRACKSETEX in der Praxis
TRACKSETEX ist nicht wirklich weit verbreitet aber ich persönlich habe es sehr gern genutzt. Bei einigen Blu-rays kann es vorkommen, dass eine erweiterte Filmversion vorhanden ist, welche aber nur Englishen Ton hat. Weiterhin gibt es erzwungene Untertitel für Deutsch und English und andere Sprachen. Wenn man während des Video schauens eine andere Sprache haben möchte und die dazugehörigen Untertitel, so muss ein Benutzer zwei Aktionen im Player ausführen. Wenn nun noch die andere Filmversion ausgewählt werden muss, dann bedarf dies einer dritten Aktion des Benutzers. Mit TRACKSETEX werden alle 3 Aktionen auf eine Aktion reduziert. TRACKSETEX ist ein Set von Aktionen.

## TRACKSETEX Aufbau
### Parameter
Es gibt 6 Parameter, die durch ein Leerzeichen getrennt sind. Der letzte Parameter ist optional.

1. Versionen UID
2. Videospur UID oder Spurindex
3. Audiospur UID oder Spurindex
4. Untertitel UID oder Spurindex
5. 3-buchstabiger Sprachcode (eng,ger)
6. ein optionaler Name für dieses TrackSet

### vordefinierte Platzhalter
#### Der Punkt `.`
Der Punkt `.` ist offiziell für die Parameter 2 bis 4 vorgesehen und bedeutet, dass die aktuell ausgewählte Spur NICHT gewechselt werden soll. Wenn man zum Beispiel nur die Audiospur wechseln möchte, dann wird im 2. und 4. Parameter der Punkt `.` gesetzt.

Der Punkt `.` kann auch für den 1.Parameter genutzt werden. Dies bedeutet, dass die aktuelle Version nicht gewechselt werden soll. Alternativ könnte man irgendeine Zahl eingeben, die zu keiner VerisonsUID passt. Die 0 passt 100% zu keiner VersionsUID, weil die 0 laut Matroska Specs nicht erlaubt ist.

#### Die Raute `#`
Die Raute `#` kann für die Parameter 2 bis 4 benutzt werden. Diese gibt an, dass die folgende Zahl ein Spurindex ist. Ohne die Raute `#` muss die Zahl eine UID sein, die zu der entsprechenden Spur gehört.

Der Spurindex ist gleich dem Index, den [mkvmerge](https://mkvtoolnix.download/doc/mkvmerge.html) für die Spuren verwendet. Zu beachten ist, dass jede Art von Spur einen eigenen Index-Zähler hat. Eine 1.Videospur und eine 1.Audiospur sowie eine 1.Untertitelspur haben allen den Index 0.

#### Ein kleines `x`
Ein kleines `x` wird nur im 4.Parameter verwendet und sorgt dafür, dass kein Untertitel im Player angezeigt werden soll.