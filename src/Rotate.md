# Rotation of a video track
Matroska offers the possibility to rotate a video track around the z-axis during playback. Of course, only if the player can read and process the instructions.

##  With the Matroska element `ProjectionPoseRoll`
The element is included in the header of the video track.

[Matroska test file](https://github.com/hubblec4/Matroska-Playback/blob/master/files/Rotate/RotateProjectionPoseRoll.mkv)

## With Matroska Tags
Matroska Tags can also be used to rotate the video. However, this is not officially documented in the Matroska specs and only a few players can read the Matroska Tags. A software developer should not prefer this variant.

#### Test files
[XML Matroska Tags file](https://github.com/hubblec4/Matroska-Playback/blob/master/files/Rotate/Rotate_Tags.xml)

[Matroska file](https://github.com/hubblec4/Matroska-Playback/blob/master/files/Rotate/Rotate_Tags.mkv)