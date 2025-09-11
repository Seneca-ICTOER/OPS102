# File Redirection 

Any of these descriptors/handles may be connected to a different file or
device by adding symbols to the command line.

These are the most commonly-used symbols:

```plain
> file     redirects stdout to the specified file, overwriting any existing content, or creating the file if it does not exist
>>file     redirects stdout to the specified file, appending to existing content, or creating the file if it does not exist
< file     redirects stdin from the specified file
```

Both the \> and \>\> symbols will create the file if it does not exist.
If the file does exist, the \> symbol will overwrite it, while the \>\>
symbol will append to it (add to the end of the file).

Examples on Linux:

```plain
$ date >now      # redirect the output of the date command into the file named "now"
$ cat now        # display the file contents
Tue 26 Sep 2028 01:14:02 PM EDT
$ date >>now     # append the output of the date command into the file "now"
$ cat now        # display the file contents - note that there are two dates
Tue 26 Sep 2028 01:14:02 PM EDT
Tue 26 Sep 2028 01:14:10 PM EDT
$ date >>now     # repeat a third time
$ cat now
Tue 26 Sep 2028 01:14:02 PM EDT
Tue 26 Sep 2028 01:14:10 PM EDT
Tue 26 Sep 2028 01:14:22 PM EDT
$ date >now      # redirect with a single > character - will overwrite
$ cat now        # display the file contents - note the old data was overwritten
Tue 26 Sep 2028 01:14:28 PM EDT
```

The same example on Windows:

```plain
> date /t >now.txt
> type now.txt
2028-09-26 
> date /t >>now.txt 
> type now.txt
2028-09-26 
2028-09-26 
> date /t >>now.txt
> type now.txt
2028-09-26 
2028-09-26 
2028-09-26 
> date /t >now.txt
> type now.txt
2023-09-26 
```

To redirect a different file descriptior/handle, place the
descriptor/handle number in front of the redirection symbol:

```plain
2>file     redirects stderr (2) to the specified file, overwriting
2>>file    redirects stderr (2) to the specified file, appending
```

Examples on Linux:

```plain

$ touch one two       # create the files "one" and "two"
$ rm three            # make sure that no file named "three" exists
rm: cannot remove 'three': No such file or directory
$ ls -l one two three # this should succeed for 2 files, fail for 1 file
ls: cannot access 'three': No such file or directory
-rw-r--r--. 1 chris chris 0 Sep 26 13:17 one
-rw-r--r--. 1 chris chris 0 Sep 26 13:17 two
$ ls -l one two three >listing.txt # redirect output but not errors
ls: cannot access 'three': No such file or directory
$ cat listing.txt     # view the saved output
-rw-r--r--. 1 chris chris 0 Sep 26 13:17 one
-rw-r--r--. 1 chris chris 0 Sep 26 13:17 two
$ ls -l one two three >listing.txt 2>errors.txt # output and errors redirected separately
$ cat listing.txt     # view the saved output
-rw-r--r--. 1 chris chris 0 Sep 26 13:17 one
-rw-r--r--. 1 chris chris 0 Sep 26 13:17 two
$ cat errors.txt      # view the saved error messages
ls: cannot access 'three': No such file or directory
```

To redirect one descriptor/handle to another descriptor/handle, use the
syntax:

```plain
X>&Y
```

Where X is the descriptor/handle you\'re redirecting, and Y is the
target descriptor/handle.

For example, on Linux:

```plain

$ ls -l one two three >all.txt 2>&1 # redirect stdout to all.txt, then redirect stderr to the same place as stdout
$ cat all.txt                       # view the contents of all.txt
ls: cannot access 'three': No such file or directory
-rw-r--r--. 1 chris chris 0 Sep 26 13:17 one
-rw-r--r--. 1 chris chris 0 Sep 26 13:17 two
```

Note that in this example, it is necessary to redirect stdout before
redirecting stderr to the same location.

