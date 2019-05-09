# Matroska Menu
For the Matroska menu, [Ordered Chapters](OrderedChapters.md) and a "Chapter CODEC" are used. Within a chapter there is a `ChapProcess` element. This master element stores (almost) all the necessary data for the Matroska menu.

#### Chapter CODEC
A Chapter CODEC is a software that knows all Matroska menu commands and can process them. The commands must be able to be received and sent.

There are currently two existing menu systems and a third is planned.

## Native Matroska Menu
To use this system the value 0 has to be used in the `ChapProcessCodecID` element. `ChapProcessCodecID` has a default value of 0 and therefore does not necessarily exist.

At the moment there is only one command `GotoAndPlay (ChapterUID);`, where you have to jump to a certain chapter.

Only in the VLC player native Matroska menu was installed, but not in all versions. For testing such a Matroska file I had used version 3.

The test file contains the `GotoAndPlay ();` command in the 5th chapter. It should be jumped to the second chapter before the 5th chapter is played.

#### Test files
[XML Matroska chapter file](https://github.com/hubblec4/Matroska-Playback/blob/master/files/MatroskaMenu/Native/GotoAndPlay.xml)

[Matroska file](https://github.com/hubblec4/Matroska-Playback/blob/master/files/MatroskaMenu/Native/GotoAndPlay.mkv)

## Matroska DVD Menu (Matroska Soft-Linking)
To use this system, the value 1 must be used in the` ChapProcessCodecID` element.

Matroska borrows the DVD menu system. The structure of the menu, the DVD commands and the VOB-Butons are used. In addition, a "Control Track" is still used for the interactions.

In the Segment/Info(`ChapterTranslate` and` SegmentFamily`) and in the Tracks(`TrackTranslate`) there are further elements belonging to this system.

Only in VLC player this system is installed, but it does not work anymore in today's versions.

[DVDMenuXtractor](https://github.com/Matroska-Org/dvdmenuxtractor) can decompose a DVD into its components, but it is very outdated and no longer works with today's MKVToolNix.

I took a StarTrek TNG DVD for the test files. Only the XML files and the VOB-Buton file are included in the zip.

[Matroska DVD Menu test files](https://github.com/hubblec4/Matroska-Playback/blob/master/files/MatroskaMenu/DVD/MatroskaDVDMenuTNG-S6-D1.zip)

## Interactive Movie
This system is [planned](https://wiki.videolan.org/SoC_2019/#Interactive_movie_support) for the VLC player, but not yet part of the Matroska Specs.

