Installation guide: ClamAV 0.99.2 +

_*Note: some of the packages used for installation are for 99.3+ versions of ClamAV._


### Introduction:

Clam AntiVirus is an open source (GPL) anti-virus toolkit designed especially
for e-mail scanning on mail gateways. It provides a number of utilities including
a flexible and scalable multi-threaded daemon, a command line scanner and advanced
tool for automatic database updates. The core of the package is an anti-virus engine
available in a form of shared library.

The reason for this guide is to provide installation instructions to the ClamAV product.
As of right now, you can install ClamAV on Linux, Mac OSX and Windows.


### Packages needed for installation:

Below are the steps for installing ClamAV from source on Linux systems.

```
Required Packages:
```

- Zlib and zlib-devel packages
- Openssl version 0.9.8 or higher and libssl-devel packages
- GCC compiler suite. (tested with 2.9x, 3.x and 4.x series)

If you are compiling with higher optimization levels than the default one (-O
for gcc), be aware that there have been reports of misoptimizations. The
build system of ClamAV only checks for bugs affecting the default settings,
it is your responsibility to check that your compiler version doesn’t have any
bugs.

- GNU make (gmake) / Make

```
Recommended Packages:
```

- Bzip2 and bzip2-devel library
- Libxml2 and libxml2-dev library
- Check unit testing framework


### Pre-requisite install steps for Rhel / CentOS:
_NOTE* The names of the software below are subject to change, when running the commands to install._

**Step 1** : Install openssl
Example: `yum install openssl`

**Step 2** : Install openssl-devel
Example: `yum install libssl-dev`

**Step 3** : Install zlib-devel
Example: `yum install zlib-devel`

**Step 4** : Install libpng-devel
Example: `yum install libpng-devel`

**Step 5** : Install libxml2-devel
Example: `yum install libxml2-devel`

**Step 6** : Install json-c-devel
Example: `yum install json-c-devel`

**Step 7** : Install bzip2-devel
Example: `yum install bzip2-devel`

**Step 8** : Install valgrind (this is for testing the unit tests)
Example: `yum install valgrind`

**Step 9** : Install pcre-devel
Example: `yum install pcre-devel`

**Step 10** : Install check
Example: `yum install check`

**Step 11** : Install LLVM (versions between 3.0 – 3.6)
Example: Navigate to the LLVM webpage:
[http://releases.llvm.org](http://releases.llvm.org) to download the version. Keep in mind you will also need to
untar this file, and run the `./configure`, `make`, `make install` on this software.

At this point, all of the pre-reqs should be installed for ClamAV.


### How to download AND install ClamAV from source:

**Step 1:**
Navigate to [http://www.Clamav.net](http://www.Clamav.net)

The page should look similar to:

![rhel-1](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/rhel/rhel-1.jpg)

**Step 2:**
You will want to look for the Download button in the upper left hand corner and click it.

![rhel-2](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/rhel/rhel-2.jpg)

**Step 3:**
Once you are on the download section, you will see something similar to the latest stable
release is 0.99.2. Underneath that, you will see tar.gz files. You will want to locate the one for
your operating system. For Linux, we will use the Clamav-0.99.2.tar.gz file.
Please download the file:

![rhel-3](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/rhel/rhel-3.jpg)

**Step 4:**
Once the file is downloaded, you will want to drop it in a location you wish to install Clam. For
the sake of this document, I will drop the file in my `/opt` location. But you can choose where
you would like to untar the file. Keep in mind, if you untar this in `/tmp` make sure that you do
not have the operating system set to clear `/tmp` files on reboot.
To move the file from Downloads run:

`cp Downloads/clamav-0.99.2.tar.gz /opt`

Depending on your user rights, you might need to use sudo.

![rhel-4](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/rhel/rhel-4.jpg)

**Step 5:**
Now, you will want to navigate to `/opt` by doing a CD. After that, you need to untar that
monster file by running the following: `tar –xvf clamav-0.99.2-tar.gz`

![rhel-5](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/rhel/rhel-5.jpg)

**Step 6:**
When you do a ls you will see the tar.gz file, and a folder for clamav-0.99.2.

![rhel-6](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/rhel/rhel-6.jpg)

You will want to `cd` into clamav-0.99.2:

![rhel-7](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/rhel/rhel-7.jpg)

**Step 7** :
Assuming you want to install the configuration files in `/etc`, configure and build the software
with the following:

`./configure –sysconfdir=/etc`

![rhel-8](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/rhel/rhel-8.jpg)

_NOTE* at the end of the `./configure` command, you will see a print out of the summary to make sure everything is
being detected. You should verify that the packages you installed are in fact being detected:_

![rhel-9](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/rhel/rhel-9.jpg)

After the `./configure` command finishes, you want to run `make`

![rhel-10](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/rhel/rhel-10.jpg)

Once that finishes, run `make install`

**Step 8:**
I will start this step with a common error that might pop up when doing a freshclam

![rhel-11](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/rhel/rhel-11.jpg)

How do you fix that you ask? Simple:
Run the following:

`sudo ldconfig`

**Step 9:**
You will need to edit the freshclam.conf file. At minimum, you have to uncomment the Example
line as seen below:

![rhel-12](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/rhel/rhel-12.jpg)

As you can see I added a # before Example.
You will need to use an editor, nano or whatever to edit the file. Make sure you rename the file
as freshclam.conf


**Step 10:**
If you are installing Clam-AV for the first time, you have to add new user and group to
system - clamav:

```
groupadd clamav
```

```
useradd -g clamav -s /bin/false -c "Clam Antivirus" clamav
```

![rhel-13](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/rhel/rhel-13.jpg)

**Step 11:**
Let͛s create the directory needed for freshclam:

`/usr/local/share/clamav`

![rhel-14](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/rhel/rhel-14.jpg)

`mkdir /usr/local/share/clamav`

**Step 12:**
Making the database directory writeable with the following:

`chmod 777 /usr/local/share/clamav`

![rhel-15](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/rhel/rhel-15.jpg)

**Step 13:**
Run a freshclam to download the latest updates.
Just type `freshclam`

![rhel-16](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/rhel/rhel-16.jpg)

Once that is done, you should be set for the installation.


### UNIT TEST CHECKS

But how do I test out that the unit tests are passing?

**Step 1:**
Navigate back to where ClamAV is installed. `cd /opt/clamav-0.99.2`

**Step 2:**
Preform the following:
`./configure`

**Step 3:**
`make check VG=1`

IF done correctly, you will see something like this:

![rhel-17](https://github.com/Cisco-Talos/clamav-faq/blob/master/manual/pictures_4_markdown/rhel/rhel-17.jpg)

The `check7_clamd.hg.sh` will skip, and that is fine for now.

If you have a failure or an error in the unit tests:
1) Could be that you do not have installed all the packages mentioned above.

If you are investigating a failure, please do the following:

`cd unit_tests`

`cat` whatever check failed by adding a .log to the end of it.
Example: `cat check4_clamd.sh.log`


