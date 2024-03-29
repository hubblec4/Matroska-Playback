# Matroska Player Overview
This overview should show which players use which Matroska features.

## MPC-HC
MPC-HC internally uses the LAV Filter/Splitter. This adds up the used Matroska features. Furthermore, other external DirectShow filters can be used, such as the Haali Splitter, which can be used to further Matroska features.

[Test version is MPC-HC 1.8.6(clsid)](https://github.com/clsid2/mpc-hc/releases/tag/1.8.6)

Matroska features | present | is working | comment
------------------|:-------:|:----------:|----------
[Basic Chapters](BasicChapters.md) | yes | very good |
[Multiple chapter names](BasicChapters.md#multiple-chapter-names)| no | |
[Nested Chapters](NestedChapters.md) | yes | very good |
[Ordered Chapters](OrderedChapters.md) | yes | very good |
[Nested Ordered Chapters](NestedOrderedChapters.md) | yes | good | only start times are used
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

Test version is MPC-BE.1.5.6.6000.x64

Matroska features | present | is working | comment
------------------|:-------:|:----------:|----------
[Basic Chapters](BasicChapters.md) | yes | good | no display in the timeline, cumbersome chapter selection in submenus, chapter flags are ignored
[Multiple chapter names](BasicChapters.md#multiple-chapter-names)| no | |
[Nested Chapters](NestedChapters.md) | yes | good | Chapter display corresponds to the usual standard
[Ordered Chapters](OrderedChapters.md) | no | | only start times are used
[Nested Ordered Chapters](NestedOrderedChapters.md) | no | |
[Matroska Editions](EditionEntry.md)| no | | the 1st Edition is always used
[Selection of Matroska Editions](EditionEntry.md#editions-selection-in-the-player) | no | |
[Matroska Hard-Linking](HardLinking.md)| no | |
[Matroska Medium-Linking (Chapter-Segment-Linking)](ChapterSegmentLinking.md)| no | |
[Matroska Soft-Linking (Matroska DVD menu)](MatroskaMenu.md#matroska-dvd-menu-matroska-soft-linking)| no | |
[Native Matroska menu](MatroskaMenu.md#native-matroska-menu)| no | |
[Video Rotation](Rotate.md)| yes | very good |
[TRACKSETEX](TRACKSETEX.md)| no | |
[Tracks selection per chapter](ChapterTrack.md)| no | |

## VLC
The VLC player has an internal Matroska Demuxer/Splitter programmed by Matroska founder Steve Lhomme.

Test version is vlc-3.0.7-20190514-0510-win64

Matroska features | present | is working | comment
------------------|:-------:|:----------:|----------
[Basic Chapters](BasicChapters.md) | yes | good | Chapter selection in a submenu, Chapter flag `ChapterFlagEnabled` is ignored
[Multiple chapter names](BasicChapters.md#multiple-chapter-names)| yes | good | All chapter names are put together into a string. The language is not really taken into account.
[Nested Chapters](NestedChapters.md) | yes | good | Chapter display corresponds to the usual standard
[Ordered Chapters](OrderedChapters.md) | yes | good | Playing time is not correct if there are deactivated chapters
[Nested Ordered Chapters](NestedOrderedChapters.md) | yes | good | only start times are used
[Matroska Editions](EditionEntry.md) | yes | very good |
[Selection of Matroska Editions](EditionEntry.md#editions-selection-in-the-player) | yes | bad | Switching Editions does not work properly
[Matroska Hard-Linking](HardLinking.md) | yes | good | Problems with the chapter display, the series-intro-credits test crashes VLC, timeline is not correct
[Matroska Medium-Linking (Chapter-Segment-Linking)](ChapterSegmentLinking.md) | yes | good | `ChapterSegmentEditionUID` is not supported, problems with chapter display
[Matroska Soft-Linking (Matroska DVD menu)](MatroskaMenu.md#matroska-dvd-menu-matroska-soft-linking) | yes | no more | only worked in a very early version of the VLC
[Native Matroska menu](MatroskaMenu.md#native-matroska-menu) | yes | very good |
[Video Rotation](Rotate.md) | no | |
[TRACKSETEX](TRACKSETEX.md) | no | |
[Tracks selection per chapter](ChapterTrack.md) | no | |

## mpv
The [mpv player](https://mpv.io) is an open source project that is currently working on a lot.

Test version is mpv-x86_64-20190513-git-64cdc36

Matroska features | present | is working | comment
------------------|:-------:|:----------:|----------
[Basic Chapters](BasicChapters.md) | yes | bad | no chapter selection menu, no chapter names in the timeline, chapter flags `ChapterFlagEnabled` and` ChapterFlagHidden` are ignored
[Multiple chapter names](BasicChapters.md#multiple-chapter-names)| no | |
[Nested Chapters](NestedChapters.md) | no | |
[Ordered Chapters](OrderedChapters.md) | yes | good | Playing time is not correct if there are deactivated chapters
[Nested Ordered Chapters](NestedOrderedChapters.md) | no | |
[Matroska Editions](EditionEntry.md) | yes | good | which Edition is used is not apparent
[Selection of Matroska Editions](EditionEntry.md#editions-selection-in-the-player) | yes | bad | awkward, a mpv command must be used
[Matroska Hard-Linking](HardLinking.md)| no | |
[Matroska Medium-Linking (Chapter-Segment-Linking)](ChapterSegmentLinking.md) | yes | good | `ChapterSegmentEditionUID` is supported
[Matroska Soft-Linking (Matroska DVD menu)](MatroskaMenu.md#matroska-dvd-menu-matroska-soft-linking)| no | |
[Native Matroska menu](MatroskaMenu.md#native-matroska-menu)| no | |
[Video Rotation](Rotate.md) | no | |
[TRACKSETEX](TRACKSETEX.md) | no | |
[Tracks selection per chapter](ChapterTrack.md) | no | |