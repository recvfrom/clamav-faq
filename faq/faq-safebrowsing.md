# Safebrowsing

__ClamAV 0.95__ introduced support for __Google Safe Browsing database__.

The Safebrowsing database is packed inside a CVD file and distributed through our mirror network.
This feature is disabled by default on all installations and should be enabled with **extreme** care.

All signatures provided by Google Safe Browsing Database will be prefixed with the _Safebrowsing_ tag. If ClamAV reports `Safebrowsing.<something> FOUND`, it means that the advisory was provided by Google and not by ClamAV Virus database.

Please note that such reports DO NOT necessarily mean that the data scanned contains some malware. You should treat such data as a _potential_ risk, that is a _suspicious_ source of malware.

If you want to know more about the potentially dangerous data matched by the signature, you should visit [http://www.antiphishing.org](http://www.antiphishing.org/) (for phishing warnings) or [http://www.stopbadware.org](http://www.stopbadware.org/) (for malware warnings).

In order to enable this feature, you must add `SafeBrowsing Yes` to `freshclam.conf`.

There is no option in `clamd.conf`. If the engine finds Google Safe Browsing files in the database directory, ClamAV will enable safe browsing. To turn it off you need to update freshclam.conf and remove the safebrowsing files from the database directory before restarting clamd.
