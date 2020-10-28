# Installing operating system images on Linux using dd

**Note**: use of the dd tool can overwrite any partition of your machine. If you specify the wrong device in the instructions below, you could delete your primary Linux partition. Please be careful.

## Finding SD card/ USB drive name
- Open Terminal (you can press `ctrl + alt + t` for that)
- Run `lsblk -p` to see which devices are currently connected to your machine.
- After connecting SD card/USB drive run `lsblk -p` again. Remember the new device name.
- Now that you've noted what the device name is, you need to unmount partitions on it so that files can't be read or written to the SD card while you are copying over the SD image. So run the command below, replacing "/dev/sdd1" with whatever your SD card's device name is (including the partition number)
```
umount /dev/sdd1
```

## Copying the image to the SD card

- In a terminal window, write the image to the card with the command below, making sure you replace the input file if= argument with the path to your .img file, and the /dev/sdX in the output file of= argument with the correct device name. 
```
unzip -p 2020-08-20-raspios-buster-armhf.zip | sudo dd of=/dev/sdX bs=4M status=progress conv=fsync
```

- The first part of the code unzips the .img file.
- `status=` is for showing realtime progress.
