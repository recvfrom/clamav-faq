# Installing ClamAV #

## Installing from source ##

* Check [Requirements](#requirements)
* Uninstall any old version, see [UninstallClamAV] (Note: this isn't essential, but removes sources of problems).
* wget the source gzip file, see [Which Version].
* untar the source to an appropriate location. Note that most modern versions of tar will automatically ungzip for you.
* ensure you have a user clamav and group clamav.
  * If you're using a different group/user you must specify that using the _--with-user_ and/or _--with-group_ option when you run configure
* Configure the build:
  * for clamav-milter support _./configure --enable-milter_
  * to support new features _./configure --enable-experimental_
  * otherwise _./configure_
* run _make_
* if you did not uninstall the previous version, stop any running services.
* as root, run "make install" to install the binaries
* it is recommended that you run ldconfig as root after installing
* restart any relevant services.
* Run freshclam manually, to ensure your AV definitions are up to date.


### Requirements <a id="requirements" class="anchor">&nbsp;</a>###

Mandatory:

* C compiler
* zlib library

>__Note:__ you must compile with a shared library, use:
>_make clean ; ./configure -s_ __before__ _make_ when building zlib


## Installing From Packages ##

Installing your distribution's packages is the easiest route. It will make also upgrades easier.

### Understand which packages you need ###

You don't necessarily need all packages. Please read [ClamOverview] carefully to understand which ones you need.

## Operating System Specific Information ##

* [Debian](#debian)
* [RHEL/CentOS](#rhel)
* [Fedora](#fedora)
* [Mandriva](#mandriva)
* [Gentoo](#gentoo)
* [openSUSE](#opensuse)
* [FreeBSD, OpenBSD, NetBSD](#bsd)
* [Solaris](#solaris)
* [Slackware](#slackware)
* [Windows](#windows)
* [OpenVMS](#openvms)
* [OSX](#osx)

### Debian <a id="debian" class="anchor">&nbsp;</a> ###


`` # apt-get update ``

`` # apt-get install clamav ``

### RHEL/CentOS <a id="rhel" class="anchor">&nbsp;</a> ###

On CentOS:


`` # yum install -y epel-release ``

`` # yum install -y clamav ``


On [Community Enterprise Operating System (CentOS)] the clamav package requires the [Extra Packages for Enterprise Linux (EPEL) repository].

On [RedHat Enterprise Linux (RHEL)] the EPEL release package has to be installed either manually or through RHN.

### Fedora <a id="fedora" class="anchor">&nbsp;</a> ###

```
# yum install -y clamav clamav-update
```

### Mandriva <a id="mandriva" class="anchor">&nbsp;</a> ###

```
# urpmi clamav clamd
```

### Gentoo <a id="gentoo" class="anchor">&nbsp;</a> ###

```
# emerge clamav
```

See package entry on [Portage].

### openSUSE <a id="opensuse" class="anchor">&nbsp;</a> ###

```
# zypper install -y clamav
```

### FreeBSD, OpenBSD, NetBSD <a id="bsd" class="anchor">&nbsp;</a> ###

Use the ports Luke.

### Solaris <a id="solaris" class="anchor">&nbsp;</a> ###


#### Solaris packages from [OpenCSW] ####

OpenCSW is a community software project for Solaris 8+ on both Sparc and x86. It packages more than 2000 popular open source titles and they can all easily be installed with dependency handling via _pkgutil_ which is modeled after Debian's _apt-get_.

>  # pkgutil -i clamav

More info on [OpenCSW]

### Slackware <a id="slackware" class="anchor">&nbsp;</a> ###

Linuxpackages.net provides third-party precompiled packages for Slackware. You can find them with this search query on that site.

Martijn Dekker provides packages there that provide complete and semi-automatic integration with ClamAV's stock Sendmail package.

### OSX <a id="osx" class="anchor">&nbsp;</a> ###

Various Installation Guides for OSX can be found on the Internet, two that we have seen are:
* http://www.gctv.ne.jp/~yokota/clamav/
* https://gist.github.com/zhurui1008/4fdc875e557014c3a34e


#### How to use ####

Download the package, and as root, install it like so (substituting the appropriate filename):

>  # installpkg clamav-0.91.2-i486-1McD.tgz

To activate Sendmail integration, after installing the package, copy the ‘/usr/share/sendmail/sendmail-slackware-clamav.cf’ file into ‘/etc/mail/sendmail.cf’:

>  # cp /usr/share/sendmail/sendmail-slackware-clamav.cf /etc/mail/sendmail.cf

Then start ClamAV and restart Sendmail:

>  # /etc/rc.d/rc.clamav start

>  # /etc/rc.d/rc.sendmail restart

#### Building your own ####

You may wish to build your own package if I haven't uploaded one with the most recent version yet, if you use a pre-11.0 Slackware version (at the time of this writing, I build on 11.0, 12.0 and 12.1, and my binaries may not work on earlier versions), if you don't trust third-party binaries, or simply because you're a complete geek ;-) . You can download my easy-to-use Slackbuild script, from which the fully-integrated ClamAV packages at Linuxpackages.net are generated.

This script can be used to build a ClamAV package for Slackware 10.0 or higher with Sendmail installed (as Sendmail milter support was introduced as of 10.0). To choose a version of ClamAV to build, you can ‘cd’ to the script's directory and invoke the script like so:

> $ VERSION=1.23.4 ./clamav.SlackBuild

…substituting, of course, the appropriate ClamAV version for ‘1.23.4’. Note: there is no need to be root to use this build script; it will ask for your root password after building the binaries and just before creating the package (and if you have fakeroot installed, even that isn't necessary).

### Windows <a id="windows" class="anchor">&nbsp;</a> ###

#### First update Windows ####

* Microsoft Update

#### Available packages ####

clamAV.msi - base package for clamav, an anti-virus utility for Windows

#### How to install ####

* simple mode: doubleclick the MSI installer package
* command line (displays only a confirmation dialog at the end): msiexec /i clamAV.msi /qr

#### Requirements ####

Microsoft .net version 2.0 is required starting with ClamAV 0.92.1

### OpenVMS <a id="openvms" class="anchor">&nbsp;</a> ###

The ClamAV [for OpenVMS] port is maintained by Alexey Chupahin, Mibok Ltd

Please visit Clamav [OpenVMS project site]

First, you should download latest clamav sources and bzip2 library (if you need bz2 archives support) from the site above. Install process is very similar to one in unix:

>@configure
>
>@build
>
>@clamav$startup

This process provides for you:

* ClamAV library
* clamscan
* freshclam
* clamd
* clamdscan 
* clamconf 
* scripts, allow you to start clamd and freshclam in daemon mode


[my blog]: http://miltonpaiva.wordpress.com/
[OpenCSW]: http://www.opencsw.org
[OpenVMS project site]: http://clamav.dyndns.org/clamav
[for OpenVMS]: http://www.openvms.org/    
[UninstallClamAV]: https://github.com/vrtadmin/clamav-faq/blob/master/faq/faq-uninstall.md
[Which Version]: https://github.com/vrtadmin/clamav-faq/blob/master/faq/faq-whichversion.md
[ClamOverview]: https://github.com/vrtadmin/clamav-faq/blob/master/faq/faq-overview.md
[Community Enterprise Operating System (CentOS)]: http://centos.org/
[Extra Packages for Enterprise Linux (EPEL) repository]: https://fedoraproject.org/wiki/EPEL
[RedHat Enterprise Linux (RHEL)]: http://www.redhat.com/en/technologies/linux-platforms/enterprise-linux
[Portage]: https://packages.gentoo.org/package/app-antivirus/clamav
