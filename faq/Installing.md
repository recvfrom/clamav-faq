# Installing ClamAV #

## Installing from source ##

* Check [Requirements](#requirements)
* Uninstall any old version, see [UninstallClamAV](https://github.com/vrtadmin/clamav-faq/blob/master/faq/faq-uninstall.md) (Note: this isn't essential, but removes sources of problems).
* wget the source gzip file, see [Which Version](https://github.com/vrtadmin/clamav-faq/blob/master/faq/faq-whichversion.md)
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

You don't necessarily need all packages. Please read [ClamOverview](https://github.com/vrtadmin/clamav-faq/blob/master/faq/faq-overview.md) carefully to understand which ones you need.

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

```
# apt-get update
# apt-get install clamav
```

### RHEL/CentOS <a id="rhel" class="anchor">&nbsp;</a> ###

On CentOS:

```
# yum install -y epel-release
# yum install -y clamav
```

On [Community Enterprise Operating System (CentOS)](http://centos.org/) the clamav package requires the [Extra Packages for Enterprise Linux (EPEL) repository](https://fedoraproject.org/wiki/EPEL).

On [RedHat Enterprise Linux (RHEL)](http://www.redhat.com/en/technologies/linux-platforms/enterprise-linux) the EPEL release package has to be installed either manually or through RHN.

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

See package entry on [Portage](https://packages.gentoo.org/package/app-antivirus/clamav).

### openSUSE <a id="opensuse" class="anchor">&nbsp;</a> ###

```
# zypper install -y clamav
```

### FreeBSD, OpenBSD, NetBSD <a id="bsd" class="anchor">&nbsp;</a> ###

Use the ports Luke.

### Solaris <a id="solaris" class="anchor">&nbsp;</a> ###

There are a number of package maintainers for ClamAV on Solaris. The installation method differs for each.

Would you like to download the latest virus pattern definitions during installation ?  (This requires that you have a direct connection to the Internet. If you are behind a proxy server then skip this step.)
  
    
    Update virus patterns? (y/n): y
    
     ## Processing package information.
     ## Processing system information.
     ## Verifying package dependencies.
     ## Verifying disk space requirements.
     ## Checking for conflicts with packages already installed.
     ## Checking for setuid/setgid programs.
    
    This package contains scripts which will be executed with super-user
    permission during the process of installing this package.
    
    Do you want to continue with the installation of <ClamAV> [y,n,?] y
    
    Installing ClamAV 0.92 as <ClamAV>
    
     ## Executing preinstall script.
    Creating group clamav...
    Creating user clamav...
     ## Installing part 1 of 1.
    /lib/svc/method/clamav
    /opt/ClamAV/bin/clamav-config
    /opt/ClamAV/bin/clamconf
    /opt/ClamAV/bin/clamdscan
    /opt/ClamAV/bin/clamscan
    /opt/ClamAV/bin/freshclam
    /opt/ClamAV/bin/sigtool
    /opt/ClamAV/etc/clamd.conf
    /opt/ClamAV/etc/freshclam.conf
    /opt/ClamAV/etc/freshclam.conf.install
    /opt/ClamAV/include/clamav.h
    /opt/ClamAV/lib/libclamav.a
    /opt/ClamAV/lib/libclamav.la
    /opt/ClamAV/lib/libclamav.so <symbolic link>
    /opt/ClamAV/lib/libclamav.so.3 <symbolic link>
    /opt/ClamAV/lib/libclamav.so.3.0.3
    /opt/ClamAV/lib/libclamunrar.a
    /opt/ClamAV/lib/libclamunrar.la
    /opt/ClamAV/lib/libclamunrar.so <symbolic link>
    /opt/ClamAV/lib/libclamunrar.so.3 <symbolic link>
    /opt/ClamAV/lib/libclamunrar.so.3.0.3
    /opt/ClamAV/lib/libclamunrar_iface.a
    /opt/ClamAV/lib/libclamunrar_iface.la
    /opt/ClamAV/lib/libclamunrar_iface.so <symbolic link>
    /opt/ClamAV/lib/libclamunrar_iface.so.3 <symbolic link>
    /opt/ClamAV/lib/libclamunrar_iface.so.3.0.3
    /opt/ClamAV/lib/pkgconfig/libclamav.pc
    /opt/ClamAV/sbin/clamav-milter
    /opt/ClamAV/sbin/clamd
    /opt/ClamAV/share/clamav/daily.inc/COPYING
    /opt/ClamAV/share/clamav/daily.inc/daily.cfg
    /opt/ClamAV/share/clamav/daily.inc/daily.db
    /opt/ClamAV/share/clamav/daily.inc/daily.fp
    /opt/ClamAV/share/clamav/daily.inc/daily.hdb
    /opt/ClamAV/share/clamav/daily.inc/daily.hdu
    /opt/ClamAV/share/clamav/daily.inc/daily.info
    /opt/ClamAV/share/clamav/daily.inc/daily.mdb
    /opt/ClamAV/share/clamav/daily.inc/daily.mdu
    /opt/ClamAV/share/clamav/daily.inc/daily.ndb
    /opt/ClamAV/share/clamav/daily.inc/daily.ndu
    /opt/ClamAV/share/clamav/daily.inc/daily.pdb
    /opt/ClamAV/share/clamav/daily.inc/daily.wdb
    /opt/ClamAV/share/clamav/daily.inc/daily.zmd
    /opt/ClamAV/share/clamav/main.cvd
    /opt/ClamAV/share/clamav/mirrors.dat
    /opt/ClamAV/share/man/man1/clamconf.1
    /opt/ClamAV/share/man/man1/clamdscan.1
    /opt/ClamAV/share/man/man1/clamscan.1
    /opt/ClamAV/share/man/man1/freshclam.1
    /opt/ClamAV/share/man/man1/sigtool.1
    /opt/ClamAV/share/man/man5/clamd.conf.5
    /opt/ClamAV/share/man/man5/freshclam.conf.5
    /opt/ClamAV/share/man/man8/clamav-milter.8
    /opt/ClamAV/share/man/man8/clamd.8
    /var/svc/manifest/network/clamav.xml
    
    [ verifying class <none> ]
    
#### Executing postinstall script:
    
    svccfg: Taking "initial" snapshot for svc:/network/clamav:default.
    svccfg: Taking "last-import" snapshot for svc:/network/clamav:default.
    svccfg: Refreshed svc:/network/clamav:default.
    svccfg: Refreshed svc:/milestone/multi-user:default.
    svccfg: Successful import.
    
     *** Downloading latest virus pattern definitions.
    
    Current working dir is /opt/ClamAV/share/clamav
    Max retries == 3
    ClamAV update process started at Sun Dec 30 20:03:53 2007
    Querying current.cvd.clamav.net
    TTL: 300
    Software version from DNS: 0.92
    main.cvd version from DNS: 45
    main.cvd is up to date (version: 45, sigs: 169676, f-level: 21, builder: sven)
    daily.cvd version from DNS: 5297
    Retrieving http://database.clamav.net/daily.cvd
    Trying to download http://database.clamav.net/daily.cvd (IP: 193.19.98.136)
    Downloading daily.cvd [100%]
    Removing incremental directory daily.inc
    Removing backup directory ./clamav-a1b9834acd3a8a1360172186199f917d
    daily.inc updated (version: 5297, sigs: 14304, f-level: 21, builder: ccordes)
    Database updated (183980 signatures) from database.clamav.net (IP: 193.19.98.136)
    

#### Installation is complete.
    
    You should now review the following configuration files and customise
    them for your environment.
    
     /opt/ClamAV/etc/clamd.conf
     /opt/ClamAV/etc/freshclam.conf
    
    and then the daemons can be started with
    
    svcadm enable clamav
    
    
    For assistance with this package, please email clamav@citrus-it.net
    in the first instance. For general assistance with ClamAV, see
    http://www.clamav.net/ 
    
    Installation of <ClamAV> was successful.
  

####Verify that the ClamAV service has been installed into the SMF database (Solaris 10 only)
  
    # svcs clamav
    STATE          STIME    FMRI
    disabled       20:06:24 svc:/network/clamav:default
    Test the command line scanner
    
     # /opt/ClamAV/bin/clamscan /tmp/ClamAV-s10-0.92 
    /tmp/ClamAV-s10-0.92: OK
    
    ----------- SCAN SUMMARY -----------
    Known viruses: 183980
    Engine version: 0.92
    Scanned directories: 0
    Scanned files: 1
    Infected files: 0
    Data scanned: 19.48 MB
    Time: 13.060 sec (0 m 13 s)
    Configure the daemon scanner and updater
    

Edit the two configuration files in _/opt/ClamAV/etc_ to suit your installation then start the ClamAV services.    

>  # svcadm enable clamav

Instructions courtesy of Andy Fiddaman - 30 Dec 2007

#### Solaris packages from [OpenCSW] ####

OpenCSW is a community software project for Solaris 8+ on both Sparc and x86. It packages more than 2000 popular open source titles and they can all easily be installed with dependency handling via _pkgutil_ which is modeled after Debian's _apt-get_.

>  # pkgutil -i clamav

More info on [OpenCSW]

### Slackware <a id="slackware" class="anchor">&nbsp;</a> ###

Linuxpackages.net provides third-party precompiled packages for Slackware. You can find them with this search query on that site.

Martijn Dekker provides packages there that provide complete and semi-automatic integration with ClamAV's stock Sendmail package.

### OSX <a id="osx" class="anchor">&nbsp;</a> ###

Various Installation Guides for OSX can be found on the Internet, two that we have seen are:
http://www.gctv.ne.jp/~yokota/clamav/
https://gist.github.com/zhurui1008/4fdc875e557014c3a34e


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
