# Uninstalling ClamAV #

## If you installed from source

* _./configure_
* _sudo make uninstall_

##If you installed from packages

* Debian: _dpkg --remove clamav*_
* Redhat/Fedora: _yum remove clamav*_
* Mandriva: _urpme clamav_
* Gentoo: _emerge -C clamav_
* FreeBSD?: _pkg_deinstall -f security/clamav*_
* Slackware: _/etc/rc.d/rc.clamav stop; removepkg clamav_

##Caveats

Make sure that you haven’t got old libraries (_libclamav.so_) lying around your filesystem. You can verify it using: _$ ldd `which freshclam`_
Also make sure there is really only one version of ClamAV installed on your system:

_$ whereis freshclam_
_$ whereis clamscan_
