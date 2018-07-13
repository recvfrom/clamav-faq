# How to Speed Up ClamWin #

*ClamWin* is based off the ClamAV engine. One problem remains: scans are really slow. This is not because of the engine itself. Many AVs, including the big time commercial ones, with full scan features and **no** limits are slow. The bigger a hard drive gets, the longer a scan will take. What is the easiest solution? This is a documentation for adapting Clam scans to a much faster rate. While this article is intended to be for ClamWin, these features can also be used in ClamAV.


## Phase 1: File extensions

ClamAV, by default, will scan all extensions. This is what a full time scanning operation does, however, a quick scan option is different and does not need to go through all that. The term "quick" is the key. Below is a list of extensions only needed to be scanned during a quick time operation and should tackle around 80% - 90% of malware across the web.

Extensions to be scanned during a quick scan operation:

`.exe` - The main source of malware comes from `.exe` files. This is prime to any real-time protection capabilities.

`.dll` - While `.dll` files cannot be accessed without a supplement from a `.exe` file, many malware writers have adapted `.dll` files to be able to work with other malware related techniques from other malware writers. For a pre-caution, it is best to delete these files along with the `.exe` files.

`.src` - You may ask why this extension is on here. These files are used commonly throughout instant messengers, like Steam and Skype. These files are most commonly used to take control of accounts and steal personal information and credit card information.

`.sys` - Yes it is strange, however, malware are making fake system files and hiding them in system directories to infect operating system directories.

`.msi` - This is a more technical installation, similar to `.exe` extension and malware writers have been using this as an alternative to `.exe` extensions.

That is all. These 5 extensions are all that is needed to perform a quick scan operation.


## Phase 2 - File sizes

This is a short description of file sizes. In my 6 years of experience, so far, I have never seen a piece of malware larger then *5 mb*. ClamAV offers a file size limit and allows the user to decide. Most AVs are now just tuning the engine itself to scan small file sizes. To majorly speed up all scans, this is including full system scans as well as quick scans, Clam engine should be adapted to scan no more then 5mb. This will surely make scans 20x faster without effecting detection ratios.


## Phase 3 - File directories

Full system scans are meant to scan all directories, which is good, however, a quick scan option only needs to scan a few. Currently, ClamAV is only capable of scanning the memory for a quick scan option, which is a good start, but the memory is not the only commonly targeted directory. Below is a list of directories that should also be included in a quick scan operation:

Locations to be scanned during a quick scan:

* `Memory` - Malware's number one target is usually the memory. With this, malware can target key system points and have access to most to all system files.

* `Registry` - Malware use registry keys to gain access to certain files on the system. At the same time, malware can rewrite a certain registry key and make any file unresponsive, including AVs.

* `Appdata` - This directory is where malware likes to hide the most. In this process, malware can also have access to all of your configuration files of every program on your system.

* `System32` - This is the second most targeted area on Windows systems. Here, malware can take control of Windows drivers and use this to monitor your activity and personal information.

* `SystemWOW64` - This directory is similar to `System32`, however this is only for 64-bit systems. 64-bit malware target this directory instead of `system32` and can take control of 64-bit systems.


## Phase 4 - Archive scanning (optional)

Archives are commonly used across torrent sites, emails, and file transfers. While, if any malware is inside a archive, it cannot harm a user until the user decides to open the archive. Of course, a user will not know if a archive contains malware, until it is already too late. Here is a collection of muli platform archive extensions that are the most popular:

* `.zip` - The most popular archive format are zip archives. You are more likely not to see this on Linux systems, but thesee are used commonly on Mac and Windows systems.

* `.rar` - rar files are really common on torrent sites. They are fast archives and the most common archive extension used for malware.

* `.7z` - 7-zip is another popular archive format that is used on Linux, Mac, and Windows systems.

* `.cab` - cab is mostly used on Windows systems and belongs in the catagory, commonly used by malware writers.

* `.jar` - jar is a archive written by Java. Most malware researchers know Java is not the best when it comes to security. At the sametime, `.jar` archives are used to spread malware, as well.

## That is all

With these operations, this should make Clam scans up to 20x faster. While ClamAV was only meant to be for Linux systems, 95% of their signatures are for Windows malware. While not everything on here can apply to ClamAV, such as the directory paths, which will vary on Linux and Mac systems, however, ClamAV can still use the file size limits and extensions to benefit the Clam engine. Over 10 million people use the Clam engine, such as *ClamAV*, *ClamTK*, *ClamXav*, *ClamWin*, *Clam Sentinel*, *GPM Clam*, and *amiti*. 

- Written by *Alex Boehm*, moderator of *ClamWin*
