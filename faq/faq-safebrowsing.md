# Safebrowsing  #

CURRENT STATUS at October 2020.

The safebrowsing feature has now been spun off into a related project.
It requires substantially more effort to implement safebrowsing than
simply enabling the relevant freshclam.conf configuration option.

Briefly, tools are needed to

1. Download the data from Google to a local mysql database using
Google's API [*];

2. produce a local copy of the safebrowsing database file in a form
suitable for use by the ClamAV tools;

3. distribute this database file to the systems which need it; and

4. optionally notify any clamd daemons of the change.

[*] For efficiency, the API permits downloading differences, in much
the same way that ClamAV itself uses .cdiff files.

Documentation can be found at

https://github.com/Cisco-Talos/clamav-safebrowsing


HISTORY

ClamAV 0.95 introduced support for the Google Safe Browsing database.

For use with ClamAV a copy of the database was packed inside the file
"safebrowsing.cvd" which was distributed in the same way as the other
ClamAV database files via the ClamAV mirror network.  Downloading the
database was disabled by default, and the feature was to be enabled
only with extreme caution.  In order to enable this feature it was
necessary to add the option `SafeBrowsing Yes` to freshclam.conf.
This would tell freshclam to download the safebrowsing.cvd database,
and when ClamAV found the database in the database directory it would
enable the safe browsing feature. To turn it off it was necessary to
remove the configuration option from freshclam.conf AND to remove the
safebrowsing files from the database directory.  If clamd was running
it was necessary to restart it.

Updates to the safebrowsing.cvd database were discontinued in 2019 and
it was declared obsolete.
