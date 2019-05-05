# TRACKSETEX - Extended track selection
With TRACKSETEX, several predefined tracks can be changed with one action. In addition, a UID for an edition can be specified, so that it will be used.

TRACKSETEX is not an official part of the Matroska Specs and can only be realized with the Matroska Tags.

[Haali Splitter](https://haali.su/mkv/) the only software supports TRACKSETEX.

## TRACKSETEX structure
### Parameter
There are 6 parameters separated by a space. The last parameter is optional.

1. Edition UID
2. Video track UID oder track index
3. Audio track UID oder track index
4. Subtitle track UID oder track index
5. 3-letter language code (eng,ger)
6. an optional name for this TrackSet

### Predefined placeholders
#### The point `.`
The point `.` is officially provided for the parameters 2 to 4 and means that the currently selected track is NOT to be changed. If, for example, you only want to change the audio track, the point `.` is set in the 2nd and 4th parameters.

The point `.` can also be used for the 1st parameter. This means that the current edition should not be changed. Alternatively, one can enter any number that does not match any EditionUID. The 0 does not fit 100% to any edition UID, because the 0 is not allowed according to Matroska Specs.

#### The hash `#`
The hash `#` can be used for the parameters 2 to 4. This indicates that the following number is a track index. Without the hash `#` the number must be a UID belonging to the corresponding track.

The track index is equal to the index used by [mkvmerge](https://mkvtoolnix.download/doc/mkvmerge.html) for the tracks. It should be noted that each type of track has its own index counter. A first video track and a first audio track as well as a first subtitle track all have the index 0.

#### A small `x`
A small `x` is only used in the 4th parameter and ensures that no subtitle is displayed in the player.

## TRACKSETEX in Matroska Tags
A `Tag` is used with one `SimpleTag` (in the XML only `Simple`) for each TrackSet. No `Targets` element is used. In the `TagName` element (in the XML only `Name`) the keyword "TRACKSETEX" is entered and in the `TagString` element (in the XML only `String`) the parameters are stored.

## TRACKSETEX in practice
TRACKSETEX is not really widespread but I personally enjoyed it very much. With some Blu-rays, it may happen that an extended movie version is available, but which has only English sound. There are also forced subtitles for German and English and other languages. If you want to have a different language while watching the video and the associated subtitles, a user must perform two actions in the player. If now the other movie version must be selected, then this requires a third action of the user. With TRACKSETEX all 3 actions are reduced to one action. TRACKSETEX is a set of actions.

### Test files
[Matroska Tags XML file](https://github.com/hubblec4/Matroska-Playback/blob/TRACKSETEX/files/TRACKSETEX/TRACKSETEX.xml)

[Matroska file](https://github.com/hubblec4/Matroska-Playback/blob/TRACKSETEX/files/TRACKSETEX/TRACKSETEX.mkv)

Haali Splitter popup menu from system Tray Icon

![Haali Splitter popup menu](https://github.com/hubblec4/Matroska-Playback/blob/TRACKSETEX/files/TRACKSETEX/Haali-TRACKSETEX.jpg)