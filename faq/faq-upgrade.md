 How To Upgrade ClamAV

### ClamAV from Packages

If you installed from a package, we suggest you find the approve package from your distro provider and install that. The ClamAV team does not maintain individual packages for every distribution build.
If there are no new packages, you have three options:

* Wait
* Build Clam Package
* Install From Source

### ClamAV from Sources

If you installed from sources, first uninstall the old version:

`./configure`
`sudo make uninstall`

Compile and install the new one: see [Installing ClamAV]

Depending on your installation method, you might want to backup configuration (located in _/usr/local/etc_ by default) and signature database (located in _/usr/local/share/clamav_ by default). Don't forget to restore backups before starting up updated ClamAV.

Backup your database signature (located in _/usr/local/share/clamav_ by default) before upgrading to newer ClamAV version. Restore the backed up database signature before running the updated version. This is to avoid getting the _/usr/local/share/clamav not locked_ error message when doing _freshclam_.

### Webmin and yum

To obtain a new version:

`yum list clamav`

`yum update clamav` (if everything updated properly, run freshclam)

* What does _WARNING:	Current functionality level = 1, required = 2_ mean?

The _functionality level_ of the database determines which scanner engine version is required to use all of its signatures. If you don't upgrade immediately you will be missing the latest viruses.

* What does _Your ClamAV installation is OUTDATED_ mean?

You'll get this message whenever a new version of ClamAV is released.  In order to detect all the latest viruses, it's not enough to keep your database up to date. You also need to run the latest version of the scanner. You can download the [sources] of the latest release from our website. If you are afraid to break something while upgrading, use  the [precompiled packages] for your operating system/distribution.  Remember: running the latest stable release also improves stability.

* I upgraded to the latest stable version but I still get the message _Your ClamAV installation is OUTDATED_, why?

Make sure there is really only one version of ClamAV installed on your system: 
   `$ whereis freshclam` 
   `$ whereis clamscan`

Also make sure that you haven't got old libraries (`libclamav.so*`) lying around your filesystem. You can verify it using: `$ ldd $(which freshclam)`

* What does _Malformed hexstring: This ClamAV version has reached End of Life_ mean?

Please refer to: [eol-clamav-096]

* How do I verify the integrity of ClamAV sources?

Using [GnuPG] you can easily verify the authenticity of your stable release downloads by using the following method: Download the [Sourcefire VRT key] from the VRT labs site. Import the key into your local public keyring: `$ gpg --import vrt.gpg`.  
 
Download the stable release AND the corresponding `.sig` file to the same directory. Verify that the stable release download is signed with the [Sourcefire VRT key]: `$ gpg --verify clamav-X.XX.tar.gz.sig`  

Please note that the resulting output should look like the following:

`gpg: Signature made <some date> using DSA key ID 15497F03`    
`gpg: Good signature from Sourcefire VRT <email address>`  

For other PGP implementation, please refer to their manual.

* Where can I get the latest GIT snapshot of ClamAV?

Visit the [source download page].

* Is my compiler/hardware/operating system supported by ClamAV?

ClamAV supports a wide variety of compilers, hardware and operating systems. Our core compiler is gcc with Linux on 32 and 64 bit Intel platforms, though we also test using other compilers, including Sun's C compiler, Microsoft's Visual Studio, Intel's C compiler, LLVM-GCC, and others. To date we have only found one compiler that we do not support, GCC version 4.0.0 to 4.0.1 inclusive. We have found that version of the compiler produces incorrect code on all of the platforms and operating systems on which we have tested it. ClamAV will not work using that compiler and you MUST switch to an alternative, such as GCC3.4 or GCC4.1.   

Please contact your vendor for further information. Please refer to [gcc's bugzilla] for further information. If you want to see a proof of why gcc 4.0.1 generates wrong code for the kernel read the [relevant article] on kerneltrap. More information about this bug is also available in [our bugzilla].   

Our configure scripts will detect if your compiler is affected by this bug and refuse to generate a non working binary with the following error message: _your compiler has gcc PR26763-2 bug, use a different compiler_ . If you are on MacOS X, you can try an alternative compiler, LLVM-GCC4.2-2.2, which has [official binaries available]


[eol-clamav-096]: http://blog.clamav.net/2014/07/clamav-096-engine-end-of-life.html 
[GnuPG]:http://www.gnupg.org/
[sources]: http://sourceforge.net/projects/clamav/files/
[Wiki](Upgrading.md)
[precompiled packages]: http://www.clamav.net/download.html#otherversions 
[Sourcefire VRT key]: http://labs.snort.org/contact.html
[source download page]: http://www.clamav.net/download.html 
[gcc's bugzilla]: https://gcc.gnu.org/bugzilla/show_bug.cgi?id=26763
[gcc's Options That Control Optimization]: https://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html
[our bugzilla]: https://bugzilla.clamav.net/show_bug.cgi?id=613 
[official binaries available]: http://llvm.org/releases/download.html#2.2
[Installing ClamAV]: ../faq/Installing.md
