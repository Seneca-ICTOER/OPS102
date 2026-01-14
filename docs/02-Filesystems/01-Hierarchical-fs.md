# Hierarchical File Systems

Most modern computers are equipped with one or more random-access storage devices &mdash; either a mechanical hard disk drive (HDD), or a fully electronic solid state disk (SSD). Both of these provide a numbered set of blocks or sectors, each of which stores a set amount of data (typically 512 or 1024 bytes). However, accessing storage as numbered blocks is very inconvenient for computer users!

In order to conveniently use this storage, it is arranged into *files*, which are named collections of bytes of arbitrary length. The organization of blocks/sectors into files is handled by a *filesystem*, which is a scheme for structuring data, along with the corresponding software to implement this scheme.

There are different types of filesystems, intended for different purposes. For example:

- the *fat* filesystem is widely used on USB flash drives and SD cards which may be connected to a wide range of different computer systems. It's a lightweight, simple filesystem that is good for exchanging data between different types of systems, but it doesn't have any advanced features such as file permissions (access control).

- the *NTFS* (Windows) and *ext4* (Linux) filesystems are very different but offer similar capabilities. Windows and Linux use very different approaches to identifying users and controlling access to files, and these two filesystems are specifically designed to work with these different approaches - NTFS is designed to work with the Windows approach, and ext4 is designed to work with the Linux approach.

- the *btrfs* filesystem is a high-performance filesystem used on Linux systems. It provides advanced features useful for enterprise systems, such as storage pooling, error mitigation, snapshot backups, and integrity checking.

Most filesystems track metadata about a file in addition to the file name (usually written as "filename"), such as the date/time of creation, the date/time of last modification, the owner or original creator of the file, and the permissions applicable to the file (for example, who is permitted to read and to change the file contents).

A hierarchical filesystem introduces the concept of *directories*, which are special files which hold zero or more other files. The files in a directory may themselves be directories, enabling files to be nested into an arbitrary hierarchy.

When graphical user interfaces were developed, the metaphor of a traditional paper-based office was introduced, and directories were called *folders* in this metaphor (a folder in a traditional office is a piece of card stock folded in half to group together related papers).

Therefore, the terms *directory* and *folder* are synonyms &mdash; you can use them interchangeably in most contexts.
