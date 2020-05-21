# Raspberry Pi setup

A raspberry Pi will host JMRI and also the Arduino environment to program the arduino for DCC++.

## Prerequisites

You need:

- a Raspberry Pi
  - I am using a Raspberry Pi 4 Model B with 4 GB of memory, but you should be able to use a Raspberry Pi 3 Model B with 1GB memory or the Pi 4 with 1 or 2 GB memory.
- microSD card of at least 16GB
- Raspberry Pi power supply
- optionally a case for the Raspberry Pi - a Raspberry Pi 4 can run quite warm, so a heat sync case or a case that allows good airflow is recommended
- On your computer you need to install an application to be able to remotely control the Raspberry Pi and see the Raspbery Pi desktop.  The best option is to install is [RealVNC viewer](https://www.realvnc.com/en/connect/download/viewer/)

### Additional setup for Windows users

Windows users will need the following software installed to be able to work with the Raspberry Pi:

- [Bonjour Print Services](https://support.apple.com/kb/dl999?locale=en_GB)
- [putty](https://putty.org)

## Setup

- Download the latest [raspbian image](https://www.raspberrypi.org/downloads/raspbian/).  I used the desktop version, but without the recommended software installed.
- unarchive the image
- flash the image to a micro SD card.  There is a recommended application on the Raspberry Pi site, but I use [belana etcher](https://www.balena.io/etcher/)
- Once the image is flashed the SD card will be ejected from your system.  You need to reinsert it and create an empty file called ssh in the boot partition.  To do this open a command line window then cd into the boot partition directory on the sd card and enter the following command:
  - ```touch ssh``` on mac and linux
  - ```type NUL >> ssh``` on windows using command prompt 
  - ```echo $null >> ssh``` on windows using PowerShell
- Optionally, if you need to use WiFi rather than an ethernet connection create a file called **wpa_supplicant.conf** and ensure it has the following content (*modify the 2 letter country code, NETWORK_NAME and NETWORK_PASSWORD to match your location and WiFi you want to connect to*)
  ```text
  ctrl_interface=DIR=/var/run/wpa_supplicant
  GROUP=netdev
  update_config=1
  country=GB

  network={
	ssid="NETWORK_NAME"
	psk="NETOWRK_PASSWORD"
  }
  ```

- Eject the microSD card from your computer and insert it into the Raspberry Pi
- Connect the Ethernet cable if needed and the power supply to the raspberry pi to power up the raspberry pi.  On initial boot the raspberry pi will appear on the network using hostname raspberrypi.local.  

```<TODO - add basic setup, initial loginm raspi config and update here>```

- Add additional software using the command ```sudo apt install -y netatalk```
- Download the JMRI software using command ```wget https://github.com/JMRI/JMRI/releases/download/v4.18/JMRI.4.18+R37ad3d0.tgz```
- uncompress the downloaded file with command ```tar zxvf JMRI.4.18+R37ad3d0.tgz```
- Move JMRI to the /opt directory and tidy up temporary files with command ```cd /opt && sudo cp -R ~/JMRI JMRI && rm -rf ~/JMRI && rm ~/JMRI.4.18+R37ad3d0.tgz```

## Setup DCC++

- Open a browser and navigate to ```https://www.arduino.cc/en/Main/Software```.  Download the Arduino IDE for **Linux ARM 32 bits***
- expand the downloaded file with comand ```cd Downloads && tar zxvf arduino-1.8.12-linuxarm.tar.xz```
- install arduino using command ```cd arduino-1.8.12 && sudo ./install.sh```
- download DCC++ code using command ```cd ~ && git clone https://github.com/DccPlusPlus/BaseStation.git```
- connect the arduino to the Raspberry Pi using a USB cable
- launch the Arduino IDE using a desktop connection over VNC.  The application should be in the system menu under programming
- open the DCC++ application using **File**->**Open** then navigate to the **pi/BaseStation/DCCpp_Uno** directory and open file **DCCpp_Uno.ino**
- set the correct board type, using menu **Tools**->**Board** and select **Arduino Uno** or **Arduino Mega or Mega 2560**, choosing the appropriate value for your Arduino board
- set the connection port, using menu **Tools**->**Board** and select **/dev/ttyACM0** or the port that indicates it has your board attached
- verify the processor is set correctly in menu **Tools**->**Processor** (if using a Mega you can choose the original Mega or Mega 2560)
- press the upload button (arrow to right), which will compile and then upload the program to your Arduino board