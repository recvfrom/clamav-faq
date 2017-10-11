# Win32 FAQ #

* Why is ClamAV for Windows called Immunet now?

Immunet now combines the power of ClamAV and our FireAMP products into one.

* With the acquisition of Immunet by Sourcefire are both teams working together now or are they separate?

Sourcefire has a single dedicated effort to deliver high quality Anti-Malware software.  We are pooling our resources between the ClamAV team and the former Immunet team to provide the best detection coverage and software for all OS’s and platforms we support.

* What is the difference between Immunet, ClamWin, and W32 Clam?

Immunet is a real-time fully featured desktop AV solution.  It contains cloud based detection technologies and the enterprise grade ClamAV detection engine. The product is produced and maintained by Sourcefire which owns both ClamAV and Immunet.  
W32 Clam was the original port of ClamAV to the Windows platform, this code is no longer maintained or needed, as ClamAV supports Windows.  
ClamWin is a free application maintained by ClamWin Pty Ltd., and has no association with ClamAV, Sourcefire, or the Immunet product.  Additionally, ClamWin does not contain an on-access real-time scanner, and can only be used to manually scan files.

* Is Immunet free for commercial use?

Yup, Immunet is free for commercial use. Use it wherever you want to, home, office, servers, education facilities, non-profits, etc, etc. In fact the more places you installed it and the more systems it’s running on, the better its community-based detection will perform.  We do have a [commercial version](http://www.cisco.com/c/en/us/products/security/fireamp-endpoints/index.html) named "AMP for Endpoints" that does FAR more.  If you are interested in deploying this in a commercial environment, we highly suggest checking that out.

* Will Immunet send any sensitive data from my computer to the cloud?

Immunet sends information about the files its scanning back to the cloud. This information is in the form of SHA hashes and file heuristics. Currently, this information is only collected for Windows PE files, or in other terms what most people refer to as executable files. No information is collected for other types of files, like Word, Excel, or PDF. Additionally, in some situations the entire PE file will be uploaded to the Cloud to determine if it is malicious. 
For a complete overview please see the [privacy policy]

* Are you going to make use of the Cloud in the \*nix version of ClamAV?

The simple answer is “yes”.  The complex answer is “when”.  We are currently working on that roadmap and will keep everyone informed as that information becomes available.

* Can I use Immunet with my current AV solution?

Yes. In fact it is encouraged.

* Where should I report false positives or undetected malware?

On ClamAV.net

* Are there 64 bit versions of ClamAV for Windows as well as 32 bit?

Yes.  You can find both versions at [Clamav/downloads]

[privacy policy]: http://www.cisco.com/web/siteassets/legal/privacy.html
[Clamav/downloads]: https://www.clamav.net/downloads#otherversions
