# Matroska Basic Chapters

A basic chapter uses only the start time and the chapter name.
If the chapter is invisible or disabled then no data from this chapter will be used.  
The chapter times should be in ascending order in the Matroska file. If this is not the case then the chapter times have to be sorted.  
Chapter times greater than the total playing time of the file must be ignored.

### Test files

[XML Chapters file](/files/BasicChapters/BasicChapters.xml)

[Matroska file](/files/BasicChapters/BasicChapters.mkv)

## Multiple chapter names

Matroska offers the option of assigning multiple names in multiple languages to a chapter. Most players only use the first name, no matter what language it is.

### Test files

[XML Chapter File](/files/BasicChapters/Multiple-Chapter-Names.xml)

[Matroska file](/files/BasicChapters/Multiple-Chapter-Names.mkv)

The Matroska test file contains 3 languages, English, German and French, each as an audio track and a subtitle track.

A good player will automatically change chapter names based on the audio track used and its language.