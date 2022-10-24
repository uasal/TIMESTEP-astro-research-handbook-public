![Linux in Windows](/Assets/Images/WindowPenguin.png)
___
# Installing Linux in a Windows Virtual Machine  
 
 This tutorial will enable you to install Linux to your Windows PC using virtual machine software. A virtual Machine is a form of system software that runs in an operating system and imitates the hardware and software of an another computer. This allows you to run another operating system within your native operating system.

 While there are several virtual machine software options, Oracle's VM [VirtualBox](https://www.virtualbox.org/) is easy to install and configure, has a host of configuration settings, works very well with Linux, and is free. This tutorial will use VirtualBox as its VM software and Ubuntu as the installed Linux distribution. Ubuntu is considered to have the most Windows-like interface and is probably the easiest for Windows users to learn. If you choose a different VM software or Linux distribution, the process is similar, and I have included references to a few other distros, along with their VM installation procedures.
 ___
 ## Windows PC Requirements  

 Because virtual machines are software that run in Windows, and Windows is a resource hungry operating system, Linux itself must run on whatever resources Windows is not using. Too little memory, or too little processor power will cause Linux to respond slowly or not at all. This creates a set of minimum requirements your PC must meet and hopefully exceed.

 ### **CPU Requirements**
 The first and most important requirement is that your processor supports **virtualization**. Virtualization is a process by which one processor can act as if it were several distinct processors. This is what enables Linux to think it has its own hardware... it sees the processor and other hardware as if it is the only OS installed.  

 An easy way to confirm if your processor supports virtualization is to see if it is already turned on in your BIOS. Most newer PCs support virtualization and come with virtualization turned on as default. Here's how to check:  
 
1. Hit **Ctrl** + **Shift** + **Esc** to bring up Task Manager.
2. Click on the **Performance** tab.
3. Look for **Virtualization** in the list under the graph. This should be followed by **Enabled**. If it is not, you will have to enable it before proceeding. Leave this tab open for the next check.

Generic instructions for enabling Virtualization in your machine's BIOS can be found here: [Enabling Virtualization in Your PC's BIOS](https://bce.berkeley.edu/enabling-virtualization-in-your-pc-bios.html).  

If it turns out that your PC does not support Virtualization, you will not be able to use this method for installing Linux to your PC.

The next requirement is that your processor has a minimum of **four cores**. If your machine is recent, it most likely does, and the more the merrier. If you still have the Task Manager performance tab open, the number of cores present is listed in the same area as your virtualization status. Otherwise, reopen it and check, and then leave Task Manager open for the next check.  
### **System RAM** 
The absolute minimum available RAM required is 4 GB. A better amount is 8 GB or more. Note that the requirement is minimum available... this means available *while windows is running*, not what is physically installed in your machine. To check this, click on the **Memory** tab in Task Manager, and look under the word **Available**. The best way to check your baseline available RAM is to close all other applications first, and then check this.  
### **Drive Space**  
You need to have at least 20 GB of available drive space, and this is the bare minimum. 50 GB is desirable. Remember, just like in Windows, drive space is required not only for software installs and saving your own work, but is also used by the operating system for swap files and other OS necessities. You will now be supporting two operatings systems; both will need ample disk space.  

___
If you meet these requirements, you are ready to proceed. If not, your choices are:
1. Access the University Linux Server
2. Install Linux Using WSL (although you will lack GUI app functionality)
3. Dual Boot Windows and Linux
___
## First Step: Download your Linux Distribution
The example distribution for this tutorial is Ubuntu 20.04.3 LTS. LTS means 'Long Term Support', which basically means that, throughout the lifetime of this particular version of the Linux distro, the company is commited to releasing upgrades, security patches, and generally supporting the OS.

Ubuntu is the most commonly downloaded Linux distro. It also has the most similar interface to Windows. It is a mature flavor of Linux, and Cannonical offers users a lot of support and resources. Download [Ubuntu 20.04.3 LTS](https://ubuntu.com/download/desktop/thank-you?version=22.04.1&architecture=amd64).

Or, download another distro of your choice. Here are two other Linux distributions that might be of interest:
 
1. [Linux Mint](https://linuxmint.com/download.php) is a popular choice, which comes in three different flavors. It's right behind Ubuntu amongst newcomers to Linux. Its major difference is that it is more customizable than Ubuntu. If you choose this option, here is a [guide](https://www.linuxfordevices.com/tutorials/linux/install-linux-mint-on-virtualbox) to installing it in Virtual Box.
2. [Elementary OS](https://elementary.io/) is to MacOS as Ubuntu is to Windows. If you are coming to Linux with a WIndows PC but a fondness for MacOS, this is your choice. The only drawback is you must make a donation, but that can be as small as $10. Here is a [guide](https://linuxhint.com/install_elementary_os_virtualbox/) to installing it in VirtualBox.  

Whichever distro you choose, you will need it saved to your hard drive as a .iso image file.
___ 
## Second Step: Install and Configure VirtualBox
First, download [VirtualBox for Windows](https://download.virtualbox.org/virtualbox/7.0.2/VirtualBox-7.0.2-154219-Win.exe). Documentation for VirtualBox can be found on the [VB Website](https://docs.oracle.com/en/virtualization/virtualbox/7.0/user/index.html). Run the installer and let it do its thing. After it completes, run the program. You'll be greated by a welcome window.  
### **Create a New Virtual Machine**
CLick on the "New" icon. This will bring up an initial configuration window:  

![VM Configuration Window](/Assets/Images/NewVMWindow.png)  

The settings should be as follows:  
1. Name your operating system. I use 'UbuntuLTS'. You can call it anything, but preferably involve the name of the distro. 
2. The 'Machine Folder' is where your VM is stored. Putting it under your user directory makes sense. (Your user directory is located in `C:\Users`.) You can name this directory anything you want... `VirtualBoxVMs` is a decent choice.
3. In the dropdown list under 'Type', select 'Linux'. This tells the VM how to initially configure itself.
4. In the dropdown list, pick 'Ubuntu (64)'. (It's highly likely you are running a 64 bit operating system. If not, adjust appropriately.)
5. Click '**Next**'. 
### **Set Memory Allocation**
The next window, '**Memory Size**, allows you to pick the amount of memory that you want to allocate for your VM to use when it is running. Note that allocating to the VM locks that memory down for the VM and is therefore unavailable for Windows to use, *while the VM is running*. This selection does not affect Windows if the VM is not running.

The slider allows you to pick the amount of memory. The recommended amount is usually ridiculously small. Move the slider to the right but stay in the green area. I suggest using at least 6 GB, but no more than a quarter of what's available. Click '**Next**' to continue.  
### **Create a Virtual Hard Disk**
This is a series of windows that are used to create a virtual hard disk. This is what your VM uses to simulate an actual hard disk. Here are suggested values for each configuration window:
  
  1. **Hard Disk**: Select 'Create a Virtual Hard Disk Now'
  2. **Hard Disk File Type**: Select 'VDI (VirtualBox Disk Image)'
  3. **Storage on Physical Hard Drive**: Select 'Dynamically Allocated'. This is concerns how the VM utilizes actual space on your machine's hard drive. Choosing dynamical allocations allows the VM to expand and contract the amount of your hard drive it uses as needed.
  4. **File Location and Size**: If you chose dynamical allocation in the previous step, this sets the maximum amount the VM can use of your disk drive. THis will depend on how big your hard drive is and how much free space you have left on it. I suggest using a minimum of 10 GB. It also lets you set the directory location of your virtual disk. This needs to be under the directory you created earlier. The routine should fill this is for you, but if not, here is an example of a VD location directory:

  ![Virtual Drive Configuration](/Assets/Images/VMConfig01.png)  

  Now, hit '**Create**' and your new VM will be initiallized. You should see a window that looks like this:  

  ![Initialized VM](/Assets/Images/InitializedVM.png)  

  This ends the configuration of the Virtual Machine. TIme to load your distro!  
  ___

  ## Third Step: Install Your Distro

  At the top of the initialization window, click on '**Start**'. This will launch the installer for your distribution image. Use the file icon next to the location box to navigate to wherever you stored your distro .iso file. Click '**Start**'. In the next window, click on your distro name and then sclick on '**Choose**'.

  The Ubuntu installer should now pop open a window which gives you a choice between '**Try Ubuntu**' and '**Install Ubuntu**'. Select the **Install** option.

  As Ubuntu installs, there will be a few installation options you may be asked, depending on your particular machine and Windows configuration. A good resource for answering these questions can be found in the discussion on the [Ubuntu Installation Flow](https://ubuntu.com/tutorials/install-ubuntu-desktop#5-installation-setup). After this is finsihed, there is only one more thing to do.
  ___  
  ## Fourth Step: Change your Window Resolution  

  You may have noticed that your Linux display window is set at 800 x 600. If you right click on the icon at the right bottom of the window that looks like a little monitor, there are many resolution options but they are all greyed out. Let's fix that. (By the way, all those little icons are for various configurations and adjustments to your virtual machine. Hovering your pointer over one will tell you what it does.)

 -  **Shut Down Ubuntu**  
  CLose the Ubuntu window, and select '**Power Off the Machine**'.  
  - **Go to Display Settings**  
    In the main VM window, click '**Settings**' at the top, and then go to the '**Display**' tab.
- **Change the Display Controller**  
Under '**Graphics Controller**', select '**VBoxSVGA**'. Ignore the warning.
  
Now, restart your virtual machine. You should be able to resize the window either by use of the display icon, or by resizing the window with your mouse.
___
## Congratulations!
You should now have a functioning virtual machine implementation of Linux.
