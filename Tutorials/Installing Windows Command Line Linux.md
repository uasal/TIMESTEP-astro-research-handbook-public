![WL2 Linux](/Assets/Images/PenguinWindows.png)

---

# Installing Windows Command Line Linux

This tutorial will enable you to install Linux to your Windows PC using Windows Subsystem for Linux (WSL). WSL allows you to install a Linux distribution to your PC and run Linux without having to use dual boot or a virtual machine environment. You will have a completely functional Linux command line, as well as limited access to applications that require a GUI.  

For more information on WSL, go here: [What is the Windows Subsystem for Linux?](https://learn.microsoft.com/en-us/windows/wsl/about).  

---

## Windows PC Requirements

To take full advantage of Linux under WSL, you must be running either Windows 10 (Version 2004 / Build 19041 or higher) or Windows 11. It is also recommended that your machine is completely up to date with the latest available Windows upgrades.  

#### To Check Your Version/Build

1. Open a '**run**' window by using **Windows Logo Key + R**
2. Type **winver**, then click OK.
3. Your Version needs to be 2004, 20H2, 21H1, 21H2, 22H2, etc, and your build needs to be 19041 or anything numerically larger, ie, 19042, 19043, etc.
4. If your Windows version/build does not meet this requirement, updating with Windows Update may bring you up to a current version. For instructions on using Windows Update, see: [Update Windows](https://support.microsoft.com/en-us/windows/update-windows-3c5ae7fc-9fb6-9af1-1984-b5e0412c556a).

#### For Older Versions of Windows

It is possible to run Linux on older systems and builds, but functionality will be reduced and there will be a more limited selection of Linux distros that you will be able to install. For instructions on how to proceed, see: [Manual Installation Steps for Older Versions of WSL](https://learn.microsoft.com/en-us/windows/wsl/install-manual).

---

## First Step: Install WSL

WSL is a Microsoft Windows add-on. The easiest way to install it is by using a PowerShell command in an elevated (administrator) PowerShell terminal. There are two quick ways of opening a powershell terminal:

#### Open Powershell in Administrator Mode, Method One

1. Right click on the Windows start menu icon.
2. Select **Windows Powershell (admin)**  

#### Open Powershell in Administrator Mode, Method Two

1. Left click on the Windows start menu icon.
2. Type **Powershell**
3. In the right panel, click on **Run As Administrator** 

#### Verify Terminal is in Admin Mode

After opening the terminal, verify that it is in admin mode by looking at the left side of the title bar. If it does not indicate 'Administrator', as in the picture below, shut down the window and try the other method.

 ![Elevated PowerShell](/Assets/Images/PowerShellWindow.png)

#### Enable WSL

In the PowerShell Window, cut and paste or manually enter the following command:  

```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart'
```

This will enable WSL on your machine. 

---

## Second Step: Install WSL2

WSL2 is essentially a virtual machine that WSL uses to allow Linux to run GUI based applications. Beware, however: WSL2 still relies on the Windows rendering system, and as such, some of the more complex GUI based Linux apps (Anaconda Navigator and Spyder, for example) simply won't run under it. (The exception to this is Ubuntu 22.4.1 with the vGPU driver install, which seems to run virtually anything, so to speak. If you choose a different distro, there is a workaround to this limited functionality that I'll discuss towards the end of this tutorial.) 

#### Prepare to Install WSL2

Because WSL2 is a virtual machine, we have to make sure that Virtualization is enabled in your machine's BIOS. To do this from Windows:  

1. Hit **Ctrl** + **Shift** + **Esc** to bring up Task Manager.
2. Click on the **Performance** tab.
3. Look for **Virtualization** in the list under the graph. This should be followed by **Enabled**. If it is not, you will have to follow the next step before proceeding.

#### Enable Virtualization in your BIOS settings

Instructions for enabling Virtualization in your machine's BIOS can be found here: [Enabling Virtualization in Your PC's BIOS](https://bce.berkeley.edu/enabling-virtualization-in-your-pc-bios.html).  

If your PC does not support Virtualization, you will not be able to install WSL2. You can still install a limited subset of Linux distros, but will not be able to take advantage of Windows built in Linux GUI functionality.  

#### Enable the Virtual Machine Platform in Windows

If you know you already have this enabled, you can skip this step. If you are not sure, go ahead and run the following command in PowerShell. You should receive a 'successfully completed' message when it is finished.

```PowerShell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

At this point, you must reboot your machine.  

#### Download and Install WSL2

1. Go to this link and download the WSL2 kernel update: [WSL2](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi).
2. Run the file.
3. When asked to elevate permission, click yes.

#### Set WSL2 as Default

Enter the following command in PowerShell to set WSL2 as the default for installed distros:

```PowerShell
wsl --set-default-version 2
```

*Note that if you choose a distro that does not run under WSL2, you can reissue this command specifying version 1.* 

---

## Third Step: Select and Install a Linux Distribution

TIme to select your preferred flavor of Linux. Ubuntu is perhaps the best supported through WSL2, with pages on Canonical Group's site dedicated to troubleshooting installations and providing general help information. Canonical also works with Microsoft and developers to make sure Ubuntu's interface with WSL is seamless. The current version is 22.4.1 LTS, and is available here: [Ubuntu 22.4.1 LTS](https://apps.microsoft.com/store/detail/ubuntu-22041-lts/9PN20MSR04DW).  

Here are a few other Distros from the Microsoft Store:  

1. [OpenSUSE-Leap 42](https://apps.microsoft.com/store/detail/opensuse-leap-42/9NJVJTS82TJX?hl=en-us&gl=us). Open SUSE is a general purpose Linux distro; to learn more, go to: [OpenSUSE Developer Website](To learn more visit: https://www.opensuse.org/).
2. [Kali Linux](https://apps.microsoft.com/store/detail/kali-linux/9PKR34TNCV07?hl=en-us&gl=us). Kali Linux is a speciality distro designed for ethical hacking and systems testing. It is an extremely sparse installation and not a good choice for general usage. For more info, go to: [Kali Linux Developer Website](https://www.kali.org).
3. [Debian Linux](https://apps.microsoft.com/store/detail/debian/9MSVKQC78PK6?hl=en-us&gl=us). Debian is a stable Linux distro widely used by developers because of its broad hardware base. For more info: [Debian Developer's Website](www.debian.org).
4. [Ubuntu 20.04.5](https://apps.microsoft.com/store/detail/ubuntu-20045-lts/9MTTCL66CPXJ). For those who want Ubuntu, but whose machine's will not support the vGPU driver. 

Almost any Linux distro can be installed into the WSL/WSL2 system, but these are the distros available through the Microsoft store that have been selected for compatability and (relatively) seemless installation. I would strongly suggest that if you do not choose Ubuntu, choose one of these.   

#### Install The Distro

After you have finished downloading the distro, run the package and it will install to your machine. The installer will add an icon for the Linux OS to your Windows start menu. Note that any Linux apps that you install through the Linux OS will show up in a folder with the same name in your Windows start menu. You can start these apps from here, or through the Linux OS itself.

The first time you run the newly installed Linux system, you will start it from here, just like any other app. It will open a window that will ask you to do some basic configuration, such as username and password. It may also ask you to pick a drive mount location; I would advise to accept the default. Be aware that this first run will be fairly slow moving, as Linux is configuring itself behind the scenes.

#### If Installing Ubuntu 22.4.1 LTS, This is an Additional Required Step after Distro Install

Ubuntu 22.4.1 LTS takes maximal advantage of WSL2's GUI capabilities by utilizing a virtual GPU, called vGPU. To do this, it requires the installation of a specific video driver. The instructions for installing this driver are located here: [Enabling vGPU acceleration in Ubuntu](https://ubuntu.com/tutorials/enabling-gpu-acceleration-on-ubuntu-on-wsl2-with-the-nvidia-cuda-platform#1-overview).

*Note: This extra step may seem like a reason to avoid the Ubuntu distribution, but the additional extra effort is well worth it. Just make sure that you follow the advice to make sure your processor is supported before you attempt the install. If it is not supported, you will not be able to install 22.4.1 LTS, as the OS will not run without the driver. You can still use Ubuntu; but you will have to use an earlier version, such as 20.04.5.*

---

## Recommended Optional Steps

There are a few more things to consider that will make your WLS Linux life much easier, including the selection of a terminal program and installation of the Anaconda Python environment for Linux.

#### Choose a Terminal Program

Although you can start and run your Linux OS from the start menu and use it's built in terminal, I would strongly recommend that you choose to use a different terminal. There are two excellent choices, largely depending on how you intend to use your Linux OS.  

##### If you intend to only use the command line:

If you intend to use WSL Linux through the command line, and don't really see yourself using GUI based Linux apps because, hey, you are already in a GUI OS, then this is most likely the choice for you. The first choice, and one that I personally think all Windows users should have regardless of whether or not the are running Linux installs, is the open source **Windows Terminal** app. This is an excellent command line interface that has tabs for the Windows Command Prompt, Powershell, and whatever Linux distros you have installed. It's highly configurable, and to start your Linux OS, you simply open **Terminal** and click on your distro's tab. You are up and running at the Linux command line.

You can get Windows Terminal here: [Terminal](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701?hl=en-gb&gl=gb).  

##### If you want robust GUI functionality:

Remember when I mentioned there was a workaround for the failures of the WSL2 GUI system? Here it is. For those who want to be able to run full-on Linux GUI apps, like Anaconda's Navigator based apps, including the Spyder IDE, this is the terminal to choose. It's called **MobaXTerm**, and as the name hints at, it comes with its own XWindows implementation. When you run your Linux OS through MobaXTerm, it augments WSL2 and enables complex GUI intensive Linux apps to run in the WIndows environment.

Aside from that, it's very similar to Windows Terminal. When you install it, it will create tabs for your Linux distribution, and to start the Linux system, you simply open **MobaXTerm** and start a terminal session. Your GUI apps then start as if you were in a regular Linux environment… for instance, to run Anaconda navigator, you type `anaconda-navigator` at the command line, and navigator opens its GUI interface.

You can get MobaXTerm here: [MobaXTerm](https://mobaxterm.mobatek.net/).

#### Install Anaconda

Anaconda is perhaps the most popular open-source Scientific Python distribution package. With the Anaconda installer, you get a host of supporting tools, like Jupyter Notebooks, the excellent Spyder IDE, and a ton of preinstalled Python libraries. You can install the Linux version in your new command line Linux OS, and if you have also installed MobaXTerm, you can take advantage of all the GUI based tools Anaconda offers. 

The Anaconda website is here: [Anaconda](https://www.anaconda.com/products/distribution).
The appropriate Linux distribution is here: [Anaconda x86 64-bit Installer](https://repo.anaconda.com/archive/Anaconda3-2022.05-Linux-x86_64.sh).

## Congratulations!

You have reached the end of the tutorial, and should now have a functioning Linux installation, your first step in learning how to use the operating system that is ubiquitous to scientific workplaces. Have fun!
