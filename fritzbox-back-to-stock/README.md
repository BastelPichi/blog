# Installing Fritz!OS on your OpenWRT-flashed Fritz!Box
After installing OpenWRT on my FritzBox, I couldn't get back into the FTP-Bootloader to install FritzOS. Even the official Fritz-recovery couldn't help. So heres what i figured out:
1) What you need:
   - Soldering Iron, Solder, Jumper Wires
   - An USB to Serial
   - An windows PC: Everything should be similar on Linux, however i've done this on an Windows.
2) Start by opening your FritzBox.
  You can do this by unscrewing the screws on the back and carefully popping of the top.
3) Soldering time!
   Flip the PCB and locate the 4 debugging pins. Solder your jumper wires to them and connect up your USB-to-Serial:
   Image

4) Connect Putty to your USB-to-Serial.
   Then startup the FritzBox. You should see an shell like-prompt named Eva-AVM. Type help to make sure you can send to the FritzBox. One of the LEDs should be blinking green.
5) Continue like normal.
   Download [FritzFlash](https://github.com/freifunk-darmstadt/fritz-tools/blob/master/fritzflash.py). Grab your Firmware file from [here](http://download.avm.de/fritzbox/). Select your FritzBox, select deutschland, select fritz.os, download the .image file.
   Rename the .image file to .tar, extract it using Winrar. In ./var/tmp, there should be an kernel.image. Copy that to the Directory you saved fritzflash in.
   ```
   fritzflash.py --image kernel.image
   ```
   Follow on-screen instructions. You should also see some progress happen on Putty.

6) You should now be able to remove your USB-to-Serial.

7) The FritzBox wouldn't really work directly, so I had to:
   - Set IP to 169.254.1.2 (gateway 169.254.1.1)
   - Open 169.254.1.1 in a browser
   - Do an Firmware Reset via the "Lost Password" option
      
   Now your FritzBox should be back working on the official FritzOS!
