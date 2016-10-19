 # How do I ignore/whitelist a ClamAV signature?

* Creating a ignore/whitelist file
>Change Directory into the location where your ClamAV databases are stored.  Create a file called "whitelist.ign2", for example, like this:

><code>touch whitelist.ign2</code>

* Ignore individual signatures
> Place the signatures you'd like to ignore, each in it's own line, within the file whitelist.ign2.  
> For example:

><code>Signature.Ignore-1</code>
>
><code>Signature.Ignore-2</code>
