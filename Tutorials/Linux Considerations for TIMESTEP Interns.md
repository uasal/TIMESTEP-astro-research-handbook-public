![LinuxOS Logo](/Assets/Images/LinuxOS.jpg)  

*"linux-logo" by laboratoriolinux is licensed under CC BY-NC-SA 2.0.*

---

## Options for Using the Linux OS on a Windows-based PC

One of the most important skills you should develop as early as possibe as a science intern / future scientist is familiarity with the Linux Operating System. Linux is the standard operating system in the physical sciences, for a number of very good reasons: it excels at high performance computing; it utilizes system resources better than GUI-based operating systems; there is far more open-source software written for it than windows; and its emphasis on the command line makes it more appropriate for the (non-GUI based) software most scientists write themselves.

This discussion is written for interns whose principle computng platform is MS Windows. Those who use Apple PCs have it somewhat easier, as Apple operating systems are built on UNIX. If this is your platform, see 'Linux Considerations for TIMESTEP interns with Apple PCs".

The first decision you must make, then, is how to access Linux, both for purposes of learning the OS in general, and specifically for your TIMESTEP work in learning the Linux command line. There are five relevant ways to do this. One of these involves accessing the university Linux server via a terminal and does not involve altering your personal computer, but only gives you remote access to a command line and therefore less overall usability. The second involves running linux from a thumbdrive. This also requires no changes to your Windows system, but has the disadvantage of resetting itself completely every time you decide to run Linux. The other three involve some form of installing a Linux system to your PC, two of which are minorly disruptive to your pre-existing Windows installation, and one of which involves making a fairly substantial change to your system. Which one you choose is up to how much overall Linux functionality you desire.

### Option One: Access the University Linux Server

Dr. Paschalitis, who will be instructing you in Linux, has an excellent tutorial entitled **Introduction to the LINUX operating system**, available **here**. The first section contains instructions on accessing the university's Linux server through SSH. It's pretty straightforward, creates a home directory for you, and gives you complete Linux command line functionality. Depending on how much immersion into Linux you want, this may be enough. 

- #### **Pros**
- Easy to use; only requires having an SSH client.
- No alteration to your computer required.
- Meets the minimum requirement of having access to a Linux command line.  
- #### **Cons**
- Only gives you access to command line Linux; no graphical user interface.
- Limited graphic support, ie plot output from Gnuplot, etc.
- Your file structure exists on a shared server.

### Option Two: Run Linux From a USB Thumbdrive

This option allows you to run Linux on your machine without making any changes to your pre-existing Windows install. In essence, you create a full bootable Linux system on an external drive (typically a USB thumbdrive), and instruct your machine to boot from that drive. You neatly bypass Windows, and Linux runs from the external drive.

This option is usually used to test out versions of Linux to make an informed decision about what distro you want to install. It is not really a viable long term option, for one important reason... you can't save changes to the system, install software, or use functionality that requires the OS to write to a drive. It essentially has permanent amnesia... as soon as you shut down the system, it forgets it was ever there to begin with.

While there are some workarounds to this, not all Linux systems allow them. If you want to experience different Linux systems before making a decision, this is a great option. If you want to have a funtioning, usable system on your PC, this is the least preferable option.  

- #### **Pros**
- Easy to use once the USB drive is created.
- No alteration to your computer required.
- Meets the minimal requirement of having access to a Linux command line.
- Allows you to experience multiple flavors of Linux
- #### **Cons**
- Not a durable Linux system. Resets itself each time it is booted.
- Cannot modify the operating system
- Cannot install software

Instructions for running Linux from a bootable USB drive are in the [Run Linux From a USB Drive Tutorial](/Tutorials/Run%20Linux%20from%20a%20USB%20Drive.md).  

### Option Three: Install Linux using Windows WSL

This option takes advantage of a relatively new functionality Microsoft has built into Windows, called the **Windows Subsystem for Linux**. This is the least invasive way to have access to both command line Linux and GUI functionality. Per Microsoft: "The Windows Subsystem for Linux lets developers run a GNU/Linux environment -- including most command-line tools, utilities, and applications -- directly on Windows, unmodified, without the overhead of a traditional virtual machine or dualboot setup."  Ignore the 'developers' portion of that sentence... it works just as well for anyone else. When you install Linux through WSL, you are, in essence, running the Linux kernel on top of the Windows kernel, making Linux fast and resource light. For a discussion of WSL, see [FAQs About WSL](https://learn.microsoft.com/en-us/windows/wsl/faq). 

Since that FAQ was written, Microsoft has added WSL2 and WSLg, which gives you not only access to Linux through the command line, but allows you to run GUI based Linux apps as well! Although you cannot run a complete Linux GUI in this way, you can run almost any Linux GUI based apps. They look and act like they would in a full Linux GUI OS, and are rendered by the Windows system.

- #### **Pros**
- Gives you a Linux command line in a Windows terminal.
- Only minor changes to your existing Windows installation.
- Little or no impact on the operation of Windows itself.
- Allows GUI based Linux apps to run under Windows.
- #### **Cons**
- Requires a bit of effort to install, moderate Windows experience helpful.
- GUI based app support is not complete; desktop focused tools and apps may not run.
- There are only a handful of distributions available through the Microsoft store. (You can technically install any distro through WSL, but the ones available through the store are selected for maximum compatability. Fortunately, Ubuntu is one of them.)

For directions on installing WSL Linux to your Windows PC, see [Installing Windows Command Line Linux](/Tutorials/Installing%20Windows%20Command%20Line%20Linux.md)  

### **Option Four: Install Linux in a Windows Virtual Machine**

This option allows you to install a complete Linux distribution to your Windows PC... graphical user interface and all... while making fairly easy changes to your operating system and PC setup that are also easily reversed. A virtual Machine is a form of system software that runs in an operating system and imitates the hardware and software of an another computer. This allows you to run another operating system within your native operating system. To the user, open a window, or blow the window up to full screen, and it looks just like a full blown Linux installation inside. To the linux installation itself, it appears that it is installed and running on it's own hardware. 

Just to be clear, your machine's operating system is still Windows... Linux is running within software running within Windows. You cannot run Linux separately from Windows. When you start Linux within its virtual machine, however, you can run it in full screen mode, and your PC will LOOK like a Linux machine... and have all the functionality of one. There is a big however, however... Windows is a hog when it comes to system resources, and it's still consuming all those resources in the background. This can cause Linux to run perceptibly slow, especially if you do not have a fast machine with a lot of RAM and a solid state drive. This can be frustrating coming from Windows, which is presumably configured and running well on your hardware. Also, your PC needs to support Virtualization (which pretty much all recent machines do). In other words, if you have an older, lower to middle level PC, installing Linux in a virtual machine may be just the frustrating experience that convinces you to not want to continue experiencing Linux.

If you decide to go for this option, Virtual Machine software is fairly easy to install, configure and use. Probably the best one available for running Linux is Oracle's [VM Virtual Box](https://www.oracle.com/virtualization/virtualbox/). As mentioned, should you decide that you wish to remove this form of Linux, this type of installation is also fairly easy to remove.

- #### **Pros**
- Only minor, reversible changes to your existing Windows installation... roughly the equivalent of installing several pieces of software.
- Little or no impact on the operation of Windows itself, unless you want to be running both Windows and Linux side by side and working between the two.
- You CAN work side by side between the two.
- Gives the full experience of GUI based Linux.
- Fairly easy to install; if you are good at following straightforward install directions, there is little here that is complicated or tricky.
- Supports almost all distributions, although some, like Ubuntu, work better.
- #### **Cons**
- Can not pick this option if your machine does not support Virtualization.
- Depending on the age of your machine, Linux can run frustratingly slow.
- Occasional issues with access to certain hardware or networking functionality which may require additional downloads.

For directions on installing Linux in a virtual machine, see [Installing Virtual Machine Linux](/Tutorials/How to Install Linux in a Windows Virtual Machine.md) 

### **Option Five: Dual Boot Windows & Linux**

This is the closest you can get to dedicating your PC entirely to Linux without actually doing so. With a dual boot system, you choose which operating system you want to run each time you start your PC. Unlike Virtual Box Linux, you can't just flip quickly between operating systems... you have to shut down and reboot to go from one to the other.  But also unlike VB Linux, Linux is not constrained by Windows consuming excessive system resources. You get the full experience of running Linux as your native OS while keeping your Windows installation. Linux utilizes system resources far better than Windows does, and so you may be pleasently surprised to find your machine functions faster than under Windows.

However, dual boot systems in Windows can be tricky to install (mostly due to partitioning considerations), and consume larger amounts of hard drive space as you have to provide space for two operating systems, cutting down the space available to each one. Because of this, dual booting may not be viable option if you have a PC that has a small drive, a mostly full drive, or cannot have an adiitional drive added (like most laptops). Removing a dual boot installation and returning your PC to its original state can also be tricky, given Windows propensity to dislike changes to its boot sector and boot manager. Again, if you are good at following install instructions and have some degree of troubleshooting skill (should something go amiss), this is perhaps the best of all options to immerse yourself in Linux without giving up Windows entirely.

- #### **Pros**
- The most complete Linux experience, aside from scrapping Windows entirely or buying another machine.
- Allows you to keep your existing Windows installation.
- #### **Cons**
- Most difficult and risky of all options to install, with the real possibility of disabling your PC.
- Uninstallation also runs the risk of disabling your PC.
- Unlike Virtual Box Linux, your choice of distribution is dependent on whether that distro supports your hardware.

For a discussion of the issues involved with dual-booting and installation instructions, see [Dual Booting Windows and Linux](/Tutorials/How to Dual Boot Linux on a PC Windows Machine.md).  








