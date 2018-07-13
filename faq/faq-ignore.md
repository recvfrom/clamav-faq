# How do I ignore/whitelist a ClamAV signature?

### Creating a ignore/whitelist file

Change Directory into the location where your ClamAV databases are stored.  Create a file called `whitelist.ign2`, for example, like this:

`touch whitelist.ign2`

### Ignore individual signatures

Place the signatures you'd like to ignore, each on it's own line, within the file `whitelist.ign2`.  

For example:

`Signature.Ignore-1`

`Signature.Ignore-2`
