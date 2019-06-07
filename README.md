# Good to know before getting started.

Below is the best quide I have seen on triple booting a mac with Mac OS, Windows and Ubuntu:

[Tripple boot Mac ](https://www.innoq.com/en/blog/triple-booting-a-mac/)

Working on the mac keyboard with ubuntu is hard, if you have not set up the correct keyboard layout.
Follow the quide below to set up for the norwegian keyboard layout.

`sudo dpkg-reconfigure keyboard-configuration`

Keyboard model -> MacBook/MacBook Pro

Country of origin for the keyboard -> Norwegian

Keyboard layout -> Norwegian

Key to function as AltGr: Right Alt (AltGr)

Compose key -> No compose key

Use Control+Alt+Backspace to terminate the X server? -> Yes or No, your choice. I chose No.

### Test your keys:

Right alt + 7 for pipe: |

Right alt + 8 for open square bracket: [

Right alt + Shift + 8 for open curly bracket: {

### Apple Magic Trackpad 2 config
I installed the driver from https://github.com/robotrovsky/Linux-Magic-Trackpad-2-Driver, which comes packaged with Ubuntu 19.04 -> but that version used libinput as the driver and I was not sure on how to change the driver to synclient. I will update this README once I figure out how to make synclient the trackpad driver on live cd of ubuntu 19. The steps below asume synclient is installed and made default driver for Apple Magic Trackpad.

`git clone https://github.com/robotrovsky/Linux-Magic-Trackpad-2-Driver`

  `cd Linux-Magic-Trackpad-2-Driver/scripts`
  
  `sudo chmod u+x install.sh`
  
  `./install.sh`

After making sure the install was ok, then continue with:

This is to find your device id:

`xinput list | grep "Trackpad"`

This is to make the trackpad responsive:

`xinput set-prop <id> "Synaptics Finger" 0, 0, 0`

`xinput set-prop 12 "Synaptics Move Speed" 3.0, 3.0, 7.0, 0`

Furhther automations for system wide config persistence:

`sudo nano /usr/share/X11/xorg.conf.d/30-synaptics.conf`

`Section "InputClass"

        Identifier "Disable clickpad buttons on Apple touchpads"
        
        MatchProduct "Apple|bcm5974"
        
        MatchDriver "synaptics"
        
        Option "SoftButtonAreas" "0 0 0 0 0 0 0 0"
        
        Option "FingerLow" "0"
        
        Option "FingerHigh" "0"
        
        Option "FingerPress" "0"
        
        Option "MinSpeed" "0"
        
        Option "MaxSpeed" "0"
        
        Option "AccelFactor" "0"
        
        Option "TrackstickSpeed" "0"
        
        Option "VertScrollDelta" "-80"
        
        Option "HorizScrollDelta" "-80"
        
EndSection`


`sudo /usr/share/X11/xorg.conf.d/30-synaptics.conf /etc/X11/xorg.conf.d/30-synaptics.conf`



# VM

For the VM, I chose Ubuntu Server 18.04. It was nice to be able to setup docker in the installation phase.
To add the virtual box image to git, I had to use git Large File System (git-lfs)

`sudo apt-get instal git-lfs`

[Download VM](https://github.com/parkerlarry/learning_linux/raw/master/VM/VM-ubuntu-18.ova)

# Backups

always nice to create a backup of a directory and ssh to remove storage

`tar vcfz - my_directory | ssh username@remotehost "cat > my_directory.tar.gz"

# misc
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi
