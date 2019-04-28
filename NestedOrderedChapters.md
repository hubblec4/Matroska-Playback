# Matroska Nested Ordered Chapters
This type of chapter automatically results from the combination of [Nested Chapters](NestedChapters.md) and [Ordered Chapters](OrderedChapters.md).

No information can be found in the Matroska Specs.

In practice, players only use the top-level [Oredered Chapters](OrderedChapters.md) to create the virtual timeline. For all [Nested Chapters](NestedChapters.md), only the start time is used for a chapter marker in the timeline. No playing time is calculated for the chapter.