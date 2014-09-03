#How to Report A Bug#

If you find a bug in ClamAV, please check it against the latest git code. Read the instructions below, then visit our <a href="https://bugzilla.clamav.net/" target="_blank">bug tracker</a> to submit your bug report. Please do not submit bugs for third party software.

##Required Information##
Please be sure to include all of the following information so that we can effectively address your bug:

+ __E-mail address :__  a working email address so the developers can get in touch with you to obtain additional info and notify you when the problem is fixed.
+ __ClamAV version and settings :__ the output from: <code>clamconf -n</code>
+ __3rd party signatures :__ whether you are using any unofficial signature databases, that is anything other than main.cvd/cld and daily.cvd/cld
+ __System details :__ full specs of your system: i.e. output from: <code>uname -mrsp</code>
+ __Library versions :__ your libc and possibly zlib versions
+ __How to reproduce the problem :__ if the issue is reproducible only when scanning a specific file, attach it to the message. Don’t forget to encrypt it or you may cause damage to the mail servers between you and us! E.g.: <code>zip -P virus -e file.zip file.ext</code>.<br>The content of the file will be kept confidential.

####Large Files###
If the file is too big to mail it, you can upload it to a password protected website and send us the URL and the credentials to access it.

##Backtrace Instructions##
Backtrace of clamscan: if possible, please send us the backtrace obtained from gdb, the GNU Project Debugger.  
Here are step by step instructions which will guide you through the process.
__Assuming you get something like:__	<code>$ clamscan --some-options some_file</code> <code>Segmentation fault</code>

1. Have the kernel write a core dump. <br> For bourne-like shells (e.g. bash): <br>	<code>$ ulimit -c unlimited</code><br>For C-like shells (e.g. tcsh): <br><code>limit coredumpsize unlimited</code>
1. Now you should see the core dumped message:<br><code>$ clamscan --some-options some_file</code><br><code>Segmentation fault (core dumped)</code><br>Looking at your current working directory should reveal a file named core.
1. Load the core file into gdb:<br><code>$ gdb -core=core --args clamscan --some-options some_file</code><br><code>(gdb)</code>. <br>You should now see the gdb prompt.
1. Just use the <code>bt</code> command at the prompt to make gdb print a full backtrace.<br>Copy and paste it into the bug report. You can use the q command to leave gdb.

##Obtain a Backtrace of clamd:##

Use ps to get the PID of clamd (first number from the left):  
<code>$ ps -aux (or ps -elf on SysV)</code>  
clamav 24897 0.0 1.9 38032 10068 ? S Jan13 0:00 clamd  
  
Attach gdb to the running process:  
<code>$ gdb /usr/sbin/clamd 24897</code>  
Replace 24897 with the pid of clamd and adjust the path of clamd.

You should now get the gdb prompt, as:  
<code>(gdb)</code>  
If you want clamd to continue running (i.e. until a segmentation fault occurs), issue the  
<code>continue gdb</code>  
command, and __wait for an error__, at which point gdb will return to its prompt.  

####Commands####

+ <code>bt</code>  will give a backtrace for the current thread.
+ <code>info threads</code> 	will tell you how many threads there are.  
+ <code>thread n</code>  will change to the specified thread, after which you can use the bt command again to get it’s backtrace.  

So, you basically want to use <code>Info threads</code> to get the number of threads and their id numbers; and for each thread do <code>thread id_number</code>; then <code>bt</code>. Exit from gdb with the <code>quit</code> command. Reply <code>y</code> to the question about the program still running.

####Strace####
Optionally, if you think it can help, the output from strace can be included in the report (not covered here).