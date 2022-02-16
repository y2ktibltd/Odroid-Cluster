Micro SD Card Creation
Replace sdX in the following instructions with the device name for the SD card as it appears on your computer.

Zero the beginning of the SD card:
dd if=/dev/zero of=/dev/sdX bs=1M count=8
Start fdisk to partition the SD card:
fdisk /dev/sdX
At the fdisk prompt, create the new partition:
Type o. This will clear out any partitions on the drive.
Type p to list partitions. There should be no partitions left.
Type n, then p for primary, 1 for the first partition on the drive, 4096 for the first sector, and then press ENTER to accept the default last sector.
Write the partition table and exit by typing w.
Create the ext4 filesystem:
mkfs.ext4 /dev/sdX1
Mount the filesystem:
mkdir root
mount /dev/sdX1 root
Download and extract the root filesystem (as root, not via sudo):
wget http://os.archlinuxarm.org/os/ArchLinuxARM-odroid-xu3-latest.tar.gz
bsdtar -xpf ArchLinuxARM-odroid-xu3-latest.tar.gz -C root
Flash the bootloader files:
cd root/boot
sh sd_fusing.sh /dev/sdX
cd ../..
Unmount the partition:
umount root
Set the boot switch on the ODROID-XU4 board next to the HDMI jack to the uSD position.
Insert the micro SD card into the XU4, connect ethernet, and apply 5V power.
Use the serial console (with a null-modem adapter if needed) or SSH to the IP address given to the board by your router.
Login as the default user alarm with the password alarm.
The default root password is root.
Initialize the pacman keyring and populate the Arch Linux ARM package signing keys:
pacman-key --init
pacman-key --populate archlinuxarm


# Odroid-Cluster

dont forget to generate ssh keys and upload them to your cluster nodes before you start using dsh or ansible ascripts.
