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

Test your keys:

Right alt + 7 for pipe: |

Right alt + 8 for open square bracket: [

Right alt + Shift + 8 for open curly bracket: {

# VM

For the VM, I chose Ubuntu Server 18.04. It was nice to be able to setup docker in the installation phase.
To add the virtual box image to git, I had to use git Large File System (git-lfs)

`sudo apt-get instal git-lfs`

[Download VM](https://github.com/parkerlarry/learning_linux/raw/master/VM/VM-ubuntu-18.ova)
