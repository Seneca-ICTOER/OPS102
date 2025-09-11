
# Piping

Piping is a special case of redirection, where the output (stdout) of
one command is connected to the input (stdin) of another command. This
is set up using the vertical-bar (pipe) symbol: *\|* (this may look like
a solid or a dashed vertical line, depending on the terminal font in
use).

For example, on Windows, the output of the *help* command is more than
one screen long. You could pipe the output of the *help* command into
the input of the *more* command to view one screen of text at a time:

```plain
> help|more
For more information on a specific command, type HELP command-name
ASSOC          Displays or modifies file extension associations.
ATTRIB         Displays or changes file attributes.
BREAK          Sets or clears extended CTRL+C checking.
BCDEDIT        Sets properties in boot database to control boot loading.        
CACLS          Displays or modifies access control lists (ACLs) of files.       
CALL           Calls one batch program from another.
CD             Displays the name of or changes the current directory.
CHCP           Displays or sets the active code page number.
CHDIR          Displays the name of or changes the current directory.
CHKDSK         Checks a disk and displays a status report.
CHKNTFS        Displays or modifies the checking of disk at boot time.
CLS            Clears the screen.
CMD            Starts a new instance of the Windows command interpreter.        
COLOR          Sets the default console foreground and background colors.       
COMP           Compares the contents of two files or sets of files.
COMPACT        Displays or alters the compression of files on NTFS partitions.  
CONVERT        Converts FAT volumes to NTFS.  You cannot convert the
              current drive.
-- More  --
```

Press the ENTER key to scroll by one line, the spacebar to scroll by one
screen, or \"q\" to quit.

Similarly, on Linux, a long directory listing could be redirected to
*more*, or better yet, the improved *less* command:

```plain
$ ls -l /etc | less
total 2160
drwxr-xr-x.  3 root root     4096 Jun 29 20:00 abrt
-rw-r--r--.  1 root root       18 May 30 03:03 adjtime
-rw-r--r--.  1 root root     1529 Nov 27  2022 aliases
drwxr-xr-x.  2 root root     4096 May 30 09:32 alliance
drwxr-xr-x.  3 root root     4096 Sep  3 20:00 alsa
drwxr-xr-x.  2 root root     4096 Aug  9 09:01 alternatives
drwxr-xr-x.  4 root root     4096 Apr 13 17:47 anaconda
-rw-r--r--.  1 root root      541 Jan 18  2023 anacrontab
-rw-r--r--.  1 root root      269 Jan 17  2023 anthy-unicode.conf
-rw-r--r--.  1 root root      833 Feb 10  2023 appstream.conf
-rw-r--r--.  1 root root       55 Sep  3 20:00 asound.conf
-rw-r--r--.  1 root root        1 Jan 17  2023 at.deny
drwxr-x---.  4 root root     4096 Aug  5 20:00 audit
drwxr-xr-x.  3 root root     4096 May 30 03:03 authselect
drwxr-xr-x.  4 root root     4096 Mar 18  2023 avahi
drwxr-xr-x.  2 root root     4096 May 30 09:33 avrdude
drwxr-xr-x.  2 root root     4096 Aug  8 10:57 bash_completion.d
-rw-r--r--.  1 root root     2638 Nov 27  2022 bashrc
-rw-r--r--.  1 root root      535 Aug  6 20:00 bindresvport.blacklist
drwxr-xr-x.  2 root root     4096 Sep 17 20:00 binfmt.d
drwxr-xr-x.  2 root root     4096 Aug 24 20:00 bluetooth
drwxr-xr-x.  2 root root     4096 May 30 09:32 bonobo-activation

:   
```

Like *more*, you can press ENTER to scroll by one line or SPACE to
scroll by one screen, or \"q\" to quit; but you can also use the up/down
arrow keys, or the PgUp/PgDn keys, to scroll in either direction by one
line or one screen.

On Windows, to see the *help* lines that mention color, you could feed
the output of the *help* command into the *find* command:

```plain
> help | find /i "color"
COLOR          Sets the default console foreground and background colors.
```

You can accomplish complex tasks by connecting a series of simple
commands together using pipes. For example, the Linux *ls -l* command
displays permissions in the second through tenth columns of output. You
could pipe the output of this command through *cut* and cut out just
those columns:

```plain
$ ls -l
total 0
dr-xr-xr-x. 2 chris chris 100 Sep 26 14:22 apple
-rw-r--r--. 1 chris chris   0 Sep 26 14:22 one
-rw-r--r--. 1 chris chris   0 Sep 26 14:22 orange
-rw-r--r--. 1 chris chris   0 Sep 26 14:22 plum
-rw-r--r--. 1 chris chris   0 Sep 26 14:22 three
-rw-r--r--. 1 chris chris   0 Sep 26 14:22 two
$ ls -l | cut -c 2-10
otal 0
r-xr-xr-x
rw-r--r--
rw-r--r--
rw-r--r--
rw-r--r--
rw-r--r--
```

However, this displays the \"total \...\" line at the top of the output,
missing the \"t\" letter in the first column. We can eliminate this with
the command *tail -n +2* which will give us the last part of the output
starting at line 2 (therefore skipping the first line):

```plain
$ ls -l | cut -c 2-10 | tail -n +2
r-xr-xr-x
rw-r--r--
rw-r--r--
rw-r--r--
rw-r--r--
rw-r--r--
```

If we wanted to see the filenames displayed alongside the permissions,
we could take the output of *ls -l*, eliminate the first line (with
*tail* as above), squeeze out multiple consecutive spaces so that they
become a single space using *tr -s \" \"*, then use *cut -d \" \" -f
1,9* to separate each line into fields delimited by the space (\" \")
character, selecting just fields 1 and 9:

```plain
$ ls -l | tail -n +2 | tr -s " " | cut -d " " -f 1,9
dr-xr-xr-x. apple
-rw-r--r--. one
-rw-r--r--. orange
-rw-r--r--. plum
-rw-r--r--. three
-rw-r--r--. two
```

However, this displays an extra character in front of the file
permission mode, and another extra character after the file permission
mode (.), which can be eliminated by selecting the columns with another
*cut* command:

```plain
$ ls -l | tail -n +2 | tr -s " " | cut -d " " -f 1,9 | cut -c2-10,12-
r-xr-xr-x apple
rw-r--r-- one
rw-r--r-- orange
rw-r--r-- plum
rw-r--r-- three
rw-r--r-- two
```
