# Matroska Nested Ordered Chapters
This type of chapter automatically results from the combination of [Nested Chapters](NestedChapters.md) and [Ordered Chapters](OrderedChapters.md).

No information can be found in the Matroska Specs.

In practice, players only use the top-level [Ordered Chapters](OrderedChapters.md) to create the virtual timeline. For all [Nested Chapters](NestedChapters.md), only the start time is used for a chapter marker in the timeline. No playing time is calculated for the chapter.

#### Full nested ordered chapters
In this case, the playing time must be calculated for each [Nested Chapters](NestedChapters.md).

Chapter     | Start | End  | Duration | Current total playing time
------------|-------|------|----------|---------------------------
Chp 1       | 0s    | 10s  | 10s      | 10s
+Chp 1.1    | 10s   | 20s  | 10s      | 20s
+Chp 1.2    | 50s   | 60s  | 10s      | 30s
++Chp 1.2.1 | 20s   | 30s  | 10s      | 40s
Chp 2       | 30s   | 50s  | 20s      | 60s
+Chp 2.1    | 50s   | 60s  | 10s      | 70s

The Matroska test file will not play in any player as described here.

### Test files
[XML Chapter file](https://github.com/hubblec4/Matroska-Playback/blob/master/files/NestedOrderedChapters/NestedOrderedChapters.xml)

[Matroska file](https://github.com/hubblec4/Matroska-Playback/blob/master/files/NestedOrderedChapters/NestedOrderedChapters.mkv)