# Automatic Break Control (ABC) systems

There are a number of technologiess (none of them part of the DCC standard), that provide a mechanism to signal a decoder to automatically stop.  This enables the layout to prevent a train going through a red signal.

To enable this feature you need to have a compatible decode and track circuitry to enable this feature.

Some features are manufacturer specific (where there is no published data how the feature works) so you need to source the DCC controller and power booster/block detection hardware from the same manufacturer and install a decoder that supports the features.  It is primarily European manufacturers that provide these features:

- Zimo has HLU which is a multi-phase stopping solution which provides a more realistic controlled stop as a train moves through the multiple signal aspects protecting an occupied block
- Lenz has a system that allows a 2 phase breaking (slow down then stop)

There is a cruder ABC system that provides an **emergancy stop** function, where diodes can be used to provide an asymmetric track DCC signal in an isolated section of the track.  When an decoder which supports the feature detects to asymmetric signal it will come to a stop.  There is a configuration variable to determine how long the train will take to stop.