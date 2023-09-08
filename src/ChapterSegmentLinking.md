# Matroska Chapter-Segment-Linking

The official Matroska name is Medium-Linking.

For an [Ordered Chapter](OrderedChapters.md), a link to another file can be established using the `ChapterSegmentUID` element. When creating the virtual timeline, the player must use the content from the linked file.

Furthermore, the element `ChapterSegmentEditionUID` can be used to selectively use the content of an [Edition](EditionEntry.md).

## Link, only with the SegmentUID

In this variant, the start and end time of the chapter is used.
Both times must be within the playing time of the linked file.

### Test files

[XML Chapter file](/files/Chapter-Segment-Linking/Chapter-Segment-Linking.xml)

[Matroska files](/files/Chapter-Segment-Linking/Chapter-Segment-Linking.zip)

The zip folder contains several "Linked.mkv" files and a _Main.mkv file. In the _Main.mkv are all the chapters leading to the linked files.

## Link, with an additional SegmentEditionUID

If a `ChapterSegmentEditionUID` element is used, then the entire content of that linked edition must be played. The start and end times of such a chapter are ignored.
A player must then integrate the entire playing time of the edition for the virtual timeline.

### Test files

[XML Chapter file](/files/Chapter-Segment-Edition-Linking/Chapter-Segment-Edition-Linking.xml)

[Matroska files](/files/Chapter-Segment-Edition-Linking/Chapter-Segment-Edition-Linking.zip)

The test files use a simple way to link the contents of the files.
There are a variety of combinations of the link, including the possibility of an endless loop. This should be intercepted by a player.
