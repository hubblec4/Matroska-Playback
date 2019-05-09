# Matroska Nested Chapters
Nested chapters behave in a similar way to the [Basic Chapters](BasicChapters.md) when the edition flag "ordered" is set to false. But there are two conditions that should be considered.

1. Condition: The start times of the nested chapters must not be smaller than the start time of the parent chapter.
2. Condition: The start times must be less than the start time of the next parent chapter.

#### Disabled parent chapter
In this case, all nested chapters must be ignored.

#### Hidden parent chapter
The current Matroska specs say that all nested chapters are also hidden, even if its own flag "hidden" is set to false. However, this is not the case for practice. All players I've tried show all nested chapters that are visible to themselves.
This behavior is very useful/important for creating Matroska Menu structures based on Chapter-Segment-Linking.

#### Presentation of the nested chapters in the player
Most players use a "+" before the chapter name to indicate the level of nesting. A chapter which is in the 2nd nesting level has two "+" in front of the name.

Parent Chapter  
+Nested Chapter Level 1  
++Nested Chapter Level 2

This is the most common form when all chapters are displayed on one level. For example in a popup menu.

Another option would be to replicate the nesting structure in a popup menu so that nested chapters are displayed in a submenu.
For a Matroska menu based on Chapter-Segment-Linking, many chapters are often used, sometimes almost 1000. It is then not possible to represent this number in a single level. You then have to search a lot and scroll in the chapter menu to find the desired chapter.

### Test files
[XML Chapter file](files/NestedChapters/NestedChapters.xml)

[Matroska file](files/NestedChapters/NestedChapters.mkv)