# Pathnames

A *pathname* is a filename that includes information about the
directory in which the file is stored. (Sometime pathnames are simply
called filenames!).

There are three types of pathnames, each of which has advantages and
disadvantages. It is often necessary to use multiple types of pathnames
in one command \-- for example, when copying information from one
directory to another directory.

These are the three types of pathnames:

## 1. Absolute Pathnames

An absolute pathname starts with a slash (on Unix-based operating
systems, such as Linux), or a backslash (on Windows), indicating the
root directory. It contains the names of all of the directories from the
root directory to the specified file, separated by slash/backslash
characters.

For example, on a Linux system, the pathname

```plain

/home/kim/ops102/presentation.pdf
```

indicates that the file presentation.pdf can be found by starting at the
root directory, then traversing to a directory named \"home\" containing
the directory \"kim\" containing the directory \"ops102\" containing the
file (\"presentation.pdf\").

Similarly, the Windows pathname

```plain

\Users\kim\ops102\presentation.pdf
```

indicates that the file presentation.pdf can be found by starting at the
root directory, then traversing to a directory named \"Users\" containin
the directory \"kim\" containing the directory \"ops102\" containing the
file (\"presentation.pdf\").

Absolute pathnames can be readily identified by the fact that they start
with the slash/backslash character. They are often the longest form of
the pathname, but they are unambiguous.

## 2. Relative-to-Home Pathnames 

On Linux (and other Unix-like operating systems), pathnames may be
specified starting with the tilde (\"\~\") character followed by a
slash, which represents the current user\'s home directory. This is a
directory assigned by the system administrator which contains all of the
user\'s personal files. The home directory is usually (but not always)
*/home*/username**.

For example, if the current user\'s home directory is */home/kim*, then
the filename

```plain
~/ops102/presentation.pdf
```

corresponds to the absolute pathname

```plain
/home/kim/ops102/presentation.pdf
```

For any file in the user\'s home directory, a relative-to-home pathname
is generally shorter than an absolute pathanme. However, a
relative-to-home pathname will have a different meaning for other users,
since each user has a unique home directory.

You can also specify the user whose home directory is to be used as the
starting point, by placing the a userid between the tilde and slash
characters. Thus the pathanme

```plain
~kim/ops102/presentation.pdf
```

is relative to the home directory of the user \"kim\", regardless of
which user is currently logged in, while the pathname

```plain
~sam/ops102/presentation.pdf
```

is relative to the home directory of the user \"sam\".

## 3. Relative Pathnames 

Any pathname that does not start with a slash/backslash or a tilde
character is a *relative* pathname, which is interpreted as starting
at the current directory.

If the current directory is */home/kim/ops102*, then the Linux pathname

```plain

presentation.pdf
```

is interpreted as

```plain
/home/kim/ops102/presentation.pdf
```

The symbol \"..\" means the parent directory. Assuming the same current
directory as above (*/home/kim/ops102*), the Linux pathname

```plain
../Downloads/example.txt
```

Is interpreted as

```plain
/home/kim/Downloads/example.txt
```

In the same way, the symbol \".\" is interpreted as referring to the
current directory, so

```plain
./test.odt
```

is the same as

```plain
test.odt
```

and both refer to

```plain
/home/kim/ops102/test.odt
```

Likewise, if the current directory on a Windows system was
*\\Users\\kim*, then the pathaname

```plain
ops102\presentation.pdf
```

refers to the absolute pathname

```plain
\Users\kim\ops102\presentation.pdf
```

And the relative pathname

```plain
..\jdoe\Downloads\example.txt
```

refers to the absolute pathname

```plain
\Users\jdoe\Downloads\example.txt
```

Relative pathnames are often the shortest form of pathname *if* the
target file is in the current working directory or a subdirectory of the
current working directory, but the meaning of a relative pathname
changes based on the current working directory.

# Directory vs File Names 

It is often impossible to tell whether a pathname refers to a file or to
a directory. For example, the Linux pathname */home/chris/presentation*
might refer to a file named *presentation* or to a directory named
*presentation*.

If you wish to explicitly indicate that a pathname refers to a
directory, append a slash or backslash to the pathname.

