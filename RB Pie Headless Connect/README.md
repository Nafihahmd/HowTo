# Running the Raspberry Pi headless from a Linux system
Headless means not using a monitor or keyboard to run Pi. In this project I am assuming that you already have a Raspberry pie OS bootable SD card or pendrive. We will be adding certain files to boot folder inorder to activate certain setup features on the first boot of the Pi itself.

## Setting up wireless networking
- create a file named `wpa_supplicant.conf` in the **boot** folder with the following content:
```
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=<Insert 2 letter ISO 3166-1 country code here>

network={
 ssid="<Name of your wireless LAN>"
 psk="<Password for your wireless LAN>"
}
```

## Remote Access 1 -SSH
**Method 1**. Used to access the command line of the Pi from another computer.
1. Get the IP address of your Pi.
2. Enable SSH
 Raspberry Pi OS has the SSH server disabled by default. SSH can be enabled by placing a file named `ssh`, without any extension, onto the boot partition of the SD card from another computer.
4. Set up your client
 - Open terminal and paste `ssh pi@<IP>`
 - If you see  security/authenticity warning type **yes** to continue.
 - Next you will be prompted for the password for the pi login: the default password on Raspberry Pi OS is `raspberry`.
5. X-forwarding allow the use of graphical applications if needed.
 For that use `ssh -Y pi@<IP>` command. Now you have the ability to open up graphical windows like scratch or geany typing `scratch &` or `geany &` respectively.

## Remote Access 2 -VNC
**Method 2**. Access full desktop environment.
