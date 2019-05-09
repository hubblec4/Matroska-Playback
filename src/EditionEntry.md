# Matroska EditionEntry
I use the term "Edition" in the description.

All chapters are always within one Edition and there may be multiple Editions. Likewise, one Edition may be ordered and another may not.

There are currently 3 flags (0=no, 1=yes) for the Edition. However, the Matroska specs are not clearly defined and there are disagreements in dealing with the flags.

## `EditionFlagOrdered`
If this element is set to 1 then the Edition is ordered and uses [Ordered Chapters](#OrderedChapters.md).

## `EditionFlagHidden`
If this element is set to 1 then the Edition is hidden/invisible and no chapter markers are generated for the timeline. Furthermore, a player should NOT "show" this Edition, meaning the user can not see or select this Edition.

## `EditionFlagDefault`
If this element is set to 1 then the Edition is
the default Edition and should be preferred by the player.

Unfortunately this element can be found in every Edition and you would have several default Editions. In addition, it has been determined that the `EditionFlagHidden` element has a "higher" value. As a result, the `EditionFlagDefault` element is negated in certain settings and a non-default Edition is still the default Edition.

It's all a lot of confusion in my opinion and I suggested the following for the Matroska specs.

The `EditionFlagDefault` element has to be moved to level 1 and then exists only once and might have to be renamed `EditionDefaultUID`.

### My recommendation for a player
The "first" Edition where the `EditionFlagDefault` element was found and has the value 1 is the default Edition. This Edition MUST be used even if it is hidden.

A good Matroska player should have a quick-to-reach selection menu for the Editions. Similar to when you can change the audio track or subtitle track.

## Test files
There are always two Editions and only the second is ordered and the third chapter is disabled. This lacks 10 seconds of video and you can see more quickly which Edition is being used after starting. I've prepared a few examples for the numerous possibilities that arise through the combinations of Edition flags.

#### Editsion 1 non-ordered - Edition 2 ordered
The player should play the 1st Edition.

[XML Matroska Chapters file](https://github.com/hubblec4/Matroska-Playback/blob/master/files/EditionEntry/E1nonOrdered-E2Ordered.xml)

[Matroska file](https://github.com/hubblec4/Matroska-Playback/blob/master/files/EditionEntry/E1nonOrdered-E2Ordered.mkv)

#### Edition 1 non-ordered - Edition 2 ordered default
The player should play the 2nd Edition.

[XML Matroska Chapters file](https://github.com/hubblec4/Matroska-Playback/blob/master/files/EditionEntry/E1nonOrdered-E2OrderedDefault.xml)

[Matroska file](https://github.com/hubblec4/Matroska-Playback/blob/master/files/EditionEntry/E1nonOrdered-E2OrderedDefault.mkv)

#### Edition 1 non-ordered - Edition 2 ordered hidden default
All tested players play the 1st Edition, because the 2nd Edition is hidden. A player should play but the 2nd Edition, because it is the default Edition.

[XML Matroska Chapters file](https://github.com/hubblec4/Matroska-Playback/blob/master/files/EditionEntry/E1nonOrdered-E2OrderedHiddenDefault.xml)

[Matroska file](https://github.com/hubblec4/Matroska-Playback/blob/master/files/EditionEntry/E1nonOrdered-E2OrderedHiddenDefault.mkv)

#### Edition 1 non-ordered hidden - Edition 2 ordered
The player should play the 2nd Edition, because the 1st Edition is hidden.

[XML Matroska Chapters file](https://github.com/hubblec4/Matroska-Playback/blob/master/files/EditionEntry/E1nonOrderedHidden-E2Ordered.xml)

[Matroska file](https://github.com/hubblec4/Matroska-Playback/blob/master/files/EditionEntry/E1nonOrderedHidden-E2Ordered.mkv)

#### Edition 1 non-ordered hidden default - Edition 2 ordered default
All tested players play the 2nd Edition, because the 1st Edition is hidden. A player should play but the first Edition, because it is the first default Edition.

[XML Matroska Chapters file](https://github.com/hubblec4/Matroska-Playback/blob/master/files/EditionEntry/E1nonOrderedHiddenDefault-E2OrderedDefault.xml)

[Matroska file](https://github.com/hubblec4/Matroska-Playback/blob/master/files/EditionEntry/E1nonOrderedHiddenDefault-E2OrderedDefault.mkv)

## Edition Name
Unfortunately, such a subelement is missing in the Edition structure and you have to use the Matroska Tags.

For each Edition a `Tag` element must be used. In `Targets` elment, the corresponding UID is entered in the `TagEditionUID` element (in the XML only `EditionUID`). In the `SimpleTag` (in the XML only` Simple`) the official Matroska tag "TITLE" is entered in the `TagName` (in the XML only` Name`) and in the `TagString` element (in the XML only` String`) a name is saved for the Edition.