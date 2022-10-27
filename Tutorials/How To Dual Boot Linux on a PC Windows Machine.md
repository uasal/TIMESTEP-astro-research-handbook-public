![PC Dual Boot](/Assets/Images/Windows&Linux.png)
___
# How to Dual Boot a Windows PC with Linux  
This tutorial will help you set up your PC to dual boot Windows and Linux. Dual booting gives you the best of both worlds... a full Windows installation AND a full Linux installation. THis is the closest you can get to experiencing native Linux without disrupting your pre-existing Windows configuration. 

With a dual boot configuration, you have the choice each time you boot your machine as to whether you want to run Windows or Linux. To be clear, the two cannot be run side-by-side as with installing Linux in a virtual machine. On the other hand, both operating systems have full use of your machine's resources. Windows won't be denying Linux your memory and processor power, and Linux gets to take full control of your hardware, which it excels at.    
___
## **Preliminary Considerations**

Before we get started, a few important things:  

### PC Requirements

Because you are going to be installing Linux as a dual booted stand-alone OS, this is really dependent on the Linux distribution you are choosing. The considerations are the same as if you were installing it as the only OS on your machine. 

Wheras most current Linux distributions are fairly complete in their hardware support, it pays to research the distribution you want to install and check out its hardware specifications. Because the setup of dual-boot systems involves some risk to your pre-existing system, it pays to make sure of this first. Last thing you want to do is set up dual boot and then try to install a Linux distro that dowsn't support a key piece of your hardware.  

### Current System Considerations  

The next thing to confirm is that your system has enough hard drive space to support a second operating system. Since Windows most likely will be your primary operating system, you won't need to dedicate a huge amount of drive space to Linux, but a good minimum amount is probably around 25 GB.

When making this determination, first check your drive properties. In file manager, got to 'THis PC'. You'll see your drive, or drives, listed by name, followed by the drive letter. Most laptops will only have a C drive. RIght click on your drive, and select '**Properties**'. You'll see your drive capacity, used space and free space remaining. 

Remember, you not only need enough space to install Linux, but also enough space to continue using Windows. If you can convince yourself that you have enough space for both, you are good to poroceed. But first, you should know some of the issues involved with dual booting.

### Pitfalls to Dual Booting

Most of the time, dual boot systems can be created without much risk, and generally the procedure goes well. But occasionally things can go wrong, primarily because the Windows boot system is finicky, and, in the world of operating systems, a bit clunky. 

As in any major change to your machine, you should backup everything before you attempt this. Unlike with most changes to your machne, there is a small chance that you can wipe out your entire Windows installation with this process. If you do a complete backup first, you can recover your system. SO please, if you want to go this route, backup first.

For a very good discussion on the perils of dual booting, [read this](https://www.makeuseof.com/tag/risks-dual-booting-windows-linux-operating-systems/).

___

## **Getting Started**
If you've made it to this point, you have not been disuaded by the possible issues. I encourage you to proceed cautiously.

### **Backup Your Machine**

Intentional repetition: I can't emphasize enough... backup your machine!

### **Read Up on the Windows Boot Process**

When making this kind of change, it helps to understand what's happening, especially when dealing with the system responsible for the fundametal process of loading your operating system. Here is a good summary of the process: [Windows Boot Process Step By Step](https://automateinfra.com/2021/11/09/windows-boot-process-step-by-step/). 

### **Choose your Linux Distribution**
There are many available. A good starting point for Windows users is Ubuntu. 

Ubuntu is the most commonly downloaded Linux distro. It also has the most similar interface to Windows. It is a mature flavor of Linux, and Cannonical offers users a lot of support and resources. Download [Ubuntu 20.04.3 LTS](https://ubuntu.com/download/desktop/thank-you?version=22.04.1&architecture=amd64).

Or, download another distro of your choice. Here are two other Linux distributions that might be of interest:
 
1. [Linux Mint](https://linuxmint.com/download.php) is a popular choice, which comes in three different flavors. It's right behind Ubuntu amongst newcomers to Linux. Its major difference is that it is more customizable than Ubuntu. 

2. [Elementary OS](https://elementary.io/) is to MacOS as Ubuntu is to Windows. If you are coming to Linux with a WIndows PC but a fondness for MacOS, this is your choice. The only drawback is you must make a donation, but that can be as small as $10.   

### **Prepare a Linux Install USB Thumb Drive**
You will need to have a USB Thumb drive with enough space to hold the Linux distribution source files for the distro you've chosen. Once you have this, follow the distro's instructions for preparing the source files to be installed. THis will usually involve using a piece of software specifically designed to do this, such as [Rufus](https://rufus.ie/en/) or [Etcher](https://etcher.download/). Your distro may suggest software as well; follow their suggestion. When finished, you should end up with a bootable install source on your thumbdrive.

### **Prepare a Bootable Windows Install USB Thumbdrive**

Although not required, you will really appreciate taking this extra step if something goes wrong. It may be the only way to recover your system if something goes catastrophically wrong during the install process. (If you don't have one of these on hand, you should. Now would be a great time to add one of these essential tools to your arsenal.) Tom's HArdware has a great tutorial for doing this [here](https://www.tomshardware.com/how-to/windows-10-usb-install-drive).

### **Determine Your Firmware Type**

Newer machines have UEFI type firmware, older machines have the older legacy BIOS type firmware. You can easily determine which one you have by running System Information:  
1. Click on the Windows Start icon.
2. Type **System Information**. This will open a search window.
3. Click on **System Information**
4. Scroll down the list until you find '**BIOS Mode**'

**If you have a legacy BIOS, you need to follow a different install routine.** Since most PCs purchased in the last 5-7 years have UEFI type, this tutorial focuses on installing to UEFI firmware. The procedure for installing to legacy BIOS sytems is [here](https://itsfoss.com/install-ubuntu-dual-boot-mode-windows/).

If you are in the UEFI camp, lets proceed.

___

## Partition Your Drive

Linux and Windows may be friends, but they can't tolerate living together. Our first step is to divide your drive into two sections; one for Windows, and one for Linux.

### **Determine Your Available Space**

Most pre-installed Windows systems have one partition which is, essentially, the entirity of the hard drive, and is dedicated entirely to Windows. You can verify this by using WIndows File Manager, and finding '**This PC**' in the left pane. Expand it, and you will most likely see one drive listed, by its name, followed by its drive letter in parenthesis.

Should you be using a multidrive system, you can also use another of your drives; the procedure is the same. However, if one of your drives is an Solid State Drive (SSD), this is the preferred installation drive as SSDs are fast in comparison to traditional hard drives.

Right click on the drive, then click on '**Properties**'. This will bring up a window which will tell you the drive's total capacity, its used space, and its free space. Note the free space, and decide how much of this you are willing to remove from Windows and give to Linux. Most modern hard drives are fairly large. A good comfortable amount of space for a Linux system is around 50 GB; since this will be mostly a Linux system installed for learning purposes, that should easily be enough for the OS, your software, and your files. You can go as low as 25 GB, but whatever you do, don't starve your windows installation of space.

### **Start Disk Management**

1. **Run an elevated command prompt** by clicking on the taskbar search icon. Type **Command**. In the right side panel, click on **Run as Administrator**.
2. **Run Disk Managemen** by entering `diskmgmt.msc` at the command prompt.

The Disk Management window is divided into two parts... the upper part is a text listing of your partitions; the bottom is a graphical listing of your partitions. They show the same info in different ways.

### **Find Your Drive**

First thing you will notice is that, even though your machine has one drive (in most cases), there are most likely multiple entries in the disk management window. That's because Windows creates multiple invisible partitions for its own nefarious purposes. Ignore them. What you are looking for is the one labelled like it is in '**My PC**'... drive name followed by drive letter in parenthesis. In a one drive system, it is the only entry in the list that ISN'T expressed like (Disk 0, partition 1).

### **Shrink Your Drive**

Right click on your C Drive (either above or below works) and then click on '**Shrink Volume**'. After it queries your drive controller, you'll get a window that looks similar to this:  

![Shrink Drive Volume](/Assets/Images/ShrinkVolume.png).

In the box that reads '**Enter the amount of space to shrink in MBs**', enter the amount of space you've decided to allocate to Linux. Remember, this is in megabytes, so multiple how many GBs you want multiplied by 1000. Click '**Shrink**'.

After the process runs, Disk Manager will ask if you want to format the new partition. For now, leave it as free space, and we'll let Linux format it. Before closing the manager, check the drive listing to make sure everything went okay. You should see a new partition listed, of the size you requested.

## Make a Few Windows Configurations Changes

Windows dislikes sharing the limelight with another operating system, and a few windows settings will interfere with Linux booting or flat out block it from booting. Let's fix that.

### **Disable Fast Startup**

Windows has always had a reputation for taking forever to start itself, and this was a Microsoft workaround. By default it is on; let's turn it off.

1. Open '**Control Panel**'.
2. Select '**Power Options**'.
3. Select '**Choose what the power buttons do**'.
4. Unselect '**Turn On Fast Startup**'.
5. Exit '**Control Panel**'

### **Disable Secure Boot**

Unfortunately, one of UEFI's best features... secure boot... blocks the ability to boot into Linux, so we have to disable it. This is done from the UEFI settings, which means you will have to restart your machine. Instructions for disabling Secure Boot are [here](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/disabling-secure-boot?view=windows-11). 

Before you exit your UEFI setup...

### **Enable Boot From USB**

There are essentially two ways to do this. 

1. While you are in UEFI configuration, find the settings for boot order. You need to tell your firmware to start from your USB thumbdrive... this is usually listed as  somehting like **Boot From Removable Media** or **Boot From USB**. Remember to set this back to the way it was after you are done with the install process.

2. Some machines will bring up a boot menu if you hit the **F10** or **F12** function key while starting your machine. This works just as well, and removes the necessity of remember to change the UEFI setting back.

Either way, turn your machine off. Insert the USB Thumbdrive. Turn the power on. Depending on what you did in the proceeding step, either let the machine boot itself from the USB drive, or hit the function key and select the appropriate option.
___
## Finally: Install Linux!
