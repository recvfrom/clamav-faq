# Uninstalling ClamAV #

## If you installed from source

```bash
./configure
sudo make uninstall
```

## If you installed from packages

* Debian: 

  ```bash
  dpkg --remove clamav*
  ```

* Redhat/Fedora: 

  ```bash
  yum remove clamav*
  ```

* Mandriva: 

  ```bash
  urpme clamav
  ```

* Gentoo: 

  ```bash
  emerge -C clamav
  ```

* FreeBSD?: 

  ```bash
  pkg_deinstall -f security/clamav*
  ```

* Slackware: 

  ```bash
  /etc/rc.d/rc.clamav stop; removepkg clamav
  ```

## Caveats

Make sure that you haven’t got old libraries (_libclamav.so_) lying around your filesystem. You can verify it using: _

```bash
$ ldd `which freshclam`
```

Also make sure there is really only one version of ClamAV installed on your system:

```bash
$ whereis freshclam
$ whereis clamscan
```
