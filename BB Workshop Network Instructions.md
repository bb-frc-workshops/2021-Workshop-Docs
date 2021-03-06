# **BB Workshop Network Instructions**
Please follow these instructions to setup your Romi prior to attending the Workshop. This is meant to prepare you so that your Romi, Pi, and PC are fully configured so that you can fully communicate with your robot from VS Code.

## **Recommended Software**
Here is a list of recommended software. Click on each link to navigate to tne download locations.
1. [FRC 2021 VS Code](https://github.com/wpilibsuite/allwpilib/releases/tag/v2021.3.1) (about 3 GB) for robot code (instructions for installation can be found [here](https://docs.wpilib.org/en/stable/docs/zero-to-robot/step-2/wpilib-setup.html)). Downloads are at the bottom of web page.

 ![image](./VSCodeDownload.png)

2. [Romi image](https://dev.azure.com/wpilib/RuntimeSupport/_build/results?buildId=17296&view=artifacts&pathAsName=false&type=publishedArtifacts) (about 10 GB) Download and extract it. You will use the file *WPILibPi_image-v2021.3.1-3-g7bd028a_2021-10-01-Romi.zip*.

 ![image](./RomiImageDownload.png)

2. [Etcher](https://www.balena.io/etcher/) (about 0.3 GB) if you need to image your Pi, use image above and instructions for installing [here](https://docs.wpilib.org/en/stable/docs/software/vision-processing/wpilibpi/installing-the-image-to-your-microsd-card.html)
3. Optional - [Angry IP Scanner](https://angryip.org/) (about 0.002 GB) for identifying IP address of Romi when in bridge mode
4. Optional - [Bonjour](https://support.apple.com/kb/dl999?locale=en_US) (about 0.004 GB) for resolving Romi hostname of wpilibpi


## **Pre-requisite - Fully Charged Batteries!** 
The Romi robot drains batteries incredibly fast. Please ensure you have fully charged batteries as well as 6 additional AA batteries for back up. It takes a long time to recharge batteries and the last thing you want to be stuck with is a dead robot.

## **Step 1: Imaging**
1. Start with the official [Romi instructions](https://docs.wpilib.org/en/stable/docs/romi-robot/imaging-romi.html)
    1. Note that the Romi micro USB port should be connected to a Raspberry Pi USB port before powering on.
    2. A good indication of when the Pi will be ready to connect via Access Point is when the green light on the Pi stops flashing.
3. When you get to **Wireless Network Setup**, if can't connect to [http://wpilibpi.local](http://wpilibpi.local) but can to IP address directly, your computer is struggling to resolve the hostname from mDNS. Try downloading and installing [Bonjour](https://support.apple.com/kb/dl999?locale=en_US)
4. Setup Pi Network settings
    1. Set Pi in update mode by clicking on the "Writable" on top of the web page.
    2. Navigate to "Network Settings" in the left navigation panel.
    3. Set "Wifi Mode" to Bridge
    4. Set "Wifi Address" to DHCP
    5. Set "SSID" to your local network name
    6. Set "WPA2 Passhrase" to the network password
    7. Click "Save" (just once). You connection will drop from the Pi.
   
   ![image](./PiUIBridgeModeNumbered.png)

5. Wait 15 seconds (web page should grey)
6. Restart PI
7. Connect your computer to the local network if you have not done so already.
8. Open Angry IP Scanner (only needed if [http://wpilibpi.local](http://wpilibpi.local) doesn't resolve)
    1. Range should default to local network. Click Start.
	2. Once scan is complete, search for "wpilibpi.xxxx" in hostname. It can take a minute or 2 for the Pi to fully boot, so if it doesn't show initially, try rescanning.
	3. Note IP address
    
    ![image](./Angry%20IP%20Scanner%20Numbered.png)

## **Step 2: Troubleshooting**
**If wpilibpi.local does not show up on Angry IP Scanner:**
1. Open SD card on computer (if you get a popup asking to format ignore. It's due to the limitations of Windows reading file system types. You will still be able to open and view the files in /boot via Windows Explorer).
2. Edit *wpa_supplicant_wpilibpi.conf*. Correct network name in the field ssid (in this example *My Home Network Name*), and password (in this example *NetworkPassword*) in field psk. The text should look like this:
    
```
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=US

###### BELOW THIS LINE EDITED BY RPICONFIGSERVER ######
network={
    ssid="My Home Network Name"
    psk="NetworkPassword"
}
```

3. Save, transfer to microSD card to the pi, restart
4. If still not working, check the batteries. Low voltage can be the problem.

## **Step 3: Test from VS Code**
1. Starting from the [Romi programming instructions](https://docs.wpilib.org/en/stable/docs/romi-robot/programming-romi.html)
2. In *build.gradle* file, update HALSIMWS_HOST from 10.0.0.2 to IP Address from Angry IP Scanner:

```
// Set the websocket remote host (the Romi IP address).
sim {
    envVar "HALSIMWS_HOST", "10.0.0.2" // <-- Change IP Address to that found in Angry IP Scanner
}
```

3. Or, if able to resolve [http://wpilibpi.local](http://wpilibpi.local), replace code for websocket to be:

```
def ROMI_IP 
try {
    ROMI_IP = java.net.InetAddress.getByName("wpilibpi.local").getHostAddress() // <-- You may need to change the name here to the hostname you see in Angry IP Scanner
} catch (UnknownHostException e) {
    ROMI_IP = "10.0.0.2"
}

// Set the websocket remote host (the Romi IP address).
sim {
  envVar "HALSIMWS_HOST", ROMI_IP
}
```
4. Leverage the simulator GUI to test out interactions with the robot
    1. Detailed instructions for the simulator GUI can be found [here](https://docs.wpilib.org/en/latest/docs/software/wpilib-tools/robot-simulation/simulation-gui.html)
    2. Build and run code with "WPILib Simulate Robot Code on Desktop" command palette option in VS Code. (see step "Running the GUI" in the link specified above)
    3. A simulator GUI should start up automatically (there will not be a pick extensions step for the Romi)
    4. Drag-n-drop your Joystick from "System Joystick" to Joysticks (port [0]) (see step "Adding a System Joystick to Joysticks" in link specified above)
    5. Switch the "Robot State" from "Disabled" to "Teleoperated"
    6. It's okay if it drives differently. Romireference was designed for the Logitech gamepad. If you are not using the same controller, the mapping of the buttons (found in *Constants.java*) will not match. This can be corrected in the workshop.

## **Step 4: Attend Workshop**
If you were able to coneect to the Romi you are in great shape. If you got Step 3 working such that you can actually interact with the robot, you are ahead of the game!
