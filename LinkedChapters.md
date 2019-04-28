# Matroska Linked Chapters
This designation is currently not included in the Matroska specs.

For a [Ordered Chapter](OrderedChapters.md), a link to another file can be established using the `ChapterSegmentUID` element. When creating the virtual timeline, the player must use the content from the linked file.

Furthermore, the element `ChapterSegmentEditionUID` can be used to specifically use the content of an edition.

All ordered chapters and their combination with nesting are then a linking chapter when a SegmentUID is specified in the `ChapterSegmentUID` element.