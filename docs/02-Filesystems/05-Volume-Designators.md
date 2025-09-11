# Volume Designators 

On Windows systems, a volume designator consisting of a letter followed
by a colon may prefix a pathname. The volume may be a partition on a
disk drive (HDD or SSD), a shortcut to a network storage location, or a
multi-drive volume, where multiple partitions or disks are combined into
a single storage pool.

Since the original IBM PC was designed to have up to two floppy disk
drives, designated A: and B:, the main/first disk drive in a Windows
system is usually designated as volume C:

Therefore, the \\Windows folder on the main/first disk drive on a
Windows system may be referred to as

```plain
C:\Windows
```

The volume designator is case-insensitive.

Each unique volume on a Windows system has its own current/working
directory. You can switch between volumes by typing the volume
designator by itself.

On a Linux system, instead of using drive designators, volumes are
*mounted* into the filesystem hierarchy \-- that is, volumes are
attached as directories, creating a unified hierarchy with a single root
directory.
