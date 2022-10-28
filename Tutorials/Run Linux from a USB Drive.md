![USB Linux](/Assets/Images/USBLinux.png)
# How to Run Linux from a USB Drive
___
This tutorial will show you how to run Linux from a USB drive. THis is typically done using a USB thumbdrive, as they are portable and do not require drivers to use as a boot device.

Running Linux from an external drive is not really a long term methodology, as it runs an operating system that essentially has situational amnesia. You are enot able to make system changes, install software, or do anything that reuires the operating system to write to a drive. Everytime you boot into it, it is the same as the time before, kind of like Bill Murray's reality in Groundhog Day. This is great for testing different flavors of Linux to make an informed choice of a dsitribution, but not so good if you want to continue to use Linux as a functioning operating system.

Here's how to do this. It is actually very simple.

___

## Pick and Download a Linux Distribution

The example distribution for this tutorial is Ubuntu 20.04.3 LTS. LTS means 'Long Term Support', which basically means that, throughout the lifetime of this particular version of the Linux distro, the company is commited to releasing upgrades, security patches, and generally supporting the OS.

Ubuntu is the most commonly downloaded Linux distro. It also has the most similar interface to Windows. It is a mature flavor of Linux, and Cannonical offers users a lot of support and resources. Download [Ubuntu 20.04.3 LTS](https://ubuntu.com/download/desktop/thank-you?version=22.04.1&architecture=amd64).

Or, download another distro of your choice. Here are two other Linux distributions that might be of interest:
 
1. [Linux Mint](https://linuxmint.com/download.php) is a popular choice, which comes in three different flavors. It's right behind Ubuntu amongst newcomers to Linux. Its major difference is that it is more customizable than Ubuntu. If you choose this option, here is a [guide](https://www.linuxfordevices.com/tutorials/linux/install-linux-mint-on-virtualbox) to installing it in Virtual Box.
2. [Elementary OS](https://elementary.io/) is to MacOS as Ubuntu is to Windows. If you are coming to Linux with a WIndows PC but a fondness for MacOS, this is your choice. The only drawback is you must make a donation, but that can be as small as $10. Here is a [guide](https://linuxhint.com/install_elementary_os_virtualbox/) to installing it in VirtualBox.

Which ever flavor you pick, you will need to download the .iso file to your PC.

___

## Create a Bootable USB Drive with the Linux Files Installed

You will need to have a USB Thumb drive with enough space to hold the Linux distribution source files for the distro you've chosen. Once you have this, follow the distro's instructions for preparing the source files to be installed. THis will usually involve using a piece of software specifically designed to do this, such as [Rufus](https://rufus.ie/en/) or [Etcher](https://etcher.download/). Your distro may suggest software as well; follow their suggestion. When finished, you should end up with a bootable install source on your thumbdrive.

___

## Enable Windows to Boot From an External Drive

### **Determine Your Firmware Type**

Newer machines have UEFI type firmware, older machines have the older legacy BIOS type firmware. You can easily determine which one you have by running System Information:  
1. Click on the Windows Start icon.
2. Type **System Information**. This will open a search window.
3. Click on **System Information**
4. Scroll down the list until you find '**BIOS Mode**'

**If you have legacy BIOS firmware**: The only change you need to make is to enable your system to boot from an external drive. There are two ways to do this.
1. Some machines allow you to select a boot menu during startup. Depending on your manufacturer, this is usually accomplished by hitting the F10 or F12 key during boot. To ensure that your machine recognizes the input, you may need to hit the key repetitively during the boot process.  Insert the USB drive into a port. Boot the machine. Hit the appropriate function key. If you are succesful, you'll be presented with a menu offering you boot drive choices. In some cases your USB drive will be listed by name; in other cases, you'll see something like '**External Drive**', '**BootableDrives**', etc. Select the right choice, and the system will boot from your Linux drive. 
2. You can also change your BIOS settings to always search for an external drive to boot from. If you do not have a USB in a port, Windows proceeds as normal. If you do, it will try to boot from it everytime it starts. To make this change, enter your BIOS and look for where boot order is set. Change this so that the first thing the system looks for is a bootable USB drive. Exit BIOS, insert your bootable Linux drive, and your PC will boot into Linux. 

**If you have UEFI firmware**: You have to make two other adjustments to your settings before doing the above. Windows dislikes sharing the limelight with another operating system, and a few windows settings will interfere with Linux booting or flat out block it from booting. Let's fix that.

1. **Disable Fast Startup**

Windows has always had a reputation for taking forever to start itself, and this was a Microsoft workaround. By default it is on; let's turn it off.

1. Open '**Control Panel**'.
2. Select '**Power Options**'.
3. Select '**Choose what the power buttons do**'.
4. Unselect '**Turn On Fast Startup**'.
5. Exit '**Control Panel**'

2. **Disable Secure Boot**

Unfortunately, one of UEFI's best features... secure boot... blocks the ability to boot into Linux, so we have to disable it. This is done from the UEFI settings, which means you will have to restart your machine. Instructions for disabling Secure Boot are [here](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/disabling-secure-boot?view=windows-11). 

Now, follow steps one and two above to tell your system to boot from a USB drive.

___

## Choose the 'Try' Option

Most Linux distros that can be run from a bootable USB drive will give you a startup option: '**Try Ubuntu**' or '**Install Ubuntu**', for instance. Select the try option, or Linux will begin to make changes to your system.

___

## Congratulations!

That's all that's involved. You can now check out whichever Linux flavor you have selected. Enjoy!
