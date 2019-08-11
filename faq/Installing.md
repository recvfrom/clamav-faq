# Installing ClamAV

## Installing from source

For instructions on how to install ClamAV from source, take a look at our [User Manual](https://www.clamav.net/documents/installing-clamav-on-unix-linux-macos-from-source).

---

## Installing From Packages

Installing your distribution's packages is the easiest route. It will make also upgrades easier.

---

### Understand which packages you need

Some distributions parcel up ClamAV components into separate packages. You don't necessarily need all of the packages. If you wish to install the bare minimum, then read the [ClamAV Overview](clamav-overview) carefully to understand which ones you will need.

---

## Operating System Specific Information

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

---

### Debian <a id="debian" class="anchor">&nbsp;</a>

<pre>
  apt-get update
  apt-get install clamav
</pre>

---

### RHEL/CentOS <a id="rhel" class="anchor">&nbsp;</a>

<pre>
  yum install -y epel-release
  yum install -y clamav
</pre>

On [Community Enterprise Operating System (CentOS)] the ClamAV package requires the [Extra Packages for Enterprise Linux (EPEL) repository].

On [RedHat Enterprise Linux (RHEL)] the EPEL release package has to be installed either manually or through RHN.

---

### Fedora <a id="fedora" class="anchor">&nbsp;</a>

<pre>
  yum install -y clamav clamav-update
</pre>

---

### Mandriva <a id="mandriva" class="anchor">&nbsp;</a>

<pre>
  urpmi clamav clamd
</pre>

---

### Gentoo <a id="gentoo" class="anchor">&nbsp;</a>

<pre>
  emerge clamav
</pre>

See package entry on [Portage].

---

### openSUSE <a id="opensuse" class="anchor">&nbsp;</a>

<pre>
  zypper install -y clamav
</pre>

### FreeBSD, OpenBSD, NetBSD <a id="bsd" class="anchor">&nbsp;</a>

Althought all these systems offer the possibility to use ports or pkgsrc, you can install the pre-built package:

* FreeBSD

<pre>
  pkg install clamav
</pre>

* OpenBSD

<pre>
  pkg_add clamav
</pre>

* NetBSD

<pre>
  pkgin install clamav
</pre>

---

### Solaris <a id="solaris" class="anchor">&nbsp;</a>

#### Solaris packages from [OpenCSW]

OpenCSW is a community software project for Solaris 8+ on both Sparc and x86. It packages more than 2000 popular open source titles and they can all easily be installed with dependency handling via _pkgutil_ which is modeled after Debian's _apt-get_.

<pre>
  pkgutil -i clamav
</pre>

More info on [OpenCSW]

---

### Slackware <a id="slackware" class="anchor">&nbsp;</a>

Martijn Dekker provides packages there that provide complete and semi-automatic integration with ClamAV's stock Sendmail package.

---

### macOS <a id="osx" class="anchor">&nbsp;</a>

Various Installation Guides for macOS can be found on the Internet, two that we have seen are:

* [Building ClamAV on macOS]
* [Get ClamAV running on macOS (using Homebrew)]

#### How to use

Download the package, and as root, install it like so (substituting the appropriate filename):

<pre>
  installpkg clamav-0.91.2-i486-1McD.tgz
</pre>

To activate Sendmail integration, after installing the package, copy the `/usr/share/sendmail/sendmail-slackware-clamav.cf` file into `/etc/mail/sendmail.cf`:

<pre>
  cp /usr/share/sendmail/sendmail-slackware-clamav.cf /etc/mail/sendmail.cf
</pre>

Then start ClamAV and restart Sendmail:

<pre>
  /etc/rc.d/rc.clamav start
  /etc/rc.d/rc.sendmail restart
</pre>

#### Building Your Own Package

You may wish to build your own package if I haven't uploaded one with the most recent version yet, if you use a pre-11.0 Slackware version (at the time of this writing, I build on 11.0, 12.0 and 12.1, and my binaries may not work on earlier versions), if you don't trust third-party binaries, or simply because you're a complete geek ;-) . You can download my easy-to-use Slackbuild script, from which the fully-integrated ClamAV packages at Linuxpackages.net are generated.

This script can be used to build a ClamAV package for Slackware 10.0 or higher with Sendmail installed (as Sendmail milter support was introduced as of 10.0). To choose a version of ClamAV to build, you can `cd` to the script's directory and invoke the script like so:

<pre>
  VERSION=1.23.4 ./clamav.SlackBuild
</pre>

…substituting, of course, the appropriate ClamAV version for `1.23.4`. Note: there is no need to be root to use this build script; it will ask for your root password after building the binaries and just before creating the package (and if you have fakeroot installed, even that isn't necessary).

---

### Windows <a id="windows" class="anchor">&nbsp;</a>

#### First update Windows

* Microsoft Update

#### Available Packages

ClamAV builds for Windows users are available [here](https://www.clamav.net/downloads#otherversions)

* `ClamAV-0.101.3.exe` - Traditional executable installer that will install ClamAV in the "Program Files" directory.
* `clamav-0.101.3-rc-win-x64-portable.zip` - Portable install package for 64-bit Windows systems.
* `clamav-0.101.3-rc-win-x86-portable.zip` - Portable install package for 32-bit Windows systems.

#### How to Install

* simple mode: doubleclick the MSI installer package
* command line (displays only a confirmation dialog at the end): `msiexec /i clamAV.msi /qr`

---

### OpenVMS <a id="openvms" class="anchor">&nbsp;</a>

The ClamAV [for OpenVMS] port is maintained by Alexey Chupahin, Mibok Ltd

Please visit ClamAV [OpenVMS project site]

First, you should download latest clamav sources and bzip2 library (if you need bz2 archives support) from the site above. Install process is very similar to one in unix:

<pre>
  @configure
  @build
  @clamav$startup
</pre>

This process provides for you:

* ClamAV library
* clamscan
* freshclam
* clamd
* clamdscan
* clamconf
* scripts, allow you to start clamd and freshclam in daemon mode

[OpenCSW]: https://www.opencsw.org
[OpenVMS project site]: http://clamav.dyndns.org/clamav
[for OpenVMS]: http://www.openvms.org/
[UninstallClamAV]: https://www.clamav.net/documents/uninstalling-clamav
[Which Version]: https://www.clamav.net/documents/which-version-of-clamav-should-i-use
[ClamOverview]: faq-overview.md
[Community Enterprise Operating System (CentOS)]: https://centos.org/
[Extra Packages for Enterprise Linux (EPEL) repository]: https://fedoraproject.org/wiki/EPEL
[RedHat Enterprise Linux (RHEL)]: https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux
[Portage]: https://packages.gentoo.org/package/app-antivirus/clamav
[Building ClamAV on macOS]: http://www.gctv.ne.jp/~yokota/clamav/
[Get ClamAV running on macOS (using Homebrew)]: https://gist.github.com/zhurui1008/4fdc875e557014c3a34e
