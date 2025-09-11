# Linux File Permissions 

Unix-like operating systems, such as Linux, provide a simple model for
maintaining file and directory permissions. There is a more advanced
model available, called File Access Control Lists (File ACLs or FACLs -
see below), but it is more complicated to manage, and experience has
shown that the simpler model is more likely to be used.

## Permission Communities 

There are three **communities** of users for each file:

**User** -- the one user that owns the file

**Group** -- the group of users that owns the file

**Other** -- every other user of the computer system

These communitities are presented in this order, so remember the
sequence!: User - Group - Other (u g o)

Note that each file has both an individual user and a group owner. The
*ls -l* command shows the user and group owner in the third and fourth
columns of output.

## Permissions 

Each community has three \*\*permissions\*\* for each file which may be
individually turned *on* or *off*:

**Read** -- the ability to read a file.

**Write** -- the ability to write to the file, including permission to 
add to, change, or truncate (shorten) the file.

**eXecute** -- the ability to run (execute) a file.

Remember this sequence also!: Read - Write - eXecute (r w x)

When applied to directories, these permissions are interpreted
differently:

**Read** -- the ability to *see* the names of the files and subdirectories 
within the directory. This is also called "search" permission.

**Write** -- the ability to create/delete/rename files and subdirectories 
within the directory.

**eXecute** (**access**) -- the ability to access files with the directory. 
If turned off, the files cannot be accessed, and metadata about each file 
(such as the owner, group owner, file length, permissions, and timestamps) 
cannot be accessed either. You can think of this as **access** permission 
when applied to directories. This is sometimes called *passthrough* 
permission.

If execute permission is enabled for a directory but read permission has
not been enabled, the affected community cannot view a directory listing
to determine filenames, but if they know the name of a file within that
directory, they may still access it.

If read permission is enabled for a directory but execute permission has
not been enabled, the affected community can view the names of files in
a directory (but only the names, not permissions, file size, ownership,
or any other information), but they will have no access to use the files
in any way.

However, read and execute permission are almost always assigned to a
directory together.

In order to access a file, a user must have execute permission on
\_\_all\_\_ of the directories from the root directory to the directory
containing the file. For example, on the file
*/home/jdoe/ops102/practice/info.txt*, a user must have execute
permission on all four directories (home, jdoe, ops102, practice) to
access the file.

## Viewing Permissions 

Permissions may be viewed with the *ls -l* command (the *ls* command
with the *-l* \"long detailed listing\" option). For example:

```plain
$ ls -l /etc/hosts
-rw-r--r--. 1 root root 386 Nov 27  2022 /etc/hosts
```

Notice that the file\'s owner is \"root\", and the file\'s group owner
is also \"root\".

The first character on this line is the file type (\"-\" meaning a
regular file), and the next nine characters represent the three
communities, each having three permissions. The permissions are written
as a letter \-- \"r\", \"w\", or \"x\" \-- if the permission is enabled,
or a dash \"-\" if the permission is disabled. Therefore, in the example
above:

```plain
rw-   the user who owns the file has read and write permission
r--   the group that owns the file has read permission
r--   others have read permission
```

Note that the user who owns the file is listed as *root* and the group
that owns the file is listed as *root* \-- these are not the same! The
user account and group happen to have the same name in this case.

To view the permisions on a directory, you may need to specify the *-d*
option to the *ls* command, which causes it to display the specified
directory instead of the *contents* of that directory. For example:

```plain
$ ls -l /     # displays the contents of the root directory
total 68
dr-xr-xr-x.   2 root root  4096 Jan 18  2023 afs
lrwxrwxrwx.   1 root root     7 Jan 18  2023 bin -> usr/bin
dr-xr-xr-x.   6 root root  4096 Sep 15 22:56 boot
drwxr-xr-x.  23 root root  4860 Sep 26 10:41 dev
drwxr-xr-x. 178 root root 12288 Sep 26 09:42 etc
drwxr-xr-x.   5 root root  4096 May 30 14:27 home
lrwxrwxrwx.   1 root root     7 Jan 18  2023 lib -> usr/lib
lrwxrwxrwx.   1 root root     9 Jan 18  2023 lib64 -> usr/lib64
drwx------.   2 root root 16384 Apr 13 17:42 lost+found
drwxr-xr-x.   2 root root  4096 Jan 18  2023 media
drwxr-xr-x.   5 root root  4096 Jun 14 10:45 mnt
drwxr-xr-x.   5 root root  4096 Sep  6 10:09 opt
dr-xr-xr-x. 489 root root     0 Sep 26 06:26 proc
dr-xr-x---.  10 root root  4096 Sep 25 05:31 root
drwxr-xr-x.  56 root root  1480 Sep 26 10:28 run
lrwxrwxrwx.   1 root root     8 Jan 18  2023 sbin -> usr/sbin
drwxr-xr-x.   2 root root  4096 Jan 18  2023 srv
dr-xr-xr-x.  13 root root     0 Sep 26 10:26 sys
drwxrwxrwt.  25 root root   580 Sep 26 10:51 tmp
drwxr-xr-x.  13 root root  4096 May 30 09:33 usr
drwxr-xr-x.  21 root root  4096 May 30 12:46 var
$ ls -l -d /      # displays the root directory itself
dr-xr-xr-x. 19 root root 4096 Sep  4 15:05 /
```

You can also view permissions as an [octal
number](#using_numeric_mode "wikilink") using the *stat* command - note
the value marked \"Access\":

```plain
$ stat /etc/hosts

File: /etc/hosts
Size: 386         Blocks: 8          IO Block: 4096   regular file

Device: 253,0 Inode: 4194708 Links: 1 Access: (0644/-rw-r\--r\--) Uid: (
0/ root) Gid: ( 0/ root) Context: system_u:object_r:net_conf_t:s0
Access: 2024-01-23 16:29:33.807860342 -0500 Modify: 2022-11-27
10:26:24.000000000 -0500 Change: 2023-05-30 03:00:51.739043061 -0400

Birth: 2023-05-30 03:00:51.738043061 -0400
```

## Setting Permissions 

The permissions on a file are also called the permission *mode* of the
file, so the command to change the permissions is called *chmod*
(\"change mode\").

The *chmod* command can be used in either of two ways: with symbolic or
numeric permissions.

In either case, the command accepts the mode as the first positional
argument, and the filename(s) (or patterns) as the remaining positional
arguments:

~~~plain
chmod mode filename...
~~~

### Using Symbolic Mode 

Symbolic mode represents permissions as a list of one or more
communities, represented by a letter:

```plain
u (user)
g (group)
o (other)
a (all - a short form to specify ugo)
```

This is followed by an action symbol:

```plain
+ (add permissions)
- (remove permissions)
= (set permissions)
```

The difference between +/- and = is that +/- will add or remove the
specified permissions while leaving other permissions unchanged, while =
will explicitly set the permissions to exactly the value specified.

This is followed by zero or more of these letters, representing
permissions:

```plain
r (read)`\
w (write)`\
x (execute - note that this is lowercase)`\
X (execute if applied to a directory, or nothing if applied to a file 
   -- note that this is UPPERCASE)
```

Therefore the symbolic notation *g+rx* instructs chmod to add read and
execute permission to the group community, and *a-w* instructs chmod to
remote write permission from all of the communities (user, group, and
other).

Here is an example:

```plain
$ touch test001   # create a file for testing
$ ls -l test001   # show the current permissions
-rw-r--r--. 1 chris chris 0 Sep 26 11:20 test001
$ chmod g+w test001     # to group, add (+) write permission
$ ls -l test001
-rw-rw-r--. 1 chris chris 0 Sep 26 11:20 test001
$ chmod o-r test001     # to other, remove (-) read permission
$ ls -l test001
-rw-rw----. 1 chris chris 0 Sep 26 11:20 test001
$ chmod u=rw,go= test001 # set user to have only read and write, group and other to have nothing
$ ls -l test001
-rw-------. 1 chris chris 0 Sep 26 11:20 test001
```

And another example using a directory:

```plain
$ mkdir apple              # create a directory for testing
$ touch apple/honeycrisp   # create some files in that directory
$ touch apple/gala
$ touch apple/ambrosia
$ ls -l -d apple           # see the permissions on the directory
drwxr-xr-x. 2 chris chris 100 Sep 26 11:26 apple
$ ls -l apple              # see the files
total 0
-rw-r--r--. 1 chris chris 0 Sep 26 11:26 ambrosia
-rw-r--r--. 1 chris chris 0 Sep 26 11:25 gala
-rw-r--r--. 1 chris chris 0 Sep 26 11:25 honeycrisp
$ chmod a=rx apple         # set permission (for all) to read and execute only
$ ls -l -d apple
dr-xr-xr-x. 2 chris chris 100 Sep 26 11:26 apple
$ ls -l apple              # note that we can still see inside the directory
total 0
-rw-r--r--. 1 chris chris 0 Sep 26 11:26 ambrosia
-rw-r--r--. 1 chris chris 0 Sep 26 11:25 gala
-rw-r--r--. 1 chris chris 0 Sep 26 11:25 honeycrisp
$ touch apple/macintosh    # we cannot create a file in the directory
touch: cannot touch 'apple/macintosh': Permission denied
$ mv apple/gala apple/fuji # we cannot rename a file 
mv: cannot move 'apple/gala' to 'apple/fuji': Permission denied
$ rm apple/gala            # we cannot remove a file
rm: cannot remove 'apple/gala': Permission denied
$ chmod a=r apple          # set permission to read only
$ ls -l -d apple
dr--r--r--. 2 chris chris 100 Sep 26 11:26 apple
$ ls -l apple              # we can see the filenames (r) but not the details (x)
ls: cannot access 'apple/ambrosia': Permission denied
ls: cannot access 'apple/gala': Permission denied
ls: cannot access 'apple/honeycrisp': Permission denied
total 0
-????????? ? ? ? ?            ? ambrosia
-????????? ? ? ? ?            ? gala
-????????? ? ? ? ?            ? honeycrisp
$ cat apple/ambrosia        # we cannot access any files in that directory (x)
cat: apple/ambrosia: Permission denied
$ chmod a=x apple           # set permission to execute (passthrough) only
$ ls -l -d apple
d--x--x--x. 2 chris chris 100 Sep 26 11:26 apple
$ ls -l apple               # we cannot see the list of files in that directory
ls: cannot open directory 'apple': Permission denied
$ ls -l apple/gala          # however, if we know the exact name of the file, we can view it
-rw-r--r--. 1 chris chris 0 Sep 26 11:25 apple/gala

```

### Using Numeric Mode 

You can also specify a mode using a number. Each digit has a range of 0
to 7, so these are known as *octal* (base eight) numbers. An extra
zero is often written in front of the number to indicate that the number
is in octal.

When a numeric value is used to specify the permission mode, all of the
permissions for all of the communities must be set at the same time. You
cannot add or remove some permissions, or set permission for just some
of the communities, as you can with symbolic mode.

The digits are written from left-to-right in the order of the
communities (u g o), with each digit being the sum of the granted
permission according to these values:

```plain
4 read
2 write
1 execute
```

Examples:

~~~plain
rwx would have a value of 7 (4+2+1)
rw- would have a value of 6 (4+2)
r-- would have a value of 4 (4)
~~~

Therefore these permissions are equivalent:

```plain
rwxrw-r-- 0764
rwxrwxrwx 0777
rw-r--r-- 0744
rwx--x--x 0711
```

Here are some examples of *chmod* commands with numeric modes:

```plain
$ touch example001
$ ls -l example001
-rw-r--r--. 1 chris chris 0 Sep 26 11:45 example001
$ chmod 0111 example001
$ ls -l example001
---x--x--x. 1 chris chris 0 Sep 26 11:45 example001
$ chmod 0764 example001
$ ls -l example001
-rwxrw-r--. 1 chris chris 0 Sep 26 11:45 example001
$ chmod 0640 example001
$ ls -l example001
-rw-r-----. 1 chris chris 0 Sep 26 11:45 example001
```

### Recursively Setting Permissions 

It is sometimes useful to use the chmod *-R* option to recursively set
all the permissions on a directory and all of its contents. However, it
is quite common to need to set execute permissions on directories but
not on files. You can indicate this to *chmod* using a capital X for the
execute permission.

~~~plain
# Don't do this! It will set Execute permission on files and directories.
chmod -R go+rx publicdir

# Instead, do this to set Execute permission on directories only (not files):
# (Notice the capital X in the symbolic permissions)
chmod -R go+rX publicdir
~~~

### Other useful chmod Options 

```plain
-v    Verbose: show information about each file processed (changed or not)
-c    Changes: show information about each change made (only changed files)
```

## Controlling Permissions on New Files and Directories 

There is a setting known as *umask* which controls the permissions
assigned to new files and directories. The umask value is a numeric mode
which represents the permissions which are *not* permitted on new
files.

The actual permission which is given to new files is a combination of
two values:

- The mode requested by the software creating the file 
(using the open, openat, or creat system calls), 
except for

- The modes prohibited by the umask value.

For example, a umask value of 0022 represents the permissions
*\-\-\--w\--w-* (write permission for group and other). Therefore, any
new files or directories will be created *without* these permissions.
This is the default permission on Matrix.

The umask value can be viewed or set with the *umask* command.

For example, the *touch* command requests 0666 (*rw-rw-rw-*) permission
on new files. Here is a demo of how the umask value can change the
assigned permissions:

```plain
$ umask                # view the current umask
0022
$ touch testfile0022   # umask of 0022 will deny write for group and other
$ ls -l testfile0022
-rw-r--r--. 1 chris chris 0 Sep 26 11:54 testfile0022
$ umask 0000    # umask of 0000 will not deny any permissions
$ touch testfile0000
$ ls -l testfile0000
-rw-rw-rw-. 1 chris chris 0 Sep 26 11:54 testfile0000
$ umask 0027    # deny group write, plus all permissions for other
$ touch testfile0027
$ ls -l testfile0027
-rw-r-----. 1 chris chris 0 Sep 26 11:55 testfile0027
```

To ensure that no one else has _any_ access to new files and
directories that you create on Matrix (unless you change the permission
mode of the file after it is created), set your umask to 0077: *umask
0077*

Note that the umask value is specific to the process that is currently
running, and it inherited by child processes. That means that if you\'re
using multiple shells (perhaps in multiple windows), each shell\'s umask
value is specific to that shell, and changing it will not affect the
other active shells. However, any command or program that you run from
that shell will inherit the umask value. You can set the default umask
value for all future bash sessions by placing a umask command into your
*\~/.bashrc* file.

-  Warning: be **extremely** careful editing your
        *\~/.bashrc* file, since an error may prevent you from logging
        in to your Matrix account. Always stay logged in to Matrix on
        one terminal while using a second terminal to confirm that you
        are able to successfully log in to the system. If you are not
        able to login, fix the problem using the first terminal and then
        re-test.

## Special Permissions 

(Note that this is an advanced topic - these permissions are not used on
the majority of files).

There are three additional, \"special\" permissions:

**Set User ID (SUID)** - when applied to an executable program file, this 
permission changes the effective user ID from the user executing the 
file to the owner of the file for the duration of the process. For example, 
if a user `*`jdoe`*` executes the `*`passwd`*` command (which is owned by 
the `*`root`*` user and has the Set User ID permission enabled), the 
effective user ID is temporarily changed to `*`root`*` while that 
command is executing. This enables the `*`passwd`*` command to change 
the user's password in the `*`/etc/shadow`*` file, which they otherwise 
do not have access to.

**Set Group ID (SGID)** - when applied to an executable program file, this 
permission is similar to SUID, but it changes the effective group ID 
instead of the effective user ID. When applied to a directory, this 
causes all newly-created files and directories with that directory to 
be owned by the same group that owns the directory. For example, if the 
directory `*`/var/www/html/`*` is owned by the group `*`website`*`, then 
any file or directory created within `*`/var/www/html/`*` will automatically
be owned by the group `*`website`*` instead of the group of the person 
creating the file.

**Sticky bit (t)** - when applied to a directory, any file within that directory 
may be renamed or deleted only by the owner of the file, by the owner of the 
directory, or by a privileged process (for example, `*`root`*`, the master 
system administrator), regardless of any other permissions that might be set.
The system's temporary directoriers (`*`/tmp`*` and `*`/var/tmp`*`) have this
turned on.

These permissions are represented in the *ls -l* output as modifications
of the \'x\' character:

~~~plain
SUID changes the user\'s x character to an s (or S if eXecute is not turned on)

SGID changes the group\'s x character to an s (or S if eXecute is not turned on)

The sticky bit changes other\'s x character to a t 
(or T if the eXecute is not turned on)
~~~

When using symbolic modes with *chmod*, the permissions are requested as
follows:

- SUID is "s" permission in the "u" community

- SGID is "s" permission in the "g" community

- Sticky is "t" permission in the "o" community

When using numeric modes with *chmod*, these special permissions are
represented as an additional octal digit to the left of the three basic
octal permission digits. The value of these special permissions is:

~~~plain
4 SUID
2 SGID
1 Sticky
~~~

Examples: 

~~~plain
$ cp /usr/bin/cp mycp     # make a private copy of the 'cp' command
$ ls -l mycp              # view the original permissions
-rwxr-xr-x. 1 chris chris 145488 Sep 26 12:21 mycp
$ chmod u+s mycp          # add SUID
$ ls -l mycp              # view the new permissions
-rwsr-xr-x. 1 chris chris 145488 Sep 26 12:21 mycp
$ cp /usr/bin/mv mymv     # make a private copy of the 'mv' command
$ ls -l mymv              # view the original permissions
-rwxr-xr-x. 1 chris chris 137280 Sep 26 12:21 mymv
$ chmod 06755 mymv        # turn on SUID and SGID and set permissions to rwxr-xr-x
$ ls -l mymv              # view the new permissions
-rwsr-sr-x. 1 chris chris 137280 Sep 26 12:21 mymv
$ ls -l -d /usr/bin/passwd /tmp  # view some existing files with special permissions
drwxrwxrwt. 26 root root   600 Sep 26 12:21 /tmp
-rwsr-xr-x.  1 root root 32760 Jan 18  2023 /usr/bin/passwd
~~~

## Securing Your Account 

There are two ways to secure your account on Matrix:

1\. If you do not want to share *any* of your files with other users,
you can disable access to your home directory by turning off all
permissions for the group and other communities. The command *chmod go=
\~* will set this. Since this turns off access permission to that
directory, other users will not be able to access any of the files
within your home directory, regardless of the permission on the
individual file.

2\. If you want to share access to *some* of your files with other
users, turn on the appropriate permissions for group and/or other users,
and use the *umask* to limit the permissions on new files and
directories.

For example, you might:

1. Start by turning off all permissions on the files and directories that are 
currently in your home directory:

~~~plain
chmod -r go= ~/*
~~~

2. Create a directory of files you wish to share, called `*`~/public`*`. Set 
the permission on this directory so that group and others can access it:

~~~plain
mkdir ~/public
chmod go=rx ~/public
~~~

3. Place any files that you want to share in the `*`~/public`*` directory and 
set appropriate permissions:

~~~plain
cp anyFilesYouWantToShare ~/public
chmod go=r ~/public
~~~

4. Set up you umask so that, by default, other users have no access to any new 
files you create (place this in your `*`~/.bashrc`*` file to ensure that it is 
applied to all new bash shells that you start in the future):

~~~plain
umask 0077
~~~

5. Ensure that users can access your ~/public directory through your 
home directory:

~~~plain
chmod go=rx ~`\
~~~


