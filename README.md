# VeraCR
VeraCrypt Decrypt System Disk

Recently, a problem has occurred. VeraСrypt was installed on the boot disk. After the next windows 10 update, loading became impossible. It was necessary to do something. 
  Made up a small plan:
    First, Boot from WinPE to decrypt the Partition. 
    Second - From the user profile folder, from the Documents folder, you had to copy "VeraCrypt Rescue Disk.zip". 
    Third - Create a bootable USB flash drive and decrypt the entire system drive for a normal windows 10 update.

Let's start:
I downloaded the WinPE iso and downloaded the latest version of VeraCrypt distribution from a second laptop. Instead of WinPE, you can use the "Hiren’s BootCD based on Windows 10 PE x64" distribution. Next, we take a flash drive with a minimum of 8GB and through the "Rufus" application, we write to the flash drive as a boot distribution. Then we simply copy the "VeraCrypt Setup 1.22.exe" to flash drive with WinPE.

Boot from a flash drive with WinPE. Run "VeraCrypt Setup 1.22.exe" and choose extract to folder. Next, go to the Extracted folder. We launch VeraCrypt-x64.exe - then Volume - Select Device - I had data on device 0 in partition 4 "\Device\Harddisk0\Partition4" - 
Volume - Mount volume with options - I note Mount Partition using system encryption ... - Then I enter the password and the partition opens. From the partition, I copy the "VeraCrypt Rescue Disk.zip" file from  user profile folder, the Documents folder.

Next we need create VeraCrypt Rescue USB Disk

VeraCrypt Rescue Disk for MBR legacy boot mode on USB Stick

To create a bootable VeraCrypt Rescue USB drive 
Download the required files from the official SourceForge repository of VeraCrypt: https://sourceforge.net/projects/veracrypt/files/Contributions/VeraCryptUsbRescueDisk.zip
Insert a Second USB drive.
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
Then unzip the "VeraCrypt Rescue Disk.zip" file and copy the "Boot" folder and "VeraCrypt" folder to the usb root of the drive
The list of files and folders on the usb drive should be:
EFI
grldr
grubinst.exe
menu.lst

Next, boot from the usb drive and select in the menu that opens
d: Decrypt OS
Enter your password, wait for Decrypt? press "y" then "Enter" and wait for the decryption of the disk to complete.



I find the best VeraCrypt Project install Windows 10 updates
https://github.com/th-wilde/veracrypt-w10-patcher
