# Matroska Player Overview
This overview should show which players use which Matroska features.

## MPC-HC
MPC-HC internally uses the LAV Filter/Splitter. This adds up the used Matroska features. Furthermore, other external DirectShow filters can be used, such as the Haali Splitter, which can be used to further Matroska features.

[Test version is MPC-HC 1.8.6(clsid)](https://github.com/clsid2/mpc-hc/releases/tag/1.8.6)

Matroska features | present | is working | comment
------------------|:-------:|:----------:|----------
[Basic Chapters](BasicChapters.md) | yes | very good |
[Nested Chapters](NestedChapters.md) | yes | very good |
[Ordered Chapters](OrderedChapters.md) | yes | very good |
[Nested Ordered Chapters](NestedOrderedChapters.md) | yes | good |
[Matroska Editions](EditionEntry.md)| yes | very good |
[Selection of Matroska Editions](EditionEntry.md#editions-selection-in-the-player) | yes | good | no internal Edition menu, very good menu in the Splitter (LAV or Haali)
[Matroska Hard-Linking](HardLinking.md)| yes | very good | Video track is perfectly seamlessly connected
[Matroska Medium-Linking (Chapter-Segment-Linking)](ChapterSegmentLinking.md)| yes | very good | `ChapterSegmentEditionUID` is not supported
[Matroska Soft-Linking (Matroska DVD menu)](MatroskaMenu.md#matroska-dvd-menu-matroska-soft-linking)| no | |
[Native Matroska menu](MatroskaMenu.md#native-matroska-menu)| no | |
[Video Rotation](Rotate.md)| yes | very good | only with the Matroska Tags, `ProjectionPoseRoll` is not supported
[TRACKSETEX](TRACKSETEX.md)| no | very good | only with the Haali Splitter
[Tracks selection per chapter](ChapterTrack.md)| no | |

## MPC-BE
For testing, the internal Matroska Splitter is used. MPC-BE can also load external splitters, such as the LAV or Haali Splitter, and then behave like the MPC-HC player.

Test version is MPC-BE.1.5.4.4545.x64

Matroska features | present | is working | comment
------------------|:-------:|:----------:|----------
[Basic Chapters](BasicChapters.md) | yes | good | no display in the timeline, cumbersome chapter selection in submenus, chapter flags are ignored
[Nested Chapters](NestedChapters.md) | yes | good | Chapter display corresponds to the usual standard
[Ordered Chapters](OrderedChapters.md) | no | | only start times are used
[Nested Ordered Chapters](NestedOrderedChapters.md) | no | |
[Matroska Editions](EditionEntry.md)| no | | the 1st Edition is always used
[Selection of Matroska Editions](EditionEntry.md#editions-selection-in-the-player) | no | |
[Matroska Hard-Linking](HardLinking.md)| no | |
[Matroska Medium-Linking (Chapter-Segment-Linking)](ChapterSegmentLinking.md)| no | |
[Matroska Soft-Linking (Matroska DVD menu)](MatroskaMenu.md#matroska-dvd-menu-matroska-soft-linking)| no | |
[Native Matroska menu](MatroskaMenu.md#native-matroska-menu)| no | |
[Video Rotation](Rotate.md)| yes | very good | only with the Matroska Tags, `ProjectionPoseRoll` is not supported
[TRACKSETEX](TRACKSETEX.md)| no | |
[Tracks selection per chapter](ChapterTrack.md)| no | |