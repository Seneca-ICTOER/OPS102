# Filenames

The rules for valid filenames vary with the type of filesystem, but
generally, filenames may include:
- letters (a-z)
- numbers (0-9)
- dashes (-)
- underscores (_)
- periods (.)

Other punctuation marks may be acceptable in some
filesystems but not in others, and are therefore best avoided,
especially if files may be transferred between different types of
filesystems or between computers.

Spaces may be included in filenames, but may require quoting if accessed
from the command-line, so that the shell does not interpret the filename
as two or more separate filenames. For example, the filename \"red
leaf\" may be interpreted as two separate filenames if written without
quoting:

```plain
ls red leaf
```

When quotes are added, the ambiguity is removed, and the shell will
correctly interpret the filename as a single name:

```plain
ls "red leaf"
```

For this reason, it is good practice to avoid using spaces in filenames
(underscores are a good alternative).

## Extensions

Many operating systems use an *extension* at the end of a filename to
denote the type of data stored in the file. These extensions are
delimited by a period followed by one or more characters. For example,
in the filename:

```plain
ops102_project.pdf
```

The extension is \"pdf\", denoting a file in Portable Document Format.

It is unusual to use multiple extensions on a Windows system, but not
uncommon on a Linux (or other Unix-like) system.

For example, on a Linux system, the filename

```plain
backup.tar.gz
```

has two extensions, \"tar\" indicating a archive created with the *tar*
command, and \"gz\" indiciating that the file was compressed with the
*gzip* command.

## Case Sensitivity 

Some filesystems are case-sensitive, and UPPER- and lower-case letters
are considered to be different. For example, the filenames *MILK.PDF*,
*Milk.pdf*, and *milk.pdf* refer to three different files. This is the
case with most Linux (and Unix-like) filesystems.

Most Windows filesystems are not case-sensitive, so the filesnames
*MILK.PDF*, *Milk.pdf*, and *milk.pdf* would refer to the same file.
