# Matroska Ordered Chapters
Prerequisite: The Edition flag "ordered" is enabled.

In this type of chapters, a playing time has to be determined for each chapter (end time minus start time), which is then added to a virtual total playing time. The order of the chapters must be followed. Furthermore, the chapter marks (display points on the timeline) must be calculated. If an ordered chapter is hidden, then its playing time is added to the next playing time of a visible chapter.

A negative playing time is illegal and such a chapter is completely ignored.

There is a special case where the playing time of a chapter is 0. Such an ordered chapter then behaves like a [Basic Chapter] (BasicChapters.md). The start time must be within the total playing time and is only used as a chapter marker.

#### Disabled chapters
The chapter named "disabled" is disabled and will not be used. Therefore, the total playing time is only 55 seconds and not 60 seconds (file playing time).

### Test files
[XML Chapters file (ordered chapter times)](https://github.com/hubblec4/Matroska-Playback/blob/master/files/OrderedChapters/OrderedChapters_ordered.xml)
Bei diesem Beispiel wird das Video "normal" von vorn nach hinten abgespielt. Version 1 in der Matroska Datei.