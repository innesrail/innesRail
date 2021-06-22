# Block Detection

Block detection allows the presence of a train on a specific section of track to be automatically detected.  There are a number of different technologies available, but the main options in use are:

- detect currect draw fron the track
- use opto sensors to identify rolling stock at a specific location

The current draw allows the presence of rolling stock anywhere within a section of track (similar to block circuit on real railways) where as the opto-sensors provide information about when an exact position on track

## Sample Circuits

- [Comparator Based DCC](http://www.circuitous.ca/DccBOD339393.html)
- Current Sensing - see links at bottom of this page

## Decoder transmission to identify loco occupying block

There is part of the DCC standard that allows a decoder to transmit a small amount of information.  However, this needs to be supported in by the components providing power to the track and there needs to be sensors around the track that can read the data from decoders and publish it.  

Not all controllers or power boosters support the NMRA decoder transmission DCC standard and some manufacturers implement a proprietary, incompatible system, so if you want this feature you need to ensure that the controller/power boosters, loco decoders are compatible and there are modules installed on the layout that can read the decoder data from the track.

## Useful sites

- [Current Sensing and Occupancy Detection for DCC](http://thenscaler.com/?p=1080)
- [Block Detection](http://www.wiringfordcc.com/blockdet.htm)
- [Current Sensing](http://www.trainelectronics.com/DCC_Arduino/Current_Sense/index.htm)
