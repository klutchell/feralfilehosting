
This Guide will allow you to mount your Feral slots remote file system as a local file system through SFTP.

> **Recommended Method:** Install Dokan Libraries and then use win-sshfs.

To do this you need meet these requirements:

**1:** You have a Feral slot that has been activated and you can SSH to. This means that your FTP/SFTP/SSH user name and password have been set-up and and are visible from You can do this from the `Install Software` link in your [Account Manager](https://www.feralhosting.com/manager/)

You login information for the relevant slot will be shown here:

![](https://raw.github.com/feralhosting/feralfilehosting/master/Feral%20Wiki/0%20Generic/slot_detail_ssh.png)

**2:** You will need to install the Visual C++ Redistributable Packages for Visual Studio 2013 to make sure Dokan will work.

[http://www.microsoft.com/en-us/download/details.aspx?id=40784](Visual C++ Redistributable Packages for Visual Studio 2013)

Download and install `vcredist_x86.exe`
Download and install `vcredist_x64.exe`

> **Important note:** Install the x86 regardless of whether your system is x86 or you will get an error about `MSVCR120.dll` not being found

Now continue to download and install the Dokan library.

### Step 1

**1:** Remove the previous Dokan library if you had it installed via the Add or Remove programs option.

**2:** Download and install the current latest release from this URL:  [Dokan Libraries](https://github.com/dokan-dev/dokany/releases).

![](https://raw.github.com/feralhosting/feralfilehosting/master/Feral%20Wiki/SSH/Mount%20Your%20Server%20as%20a%20Local%20Filesystem%20-%20Windows%20-%20Dokan%20-%20win-sshfs/Dokan/dokan-1.png)

![](https://raw.github.com/feralhosting/feralfilehosting/master/Feral%20Wiki/SSH/Mount%20Your%20Server%20as%20a%20Local%20Filesystem%20-%20Windows%20-%20Dokan%20-%20win-sshfs/Dokan/dokan-2.png)

![](https://raw.github.com/feralhosting/feralfilehosting/master/Feral%20Wiki/SSH/Mount%20Your%20Server%20as%20a%20Local%20Filesystem%20-%20Windows%20-%20Dokan%20-%20win-sshfs/Dokan/dokan-3.png)

Reboot if asked.

You can now jump to the win-sshfs section.

### Step 2

This step requires some pre requisites in order to be installable:

**1:** You will need to install `Net 2.0` if you do not already have it. It comes as part of the `Net 3.5` web installer linked here:

[Net 3.5 x86 and x64](http://www.microsoft.com/en-us/download/details.aspx?id=21)

![](https://raw.github.com/feralhosting/feralfilehosting/master/Feral%20Wiki/SSH/Mount%20Your%20Server%20as%20a%20Local%20Filesystem%20-%20Windows%20-%20Dokan%20-%20win-sshfs/Dokan/sshfs.0.2.0%201.png)

**2:** You must install this Visual C++ 2005 SP1 x86 in order to install Dokan sshfs 0201226. It does not matter if you are on a x64 OS. You must have this x86 runtime.

[Microsoft Visual C++ 2005 SP1 Redistributable Package (x86)](http://www.microsoft.com/en-gb/download/details.aspx?id=5638)

If you do not do this you will get this error when trying to install sshfs 0.2.0:

![](https://raw.github.com/feralhosting/feralfilehosting/master/Feral%20Wiki/SSH/Mount%20Your%20Server%20as%20a%20Local%20Filesystem%20-%20Windows%20-%20Dokan%20-%20win-sshfs/Dokan/sshfs.0.2.0%20error.png)

Once you have installed both of these you can download and install the sshfs 0.2.0 executable.

[Dokan sshfs 0201226](http://dokan-dev.net/wp-content/uploads/dokan-sshfs-0201226.zip)  install this program. (it requires the Dokan library is installed)

### Step 3

Download and unpack the files:

[Dokan sshfs 0.60](http://dokan-dev.net/wp-content/uploads/dokan-sshfs-0.6.0.zip):  

We will use this to update the dokan-sshfs-0201226 to 0.6.0, Why will we do this? 

"This package doesn't include installer and Explorer extensions which add context menu to Dokan drive and permission setting dialog. If you want to support those features, please install dokan-sshfs-0.2.0.1226 and overwrite DokanNet.dll and DokanSSHFS.exe files by dokan-sshfs-0.6.0".

Now browse to the location you installed it to (if no shortcut is created) for example:

~~~
C:\Program Files\Dokan\DokanSSHFS\
~~~

Or

~~~
C:\Program Files (x86)\Dokan\DokanSSHFS\
~~~

You will need to copy the files from the Dokan sshfs 0.6.0 to this folder and overwrite the files.

![](https://raw.github.com/feralhosting/feralfilehosting/master/Feral%20Wiki/SSH/Mount%20Your%20Server%20as%20a%20Local%20Filesystem%20-%20Windows%20-%20Dokan%20-%20win-sshfs/Dokan/update.0.2.0%201.png)

Confirm the overwrite action:

![](https://raw.github.com/feralhosting/feralfilehosting/master/Feral%20Wiki/SSH/Mount%20Your%20Server%20as%20a%20Local%20Filesystem%20-%20Windows%20-%20Dokan%20-%20win-sshfs/Dokan/update.0.2.0%202.png)

These are the files that have been updated:

![](https://raw.github.com/feralhosting/feralfilehosting/master/Feral%20Wiki/SSH/Mount%20Your%20Server%20as%20a%20Local%20Filesystem%20-%20Windows%20-%20Dokan%20-%20win-sshfs/Dokan/update.0.2.0%203.png)

### Step 4

Then run the DokanSSHFS.exe  located in this folder and enter your details in the windows that pops up:

One the program starts you will see something like this:

![](https://raw.github.com/feralhosting/feralfilehosting/master/Feral%20Wiki/SSH/Mount%20Your%20Server%20as%20a%20Local%20Filesystem%20-%20Windows%20-%20Dokan%20-%20win-sshfs/Dokan/mount.png)

**Important note:** you need to specify the full path to the root of your home directory. So it will be something like:

~~~
/media/DiskID/home/yourusername
~~~

If you want to use a keyfile it will need to be in the OpenSSH format. To convert your PuTTy PPK file to the OpenSSH format do this:

![](https://raw.github.com/feralhosting/feralfilehosting/master/Feral%20Wiki/SSH/Mount%20Your%20Server%20as%20a%20Local%20Filesystem%20-%20Windows%20-%20Dokan%20-%20win-sshfs/Dokan/puttygen.png)

Upon connecting Dokan will tell you that is has started SFTP and then you should see you mounted volume in My computer with the driver letter assigned in the settings. If you get an error about assigning the driver letter check that the Dokanmounter service is running.

this was done on: 

Windows 7 x86 & x64 with no compatibility settings used. Net 2 and 3.5 are included in an updated Windows 7. You must install Microsoft Visual C++ 2005 SP1 Redistributable Package (x86)

Windows 8 x86 & x64 with Windows 7 compatibility settings used. Net 2 and 3.5 must be installed manually. You must install Microsoft Visual C++ 2005 SP1 Redistributable Package (x86)


### win-sshfs

**Step 1:**

Make sure you have downloaded and installed the Dokan 0.6.0 Libraries. You can skip this step if you have done this previously.

**Important note:** Windows 8 users must use Windows 7 compatibility mode on this installer.

![](https://raw.github.com/feralhosting/feralfilehosting/master/Feral%20Wiki/SSH/Mount%20Your%20Server%20as%20a%20Local%20Filesystem%20-%20Windows%20-%20Dokan%20-%20win-sshfs/Dokan/compat%201.png)

Download and install this: 

[Dokan Libraries](http://dokan-dev.net/wp-content/uploads/DokanInstall_0.6.0.exe) you will need to install this first, reboot if asked.

**Important note:** If you see this box on Windows 8 just click "This program ran correctly" option:

![](https://raw.github.com/feralhosting/feralfilehosting/master/Feral%20Wiki/SSH/Mount%20Your%20Server%20as%20a%20Local%20Filesystem%20-%20Windows%20-%20Dokan%20-%20win-sshfs/Dokan/compat%202.png)

**Step 2:**

Download and install win-sshfs:

[Download win-sshfs](http://code.google.com/p/win-sshfs/downloads/list)

![](https://raw.github.com/feralhosting/feralfilehosting/master/Feral%20Wiki/SSH/Mount%20Your%20Server%20as%20a%20Local%20Filesystem%20-%20Windows%20-%20Dokan%20-%20win-sshfs/win-sshfs/1.png)

You will need to meet all these requirements to install and use win_sshs

![](https://raw.github.com/feralhosting/feralfilehosting/master/Feral%20Wiki/SSH/Mount%20Your%20Server%20as%20a%20Local%20Filesystem%20-%20Windows%20-%20Dokan%20-%20win-sshfs/win-sshfs/2.png)

IF you see this box when installing make sure to "Overwrite" the destination file.

![](https://raw.github.com/feralhosting/feralfilehosting/master/Feral%20Wiki/SSH/Mount%20Your%20Server%20as%20a%20Local%20Filesystem%20-%20Windows%20-%20Dokan%20-%20win-sshfs/win-sshfs/overwrite.png)

If you do not have Net Framework 4 installed you can get it from here.

[Net Framework 4 Web Installer](http://www.microsoft.com/en-gb/download/details.aspx?id=17851)

**Step 3:**

Once install and running you will see the icon in the tray. Right click on it and click on "Show Manager":

![](https://raw.github.com/feralhosting/feralfilehosting/master/Feral%20Wiki/SSH/Mount%20Your%20Server%20as%20a%20Local%20Filesystem%20-%20Windows%20-%20Dokan%20-%20win-sshfs/win-sshfs/2.5.png)

This is the default screen you will see, click on "Add"

![](https://raw.github.com/feralhosting/feralfilehosting/master/Feral%20Wiki/SSH/Mount%20Your%20Server%20as%20a%20Local%20Filesystem%20-%20Windows%20-%20Dokan%20-%20win-sshfs/win-sshfs/3.png)

Fill in your information as shown in the image. The "Save" before trying to mount:

![](https://raw.github.com/feralhosting/feralfilehosting/master/Feral%20Wiki/SSH/Mount%20Your%20Server%20as%20a%20Local%20Filesystem%20-%20Windows%20-%20Dokan%20-%20win-sshfs/win-sshfs/4.png)

Once you have saved you will see something like this. Now you can try to "Mount" the drive.

![](https://raw.github.com/feralhosting/feralfilehosting/master/Feral%20Wiki/SSH/Mount%20Your%20Server%20as%20a%20Local%20Filesystem%20-%20Windows%20-%20Dokan%20-%20win-sshfs/win-sshfs/5.png)

If successful with no programs errors, the drive will now be available to access and use. Click "Unmount" to unmount the drive

![](https://raw.github.com/feralhosting/feralfilehosting/master/Feral%20Wiki/SSH/Mount%20Your%20Server%20as%20a%20Local%20Filesystem%20-%20Windows%20-%20Dokan%20-%20win-sshfs/win-sshfs/6.png)

**Important note:** You can create and use multiple connection profiles and use them as the same time. Select each profile and "Mount" the server.



