# Layout Command Control (LCC)

## What is Layout command control

DCC provides a standard way for a controller to control a train, by placing a digital signal along with power on the tacks.  However, it does not provide a way for layout components, such as points, signals, turntables, crossings or various track sensing technologies to communicate.  When you think of how signals work on rail systems round the world they require sensors to detect when trains are within a track section (a block) and then signals automatically protect trains as they move through blocks.  As points are switched then the signals need to show the correct aspect, etc.  This communication requires 2 way communication and require a number of components to cooperate, which is not provided within the DCC standard, hence the need for Layout control.

## Competing technology available

There are a number of competing technologies in this space.  NMRA adopted a standard in 2016, but many manufacturers and other groups already had their own mechanism of providing Layout Control

- [LocoNet](https://www.digitrax.com/support/loconet/home/) - Digitrax.  This is licensed technology, though there is a [personal specification](https://www.digitrax.com/support/loconet/loconetpersonaledition.pdf) released for non-commercial use.  The technology has been licensed to a [number of other companies](https://www.digitrax.com/support/loconet/loconet-licensees/)
- [XpressNet](https://www.jmri.org/help/en/html/hardware/XPressNet/index.shtml) - Lenz (used by Atlas, Hornby, Lenz, OpenDCC (DIY), Paco Canada (DIY), Roco (some models), Viessmann and ZTC Controls)
- [CBUS](https://www.merg.org.uk/merg_resources/cbus.php) - MERG
- [C/MRI](https://www.nmra.org/sites/default/files/standards/sandrp/Other_Specifications/lcs-9.10.1_cmrinet_v1.1.pdf)

There are other technologies available but not listed.

It is unclear what the future will be as there a some very well established and supported technologies available that provide layout control and currently there is virtually no commercial support for the NMRA LCC standard.

## NMRA LCC Standard

The NMRA Layout Command Control standards are based on the [OpenLCB](https://www.openlcb.org) project.

LCC provides a bus for *nodes* to communicate.  This allows communication between multiple components controlling a layout.  LCC complements DCC, it does not replace it, but an implementation may choose to move some component control, such as signals and points, from DCC to LCC.

LCC uses **CAN** bus technology.  CAN is an industry standard protocol, which is used across a number of industries.  It provides an efficient mechanism for nodes on the bus to reliably communicate in potentially electrically *noisy* environments at high network utilisation, so is an ideal technology to use for layout control.

## Workshop/talks

- [LCC - Build a layout clinic](https://www.youtube.com/watch?v=00pYUJ7xqSo)
  - [file to accompany video](https://drive.google.com/file/d/0B-ixv6INHGIoQVNDdlFPaDBTcjA/view)
- [LCC talk](https://www.youtube.com/watch?v=P23-EuZ7AkU)
- [Basics of LCC](http://www.rr-cirkits.com/Clinics/MER-2016-LCC.pdf)

## Open source projects

- [OpenMRN](https://github.com/bakerstu/openmrn)

## OpenLCB unique ID range

I have been assigned range __05 01 01 01 5A *__