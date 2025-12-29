# Root, Home, and Current Working Directories

## Root Directory

The *root* directory is the main directory. All other directories and files are contained inside the root directory.

## Current Working Directory (or *Working Directory* or *Current Directory*)

Most operating systems have the concept of a *current working directory* (also called the *current directory* or *working directory*), which is a directory to be temporarily designated as the current working location. The working directory may be changed at any time.

To change the current working directory on Linux or on Windows, use the `cd` command (*change directory*) followed by a directory name:

```plain
cd ops102
```

To see the name of the current directory, use the command `pwd` (Print Working Directory) on Linux or `cd` (without a directory name) on Windows.

To change your current directory to your home directory on Linux, use the `cd` command by itself (with no arguments).

> **Tip:** To quickly change back to the *previous* working directory on a Linux system, issue the command: `cd -`

## Home Directory

Both Windows and Linux create a directory for each user, which is used to store that user's personal files.

On a Linux system, the home directory is contained within a directory named `home` which is within the root directory. Each user's home directory name is their user ID; for example, the user `jdoe` would have the home directory `/home/jdoe`.

> **The directory named `/home` is not the home directory!** The directory `/home` *contains* all of the users' home directories.

On a Windows system, the home directory is `C:\Users\`*username*. The user `jdoe` would have a home directory of `C:\Users\jdoe`.

## A Word about MacOS Systems

On MacOS, home directories are stored in `/Users` rather than `/home`, but otherwise, MacOS and Linux filesystems are very similar.
