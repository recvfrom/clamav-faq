Installation guide: ClamAV 0.99.3 +

_*Note: some of the packages used for installation are for 0.100.0+ versions of ClamAV._
_*Note: ClamAV-x64 directory name was changed in 0.100.0 to ClamAV._

### Introduction:

Clam AntiVirus is an open source (GPL) anti-virus toolkit designed especially
for e-mail scanning on mail gateways. It provides a number of utilities including
a flexible and scalable multi-threaded daemon, a command line scanner and advanced
tool for automatic database updates. The core of the package is an anti-virus engine
available in a form of shared library.

The reason for this guide is to provide installation instructions to the ClamAV product.
As of right now, you can install ClamAV on Linux, Mac OSX and Windows.

### Packages needed for installation:

Below are the steps for installing ClamAV from source Windows 7/10 systems.

```
Required Packages:
```

- Visual Studios 2015
![win-1](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/Windows/win-1.jpg)
![win-2](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/Windows/win-2.jpg)
![win-3](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/Windows/win-3.jpg)

### How to download AND install ClamAV from source:

**Step 1:**
Navigate to [http://www.Clamav.net](http://www.Clamav.net)

![win-4](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/Windows/win-4.jpg)

The page should look similar to:

**Step 2:**
You will want to look for the "Download" button in the upper left hand corner and click it.

![win-5](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/Windows/win-5.jpg)

**Step 3:**
Once you are on the download section, you will see something similar to "Alternate Versions of
ClamAV." Click that, and find Windows. Select Windows.

![win-6](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/Windows/win-6.jpg)

Select the file and download:

![win-7](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/Windows/win-7.jpg)

**Step 4:**
Once the file is downloaded, you will want to run the file by double clicking the setup.exe file.
Once that is done, you should see: Click Install

![win-8](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/Windows/win-8.jpg)
![win-9](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/Windows/win-9.jpg)

**Step 5:**
Now, you will hit “Next” which will take you to a screen to choose where to install ClamAV. For
this, we are going to keep it in `C:\Program Files\ClamAV-X64\` and select "everyone" who uses
this computer for whom can use ClamAV. You can choose the best options for you.

![win-10](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/Windows/win-10.jpg)

**Step 6:**
Once that is done, you will hit Next. That will bring you to a screen that says “The installer is
ready to install ClamAV-x64 on your computer. Click "Next" to start the installation.
Hit Next.
Depending on your Windows settings, you might be prompted with a UAC (user access control)
message as seen below:

![win-11](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/Windows/win-11.jpg)

Please hit “Yes” to continue the install.

**Step 7** :
Assuming everything went smoothly, you will be prompted with an "installation complete" page.

![win-12](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/Windows/win-12.jpg)

**Step 8:**
From here, you will need to navigate to `C:\Program Files\ClamAV\conf_examples`.
You will need to copy the `freshclam.conf.sample` and save it as "freshclam.conf" in the
`C:\Program Files\ClamAV`
_*NOTE You will want to edit it with a text editor with Admin rights to comment out the word “example”_

![win-13](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/Windows/win-13.jpg)

Step 9:
Run Freshclam.exe from command line:

![win-14](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/Windows/win-14.jpg)

OR you can click on `freshclam.exe` in the ClamAV directory. Once that is done, you should be set for the
installation. You might want to use 'run as administrator' for the `freshclam.exe` if you get a permissions error.



