# Matroska Player Overview
This overview should show which players use which Matroska features.

## MPC-HC
MPC-HC internally uses the LAV Filter/Splitter. This adds up the used Matroska properties. Furthermore, other external DirectShow filters can be used, such as the Haali Splitter, which can be used to further Matroska properties.

Matroska properties | present | is working | comment
--------------------|:-------:|:----------:|----------
[Basic Chapters](BasicChapters.md) | yes | very good |
[Nested Chapters](NestedChapters.md) | yes | very good |
[Ordered Chapters](OrderedChapters.md) | yes | very good |
[Nested Ordered Chapters](NestedOrderedChapters.md) | yes | good |
[Matroska Editions](EditionEntry.md)| yes | very good |
Selection of Matroska Editions | yes | good | no internal Edition menu, very good menu in the Splitter (LAV or Haali)
[Matroska Hard-Linking](HardLinking.md)| yes | very good | Video track is perfectly seamlessly connected
[Matroska Medium-Linking (Chapter-Segment-Linking)](ChapterSegmentLinking.md)| yes | good | `ChapterSegmentEditionUID` is not supported
[Matroska Soft-Linking (Matroska DVD menu)](MatroskaMenu.md#matroska-dvd-menu-matroska-soft-linking)| no | |
[Native Matroska menu](MatroskaMenu.md#native-matroska-menu)| no | |
[Video Rotation](Rotate.md)| yes | very good | only with the Matroska Tags, `ProjectionPoseRoll` is not supported
[TRACKSETEX](TRACKSETEX.md)| no | very good | only with the Haali Splitter
[Tracks selection per chapter](ChapterTrack.md)| no | |