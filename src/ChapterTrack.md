# Matroska ChapterTrack - Track selection per chapter
The `ChapterTrack` element can only be used in [Ordered Chapters](OrderedChapters.md). If this element is not present, all the tracks will be available for the chapter. For all tracks to be used for a chapter, the corresponding track UID must be specified in the `ChapterTrackNumber` element. The term `ChapterTrackNumber` suggests that a track number should be used, but that is not the case. The track UID must be used.

Unfortunately, there is very little information about this element and in practice I do not know of a player that supports it.

The idea is to use only the desired tracks for different [Editions](EditionEntry.md). It could be used in a similar way to [TRACKSETEX](TRACKSETEX.md). However, only one track-set per chapter can be created. In addition, all chapters of an [Edition](EditionEntry.md) should use the same track-set.

### Test files
In the Matroska file there are two [Ordered Editions](EditionEntry.md), each with an [Ordered Chapter](OrderedChapters.md). The duration of the chapter is equal to the total duration of the file. There are two video and audio tracks, as well as 4 subtitle tracks.

In the first [Edition](EditionEntry.md) only the first video track, the first audio track and the first subtitle track should be used. In the second [Edition](EditionEntry.md) only the second video track, the second audio track and the third subtitle track should be used.

A player selects only these tracks and uses them for playback.

If multiple tracks of one type (for example, 3 audio tracks) have been selected, then the first track of each type should always be used for playback. If the `FlagDefault` flag is activated on one of the selected tracks, then that track should be used for playback. Some players can select tracks based on language, and if a track with the preferred language is present, it will be used for playback.

[XML Matroska Chapters file](/files/ChapterTrack/ChapterTrack.xml)

[Matroska file](/files/ChapterTrack/ChapterTrack.mkv)