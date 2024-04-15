# Rotation of a video track
Matroska offers the possibility to rotate a video track around the z-axis during playback. Of course, only if the player can read and process the instructions.

##  With the Matroska element `ProjectionPoseRoll`
The element is included in the header of the video track and can contain values from -180 to 180. With negative values the video is rotated clockwise and with positive values it is rotated counterclockwise.

The rotation result for the values -180 and 180 is equal. The frames are then upside down.

At the beginning of February 2021, MPC-BE was the first player to implement support for the `ProjectionPoseRoll` element.
However, only values for the rotation that are a multiple of 90 are taken into account. (-180, -90, 90 180)

[Matroska test file: rotation -90](https://github.com/hubblec4/Matroska-Playback/blob/master/files/Rotate/RotateProjectionPoseRoll_-90.mkv)

[Matroska test file: rotation +90](https://github.com/hubblec4/Matroska-Playback/blob/master/files/Rotate/RotateProjectionPoseRoll_+90.mkv)

[Matroska test file: rotation 180](https://github.com/hubblec4/Matroska-Playback/blob/master/files/Rotate/RotateProjectionPoseRoll.mkv)

## With Matroska Tags
Matroska Tags can also be used to rotate the video. However, this is not officially documented in the Matroska specs and only a few players can read the Matroska Tags. A software developer should not prefer this variant.

The value for the rotation is an integer number and can only be positive. (0 < rotation < 360)
A value of 270 is the same as a value of -90 with the `ProjectionPoseRoll` element.

#### Test files
[XML Matroska Tags file](https://github.com/hubblec4/Matroska-Playback/blob/master/files/Rotate/Rotate_Tags.xml)

[Matroska file](https://github.com/hubblec4/Matroska-Playback/blob/master/files/Rotate/Rotate_Tags.mkv)
