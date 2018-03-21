Installation guide: ClamAV 0.99.+
_*Note: some of the packages used for installation are for 99.3+ versions of ClamAV._
_*Note: In the below commands, SUDO or SU is used- this will depend on the permissions of your operating system and directories if needed._

### Introduction:

Clam AntiVirus is an open source (GPL) anti-virus toolkit designed especially
for e-mail scanning on mail gateways. It provides a number of utilities including
a flexible and scalable multi-threaded daemon, a command line scanner and advanced
tool for automatic database updates. The core of the package is an anti-virus engine
available in a form of shared library.

The reason for this guide is to provide installation instructions to the ClamAV product.
As of right now, you can install ClamAV on Linux, Mac OSX and Windows.

### Packages needed for installation:

Below are the steps for installing ClamAV from source on MacOS X systems.
```
Required Packages:
```
- Zlib and zlib-devel packages
- Openssl version 0.9.8 or higher and libssl-devel packages
- XCode command line tools. (GCC or Clang compiler suite. Tested with 2.9x, 3.x and 4.x series)

If you are compiling with higher optimization levels than the default one (-O2
for gcc), be aware that there have been reports of misoptimizations. The
build system of ClamAV only checks for bugs affecting the default settings,
it is your responsibility to check that your compiler version doesn’t have any
bugs.

- GNU make (gmake)

```
Recommended Packages:
```
- Bzip2 and bzip2-devel library
- Libxml2 and libxml2-dev library
- 'Check' unit testing framework
- Libjson-c-devel
- Ncurses-devel
- Libcurl-devel

### Pre-requisite install steps for MAC OS X:


_NOTE* The names of the software below are subject to change, when running the commands to install._

**Step 1** : Install homebrew
Example: 
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

**Step 2:** Install OpenSSL
Example: brew install openssl

_NOTE* openssl might generate an error in ./configure of “cannot be found.” If this is the case, follow the following:_
```
brew remove openssl
brew doctor
brew update
brew upgrade
brew install openssl
ls –s /opt/openssl/include/openssl
```


**Step 3:** install check
Example: brew install check

**Step 4:** install valgrind
Example: brew install valgrind

At this point, all of the pre-req’s should be installed for ClamAV.

### How to download AND install ClamAV from source:

**Step 1:**
Navigate to [http://www.Clamav.net](http://www.Clamav.net)

The page should look similar to:
![mac-1](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/Mac/mac-1.jpg)


**Step 2:**
You will want to look for the “Download” button in the upper left hand corner and click it.
![mac-2](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/Mac/mac-2.jpg)

**Step 3:**
Once you are on the download section, you will see something similar to “The latest stable
release is 0.99.2.” Underneath that, you will see tar.gz files. You will want to locate the one for
your operating system.
Please download the file:
![mac-3](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/Mac/mac-3.jpg)

**Step 4:**
Once the file is downloaded, you will want to drop it in a location you wish to install Clam. For
the sake of this document, I will drop the file on my desktop in a “Clamav” folder location. But
you can choose where you would like to untar the file. Keep in mind, if you untar this in “/tmp”,
make sure that you do not have the operating system set to clear “/tmp” files on reboot.
To move the file from Downloads run:
‘cp Downloads/clamav-0.99.2.tar.gz /Desktop’

Depending on your user rights, you might need to use sudo.
![mac-4](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/Mac/mac-4.jpg)

**Step 5:**
Now, you will want to navigate to “clamav” folder by doing a CD. After that, you need to untar
that monster file by running the following: tar –xvf clamav-0.99.2-tar.gz
![mac-5](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/Mac/mac-5.jpg)

**Step 6:**
When you do a “ls” you will see the tar.gz file, and a folder for clamav-0.99.2.
![mac-6](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/Mac/mac-6.jpg)

You will want to “CD” into clamav-0.99.2:
![mac-7](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/Mac/mac-7.jpg)

**Step 7** :
Assuming you want to install the configuration files in /etc, configure and build the software
with the following:
./configure –sysconfdir=/etc
![mac-8](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/Mac/mac-8.jpg)

_NOTE* at the end of the ./configure command, you will see a print out of the summary to make sure everything is
being detected. You should verify that the packages you installed are in fact being detected:_
![mac-9](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/Mac/mac-9.jpg)

After the ./configure command finishes, you want to run “make”
![mac-10](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/Mac/mac-10.jpg)

Once that finishes, run “make install”

**Step 9:**
You will need to edit the freshclam.conf file in /etc/freshclam.conf. At minimum, you have to
uncomment the Example line as seen below:
![mac-11](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/Mac/mac-11.jpg)

As you can see I added a # before Example.
You will need to use an editor, nano or whatever to edit the file. Make sure you rename the file
as “freshclam.conf”


**Step 10:**
Let’s create the directory needed for freshclam:
/usr/local/share/clamav
![mac-12](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/Mac/mac-12.jpg)

mkdir /usr/local/share/clamav

**Step 11:**
Making the database directory writeable with the following:

chmod 777 /usr/local/share/clamav
![mac-13](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/Mac/mac-13.jpg)

**Step 12:**
Run a freshclam to download the latest updates.
Just type “freshclam”
![mac-14](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/Mac/mac-14.jpg)

Once that is done, you should be set for the installation.


### UNIT TEST CHECKS

But how do I test out that the “unit tests” are passing?

Step 1:
Navigate back to where ClamAV is installed. Cd /opt/clamav-0.99.

Step 2:
Preform the following:
./configure

Step 3:
Make check VG=1

IF done correctly, you will see something like this:
![mac-15](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/Mac/mac-15.jpg)

The check7_clamd.hg.sh will skip, and that is fine for now.

If you have a failure or an error in the unit tests:
1) Could be that you do not have installed all the packages mentioned above.

If you are investigating a failure, please do the following:
'cd unit_tests'
Cat whatever check failed by adding a .log to the end of it.
Example: cat check4_clamd.sh.log


