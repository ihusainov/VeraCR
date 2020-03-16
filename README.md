# VeraCR
Vera Crypt Decrypt System Disk

Recently, a problem has occurred. Vera crypt was installed on the boot disk. After the next windows update, loading became impossible. It was necessary to do something. Made up a small plan. First, it was necessary to decrypt the disk. Second - From the user profile folder, from the Documents folder, you had to copy VeraCrypt Rescue Disk.zip. Third - Create a bootable USB flash drive and decrypt the entire system drive for a normal windows 10 update.
Let's start:
I downloaded the Win PE distribution and downloaded the latest version of Veracrypt distribution from a second laptop. Instead of WinPE, you can use the "Hiren’s BootCD based on Windows 10 PE x64" distribution. Next, we take a flash drive with a minimum of 8GB and through the Rufus application, we write to the flash drive as a boot distribution. We simply copy it to the Veracrypt flash drive.

Boot from a flash drive. Run Veracrypt and choose only unpack. Next, go to the unpacked folder. We launch VeraCrypt-x64.exe - then Volume - Select Device - I had data on device 0 in section 4. \ Device \ Harddisk0 \ Partition4
Volume - Mount volume with options - I note Mount Partition using system encryption ... - Then I enter the password and the disk opens. From the disk, I copy the VeraCrypt Rescue Disk.zip file.


VeraCrypt Rescue Disk for MBR legacy boot mode on USB Stick

To create a bootable VeraCrypt Rescue USB drive 
Download the required files from the official SourceForge repository of VeraCrypt: https://sourceforge.net/projects/veracrypt/files/Contributions/VeraCryptUsbRescueDisk.zip
Insert a USB drive.
Format the USB drive with FAT32:
Launch usb_format.exe as an administrator (right click "Run as Administrator").
Select your USB drive in the Device list.
Choose FAT32 as filesystem and check "Quick Format". Click Start.
Create a bootloader which can start up an iso image:
Launch grubinst_gui.exe.
Check "Disk" and then select your USB drive in the list.
Click the "Refresh" button in front of "Part List" and then choose "Whole disk (MBR)".
Leave all other options unchanged and then click "Install".
You should see an console window that reads "The MBR/BS has been successfully installed. Press <ENTER> to continue ..."
Close the tool.
Copy the file "grldr" and "menu.lst" to your USB drive at the root (e.g. if the drive letter is I:, you should have I:\grldr). This file loads Grub4Dos.
Then unzip the VeraCrypt Rescue Disk.zip file and copy the Boot folder and VeraCrypt folder to the usb root of the drive
The list of files and folders on the usb drive should be:
Boot
Veracrypt
grldr
grubinst.exe
menu.lst

Next, boot from the usb drive and select in the menu that opens
d: Decrypt OS
Enter your password, wait for Decrypt? press y and wait for the decryption of the disk to complete.
