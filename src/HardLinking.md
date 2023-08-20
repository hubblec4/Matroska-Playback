# Matroska Hard-Linking
Hard-Linking is the "weakest" kind of Matroska-Linking to virtually and seamlessly connect Matroska files. For this procedure the elements `PrevUID` and` NextUID` are used. These elements are located in the Segment/Info section of a Matroska file.

When loading a Matroska file, a player must examine these elements and check that the `PrevUID` or `NextUID` element specifies a SegmentUID that belongs to another Matroska file that must be in the same folder.

#### Weak Hard-Linking
If an ordered edition with [Ordered Chapters](OrderedChapters.md) is used, then Hard-Linking must be ignored.

[Hard-Linking "Weak" test files](https://github.com/hubblec4/Matroska-Playback/blob/master/files/HardLinking/HardLinkingWeak.zip)

#### Chapters and Hard-Linking
If there are chapters in the Matroska files then the chapter times for the chapter markers must be adjusted/shifted. Only the start times of the chapters are used.

Which chapters, from which edition should be used?

It may happen that there are multiple editions in the open file. As already mentioned, the edition may not be ordered. Let's say the 2nd edition has to be used by the player. Then the player should also use the 2nd edition of all linked files. However, if there is no 2nd edition in any of the linked files, then no chapter markers will be created for this file.

How and which chapters are used by the linked files, the current players handle very different. For example, the LAV splitter always uses the 1st edition from the linked files. If there is an edition with the `EditionFlagDefault` element, the chapters of this edition will be used.

The first test file has 2 editions and the 2nd is the default edition. Likewise, the second and final test file has 2 editions, but none is defined as default. The other test files have only one edition.

[Hard-Linking multiple editions test files](https://github.com/hubblec4/Matroska-Playback/blob/master/files/HardLinking/HardLinkingWithMultipleEditions.zip)

## Matroska Specs
The Matroska Specs state that the 1st Matroska file must not have a `PrevUID` and the last Matroska file must not have` NextUID`. All "intermediate" files must use both elements.
This ensures that no matter what file you open in the player, the entire contents of all linked files will be played.

It should be noted that one must/should not create an endless loops linkage. Theoretically, a player could detect this, and abort when reading in the data if the linked file has already been included in the virtual timeline.

[Hard-Linking Specs test files](https://github.com/hubblec4/Matroska-Playback/blob/master/files/HardLinking/HardLinkingSpecs.zip)

## Hard-Linking in practice
First of all, a few thoughts on the system Hard-Linking.
A player examines the Matroska file and finds a `PrevUID` element with a SegmentUID. This causes a "Backward search" to be started. Furthermore, the `NextUID` element has to be examined, which then has to start a 'Forward search'.

#### Backward search
First, the player searches for this file in the folder. If the file exists, again the `PrevUID` element is examined, but NOT the` NextUID` element. This is repeated until the "first" Matroska file is reached, where there is no `PrevUID`, or the file to be linked is not available.

#### Forward search
The process is similar to the "Backward search". However, the `NextUID` element must always be examined.

#### Endless loop
It is possible (and very easy) to create an infinite loop with Hard-Linking.
To do this, simply link a file that is already included in the corresponding search direction.

[Hard-Linking with endless loop test files](https://github.com/hubblec4/Matroska-Playback/blob/master/files/HardLinking/HardLinkingWithEndlessLoop.zip)

### Further Hard-Linking possibilities
All the players I tested seem to work on this principle. That's why I came up with more Hard-Linking options. In my [chapterEditor](https://forum.doom9.org/showthread.php?t=169984) project you can easily set up these different variants.

#### Hard-Linking with `NextUID` element only
A player will thus always be able to start a "Forward search". Only when opening the first Matroska file will all the contents of all linked files be played.

For example, for a series in which each episode always has the same intro, and then a review. The intro, the review, and the episodic part are available separately as a Matroska file. If you want to see the complete episode, start the intro file. If you do not want to see an intro but the review, then you start the review file. And if you only want to see the episode part, then just start this file.

[Hard-Linking NextUID test files](https://github.com/hubblec4/Matroska-Playback/blob/master/files/HardLinking/HardLinkingNextUID.zip)

#### Hard-Linking with `PrevUID` element only
A player will thus always be able to start a "Backward search". Only by opening the last Matroska file will all the content of all linked files be played.

Let us use again our series example, only this time we have an episode part and a credits part as separate files. If you start the credits file, then the entire episode will be played. If you only start the episode file, the credits file will not be used.

[Hard-Linking PrevUID test files](https://github.com/hubblec4/Matroska-Playback/blob/master/files/HardLinking/HardLinkingPrevUID.zip)

#### Hard-Linking mixed use of `NextUID` and `PrevUID` elementes
The following three variants use these two Matroska elements in very different ways. It happens that a file itself does not use either of the two elements, but is still part of the linking chain. These variants are very helpful for series in which the episodes always have the same intro and/or credits.

##### Episodes with intro
There is only one intro file and many more episodes files. Each episode file uses the `PrevUID` to link the intro file. The intro file does not use links and is therefore always played by itself. Of course you could assign a `NextUID`, but only to one episode file.

[Hard-Linking Series-Intro test files](https://github.com/hubblec4/Matroska-Playback/blob/master/files/HardLinking/HardLinkingSeriesIntro.zip)

##### Episodes with credits
There is only one credits file and many more episodes files. Each episode file uses the `NextUID` to link the credits file. The credits file does not use links and is therefore always played by itself. Of course you could assign a `PrevUID`, but only to one episode file.

[Hard-Linking Series-Credits test files](https://github.com/hubblec4/Matroska-Playback/blob/master/files/HardLinking/HardLinkingSeriesCredits.zip)

##### Episodes with intro and credits
In this variant, there is an intro and a credits file, as well as other episodes files. Each episode file uses the `NextUID` to link the credits file. Each episode file uses the `PrevUID` to link the intro file. The intro and credits file have no links and are therefore always played by itself.

[Hard-Linking Series-Intro-Credits test files](https://github.com/hubblec4/Matroska-Playback/blob/master/files/HardLinking/HardLinkingSeriesIntroCredits.zip)

## Problems with Hard-Linking
The test files were split with mkvmerge from a "big" file. Mkvmerge can only "cut" on the keyframes. Furthermore, Matroska is subject to a limitation in terms of storing the audio data. Therefore, for many Matroska files, the longest track playing time is that of an audio track.

Almost all the players I have tested link the Matroska files so that all the data is used to the end. But this leads to the video then "hanging" remains. Only the Lav Splitter (and Haali Splitter) work better here. I can not confirm it exactly, but it will only appear as long as data from a file is used, as long as there is video data.

The Matroska files are not properly linked, you can see in the players very well on the total playing time. This was always a few seconds too high. The test files are very well "cut", because even VLC can play correctly (but the timeline does not work properly -> VLC.bug).

I uploaded test files for VLC some time ago. For these files, the audio data is longer than the video data and therefore the picture always "hangs" a bit.

[Hard-Linking issue test files 1](https://forum.videohelp.com/attachments/45588-1525907432/Matroska-Hard-Linking%20sample1.7z)

[Hard-Linking issue test files 2](https://forum.videohelp.com/attachments/45589-1525907957/Matroska-Hard-Linking%20sample2.7z)