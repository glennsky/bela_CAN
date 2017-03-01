To enable CAN on Bela's I2C1 connector (J2):

remove the pullup resistors R21 / R22 and attach a CAN transceiver
the am335x-bone*.dtb files in /boot/uboot/dtbs need to be modified to use other pins for the I2C1 to allow CAN on those pins
the BB-DCAN1-00A0.dtbo device tree overlay must be loaded at startup - copy to /lib/firmware
/etc/rc.local file used to start CAN at startup - set for 500Kbps + extended 16 message TXQUEUE - adjust as needed

run:  ./copy_to_bela  script to copy the files to the needed places when these files are on the Beaglebone
to recompile the .dtb and .dtbo files - use the compile_dtb* scripts

easiest is to reboot to get things working. if all goes well, you'll see can0 when you do 'ifconfig'
if there are any problems, check 'dmesg' for pertinent messages:  'dmesg | grep -i CAN' 

tested only on a Beaglebone Green with Bela v0.1.0a to v0.2.0b images

install can-utils for useful socketcan routines -- such as "candump can0" which will show packets received
  sudo apt-get install can-utils


----

v0.1 - 01-mar-2017 - glenn@this.is

