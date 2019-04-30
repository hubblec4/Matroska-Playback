# Matroska Hard-Linking
Hard-Linking is the "weakest" kind of Matroska-Linking to virtually and seamlessly connect Matroska files. For this procedure the elements `PrevUID` and` NextUID` are used. These elements are located in the Segment/Info section of a Matroska file.

When loading a Matroska file, a player must examine these elements and check that the PrevUID or NextUID element specifies a SegmentUID that belongs to another Matroska file that must be in the same folder.

#### Weak Hard-Linking
If an ordered edition with [Ordered Chapters](OrderedChapters.md) is used, then Hard-Linking must be ignored.

[Hard-Linking "Weak" Test files](https://github.com/hubblec4/Matroska-Playback/blob/master/files/HardLinking/HardLinkingWeak.zip)

#### Chapters and Hard-Linking
If there are chapters in the Matroska files then the chapter times for the chapter markers must be adjusted/shifted. Only the start times of the chapters are used.

Which chapters, from which edition should be used?

It may happen that there are multiple editions in the open file. As already mentioned, the edition may not be ordered. Let's say the 2nd edition has to be used by the player. Then the player should also use the 2nd edition of all linked files. However, if there is no 2nd edition in any of the linked files, then no chapter markers will be created for this file.

How and which chapters are used by the linked files, the current players handle very different. For example, the LAV splitter always uses the 1st edition from the linked files. If there is an edition with the `EditionFlagDefault` element, the chapters of this edition will be used.

The first test file has 2 editions and the 2nd is the default edition. Likewise, the second and final test file has 2 editions, but none is defined as default. The other test files have only one edition.

[Hard-Linking multiple editions Test files](https://github.com/hubblec4/Matroska-Playback/blob/master/files/HardLinking/HardLinkingWithMultipleEditions.zip)

## Matroska Specs
The Matroska Specs state that the 1st Matroska file must not have a `PrevUID` and the last Matroska file must not have` NextUID`. All "intermediate" files must use both elements.
This ensures that no matter what file you open in the player, the entire contents of all linked files will be played.

It should be noted that one must/should not create an endless loops linkage. Theoretically, a player could detect this, and abort when reading in the data if the linked file has already been included in the virtual timeline.

[Hard-Linking Specs Test files](https://github.com/hubblec4/Matroska-Playback/blob/master/files/HardLinking/HardLinkingSpecs.zip)

## Hard-Linking in practice
First of all, a few thoughts on the system Hard-Linking.
A player examines the Matroska file and finds a `PrevUID` element with a SegmentUID. This causes a "Backward search" to be started. Furthermore, the `NextUID` element has to be examined, which then has to start a 'Forward search'.

#### Backward search
First, the player searches for this file in the folder. If the file exists, again the `PrevUID` element is examined, but NOT the` NextUID` element. This is repeated until the "first" Matroska file is reached, where there is no `PrevUID`, or the file to be linked is not available.

#### Forward search
The process is similar to the "Backward search". However, the `NextUID` element must always be examined.

### Further Hard-Linking possibilities
All the players I tested seem to work on this principle. That's why I came up with more Hard-Linking options. In my [chapterEditor](https://forum.doom9.org/showthread.php?t=169984) project you can easily set up these different variants.

#### Hard-Linking with `NextUID` element only
A player will thus always be able to start a "forward search". Only when opening the first Matroska file will all the contents of all linked files be played.

For example, for a series in which each episode always has the same intro, and then a review. The intro, the review, and the episodic part are available separately as a Matroska file. If you want to see the complete episode, start the intro file. If you do not want to see an intro but the review, then you start the review file. And if you only want to see the episode part, then just start this file.

[Hard-Linking NextUID Test files](https://github.com/hubblec4/Matroska-Playback/blob/master/files/HardLinking/HardLinkingNextUID.zip)

#### Hard-Linking nur mit dem `PrevUID` Element
Ein Player wird somit immer nur in der Lage sein eine "Rückwärst Suche" zu starten. Nur wenn man die letzte Matroska Datei öffnet, wird der gesamte Inhalt aller verknüpften Dateien abgespielt.

Nutzen wir wieder unser Serien Beispiel, nur das wir diesmal einen Episodenteil und einen Abspann als separate Dateien haben. Wenn man die Apspann Datei startet, dann wird die gesamte Folge abgespielt. Startet man nur die Episodenteil-Datei, dann wird die Abspann Datei nicht verwendet.

[Hard-Linking PrevUID Test Dateien](https://github.com/hubblec4/Matroska-Playback/blob/master/files/HardLinking/HardLinkingPrevUID.zip)

#### Hard-Linking gemischtes Nutzen der `NextUID` und `PrevUID` Elemente
Die folgenden drei Varianten nutzen auf sehr unterschiedliche Weise diese beiden Matroska Elemente. Es kommt dabei vor, dass eine Datei selbst keines der beiden Elemente nutzt, aber dennoch Bestandteil der Verknüpfungskette ist. Diese Varianten sind sehr hilfreich für Serien, bei denen die Folgen immer den gleichen Vor- und/oder Abspann haben.

##### Episoden mit Vorspann
Es gibt nur eine Vorspann Datei und viele weitere Episoden Dateien. Jede Episoden Datei nutzt die `PrevUID`, um die Vorspann Datei zu verknüpfen. Die Vorspann Datei nutzt keine Verknüpfungen und wird daher immer nur alleine abgespielt. Man könnte natürlich eine `NextUID` zuweisen, aber eben nur zu einer Episoden Datei.

[Hard-Linking Serien-Vorspann Test Dateien](https://github.com/hubblec4/Matroska-Playback/blob/master/files/HardLinking/HardLinkingSeriesIntro.zip)

##### Episoden mit Abspann
Es gibt nur eine Abspann Datei und viele weitere Episoden Dateien. Jede Episoden Datei nutzt die `NextUID`, um die Abspann Datei zu verknüpfen. Die Abspann Datei nutzt keine Verknüpfungen und wird daher immer nur alleine abgespielt. Man könnte natürlich eine `PrevUID` zuweisen, aber eben nur zu einer Episoden Datei.

[Hard-Linking Serien-Abspann Test Dateien](https://github.com/hubblec4/Matroska-Playback/blob/master/files/HardLinking/HardLinkingSeriesCredits.zip)

##### Episoden mit Vorspann und Abspann
Bei dieser Variante gibt es eine Vorspann und eine Abspann Datei, sowie auch weitere Episoden Dateien. Jede Episoden Datei nutzt die `NextUID`, um die Abspann Datei zu verknüpfen. Jede Episoden Datei nutzt die `PrevUID`, um die Vorspann Datei zu verknüpfen. Die Vor- und Abspann Datei haben keine Verknüpfungen und werden daher immer nur alleine abgespielt.

[Hard-Linking Serien-Vorspann-Abspann Test Dateien](https://github.com/hubblec4/Matroska-Playback/blob/master/files/HardLinking/HardLinkingSeriesIntroCredits.zip)

## Probleme beim Hard-Linking
Die Test Dateien wurden mit mkvmerge aus einer "großen" Datei aufgeteilt. Mkvmerge kann nur an den Schlüsselbildern "schneiden". Weiterhin unterliegt Matroska einer Beschränkung, was dass Speichern der Audio Daten angeht. Daher ist bei sehr vielen Matroska Dateien die längste Spur-Spieldauer, die einer Audiospur.

Fast alle Player die ich getestet habe verknüpfen die Matroska Dateien so, dass alle Daten bis zum Ende verwendet werden. Das führt aber dazu, dass das Video dann "hängen" bleibt. Nur der Lav-Splitter (und Haali-Splitter) arbeiten hier besser. Ich kann es nicht genau bestätigen, aber es werden anscheinden nur solange Daten von einer Datei verwendet, solange es auch Videodaten gibt.

Das Matroska Dateien nicht richtig miteinander verknüpft sind, sieht man in den Playern sehr gut an der gesamt Spieldauer. Diese war dann immer ein paar Sekunden zu hoch. Die Test Dateien sind aber anscheinden alle sehr gut "geschnitten" und auch VLC kann die richtig abspielen(allerdings funktioniert die Zeitleiste nicht richtig ->VLC.bug).