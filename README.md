# DeSmuME

DeSmuME is a Nintendo DS emulator. http://desmume.org

DeSmuME-Reloaded is a fork of DeSmuME by Jackobo Le Chocobo with added WiFi capability https://github.com/slawekwaga/DeSmuME-Reloaded

This branch was for testing WiFi related changes from DeSmuME-Reloaded project merged with the original DeSmuME project code, and updated to recent code base (22/06/2018).

After successful testing, the changes were merged to master branch https://github.com/retr0s4ge/desmume/tree/master which is rebased upon current DeSmuME project master branch https://github.com/TASVideos/desmume/tree/master

***

# Current build (master branch)

[![AppVeyor CI Build Status](https://ci.appveyor.com/api/projects/status/github/retr0s4ge/desmume?svg=true)](https://ci.appveyor.com/project/retr0s4ge/desmume)

Compiled Excutables:
https://ci.appveyor.com/project/retr0s4ge/desmume/build/artifacts

***

# Instructions for setting up WiFi and connecting to AltWFC:

1- Search for, download the firmware files below (md5sum must match) and place them in "firmware" subdirectory

Required Firmware Files:

|   Filename   |    Description          |              md5sum              |
|:------------:|:-----------------------:|:--------------------------------:|
| firmware.bin | NDS Firmware - Required | 145eaef5bd3037cbc247c213bb3da1b3 |
| bios7.bin    | ARM7 BIOS - Required    | df692a80a5b1bc90728bc3dfc76cd948 |
| bios9.bin    | ARM9 BIOS - Required    | a392174eb3e572fed6447e956bde4b25 |

2- Download Winpcap software from https://www.winpcap.org/install/default.htm and install it

3- Start desmume and open the Emulation Settings (Config>Emulation Settings), then
  
    1- Set the check boxes for the following:
      Use exernal BIOS images, Use external firmware image, Load User Settings from file
  
    2- Browse for and select the ARM9 BIOS image, ARM7 BIOS image, Firmware image then click OK

4- Open the WiFi Settings (Config>Wifi), then
 
    1- Under Wifi mode: Select the radio button for "Infrastructure"
    
    2- Under Infrastructure settings:
      Select the Ethernet adapter you are currently using for connecting to the internet then click OK.
      Note that settings for infrastructure mode will be grayed out if Winpcap is not installed correctly.

5- Setup connection to the AltWFC network by following the instructions below

This needs to be done ONCE per emulator!

WfcPatcher         https://github.com/AdmiralCurtiss/WfcPatcher/releases

AltWFC Server List https://github.com/polaris-/dwc_network_server_emulator/wiki/List-of-Servers

    5a- Download the most recent version of WfcPatcher
    
    5b- Drag and drop the ROM file(s) onto WfcPatcher.exe.
        Note: WfcPatcher works correctly with most ROMs, but some need special patching instructions
    
    5c- The output (patched) ROM file has (NoSSL) at the end of its filename. 
    
    5d- Open the patched ROM in desmume, then go to Nintendo WFC Settings (Inside the game)
    
    5e- Select Options, then Erase Nintendo WFC Configuration. The ROM will be closed.
    
    5f- Open the ROM again in desmume,  then go to Nintendo WFC Settings (Inside the game)
    
    5g- Select Nintendo Wi-Fi Connection Settings, then Connection 1, then Search for an Access Point
    
    5h- SoftAP access point should appear, select OK. A connection test will be performed but WILL FAIL.
    
    5i- Select Connection 1 again, and scroll down to the bottom of the settings list
    
    5j- Set Auto-obtain DNS to No
    
    5k- Set the primary and secondary DNS servers to 104.131.93.87 (default AltWFC)
        If you want, you can choose any server from the AltWFC server list linked above
    
    5l- Select Save Settings
    
    5m- Reset the ROM and start a new game or load your in-game save
    
    5n- start an activity requiring connection to WFC network
    
    5o- The game will tell you that card and console information don't match.
        It will ask you if new information should be generated, accept this.
    
    5p- After saving the new information, the game will attempt to connect to WFC network but WILL FAIL again.
        Don't try to connect again.
    
    5q- Make an in-game save and then Reset the ROM
    
    5r- Load the previous in-game save and start the activity requiring connection to WFC network
    
    5s- You should finally be able to connect successfully to AltWFC network !

Notes:

1- The resulting settings (including WFC ID) are saved in firmware.dfc file inside the Battery folder.

2- If you need to run multiple copies of an online game at the same time as 2 different players then make sure to follow the instructions above for 2 separate copies of the emulator, so that you get a 2 different firmware.dfc files (i.e different WFC ID for each copy)
