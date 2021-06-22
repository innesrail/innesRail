# Digital Command Control (DCC)

DCC provides a way for a controller to communicate with individual components of a railway system over the rail tracks.  A digital signal running at 8KHz is encoded in the power provided to the tracks.  Each locomotive and some additional control modules have a decoder which can read the digital signal from the tracks to receive the digital signal.  Each decode must be assigned a unique address within a layout.  The addresses default to ID 3 at manufacture, so must be configured when being introduced to a new layout.

Using DCC overcomes many of the limitations of analog control, as the entire track can now be powered all the time and multiple vehicles can the be independently controlled on the same track.

The digital signal also allows control of specific features, so lighting and sounds on board a locomotive can be controlled.  It also means that signals and points can also be controlled from the controller, using additional controller boards with on board DCC decoders.

The train speed and direction is no longer controlled by the power being supplied to the track, as in analog systems, often referred to as **DC** systems.  The track power remains at a constant level and instructions sent to the decoders on board a locomotive control the motors, hence the speed and direction.

DCC only works in one direction, the controller sends signals onto the track.  The controller cannot receive any data from the decoders on the track via DCC.  However, there is an extension to the DCC standard which does allow decoders to write a small amount of data to the track for, this is not widely adopted my commercial systems and some commercial systems have competing extensions, which are not part of the DCC standard to provide this data back channel.  To be able to read the data from a decoder there usually needs to be additional hardware installed on the layout.  This topic is discussed further in the [Block Detection](BlockDetection.md) section.

To receive feedback from sensors around the layout, DCC is not used.  There is a complementary [NMRA standard](https://www.nmra.org) called [**Layout Command Control (LCC)**](LCC).

## Useful websites

- [DCCWiki](https://dccwiki.com/Main_Page)

## Open source projects

DCC++ : The implementation of a DCC controller based on an Arduino with the motor shield installed.

Original [project]() seems to have been abandoned but there is activity on [DCC++ Ex](https://dcc-ex.github.io), but this new project seems to be expanding scope beyond that of the original DCC++ project.

Git repositories

- Original project : [DCC++](https://github.com/DccPlusPlus)
- [DCC++ EX](https://github.com/DCC-EX)