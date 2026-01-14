# GUI vs CLI: Advantages and Disadvantages 

Both graphical user interfaces (GUIs) and Command Line Interfaces (CLIs)
have strengths and weaknesses, making them suited for different types of
use.

The visual nature of a graphical user interface makes it well-suited for
creating, editing, and viewing visual media, such as photos, videos,
presentations, and highly-formatted documents. A GUI is also well-suited
to dense displays of visual information, such as data dashboards.
However, many GUIs are not well-suited to some types of automation, and the large
amount of information in a graphical display may consume a lot of network
bandwidth if the GUI is used over a remote connection.

On the other hand, a CLI is well-suited to task automation, and many
tasks may require fewer steps to perform than when using a GUI. CLIs
generally require much less bandwidth when used over a network, making
them well-suited to remote administration tasks.

To compare the data demands of the two types of user interfaces,
consider the amount of information that needs to be sent to the display
to update it:

-  A GUI on a 1920x1080 ("full high definition") monitor displays about
6 megabytes of data (2 million pixels x 3 bytes per pixel) at one time

-  A CLI (or TUI) on an 80x25 character terminal displays about 
2 kilobytes of data (just 0.002 megabytes) at one time

Obviously, updating a remote CLI display will require much less data than updating a remote GUI display.

As an example of the strengths of each type of user interface, consider
the task of croping, resizing, and changing the format of photographs:

-  A GUI immediately shows the effect of changes and allows the adjustments to be easily fine-tuned, producing exact results for a small number of photos. However, it may take many steps to perform the edits, so editing hundreds of photographs will take a very long time. 

-  A CLI is well-suited to automation. Edits could be applied to hundreds of pictures in a few seconds, *if* the edits can be adequately described on the command-line.

## GUIs and CLIs are Complimentary

Since computer programs are text, programmers become accustomed to referring to resources using text descriptions. For example, a programmer may a write line of C code to open a file like this:

```C
  open("/usr/share/dict/words", O_RDONLY);
```

If the programmer wanted to check on that file, perhaps to see the file size or make sure they got the name right, they could use a either a GUI or a CLI tool. But since they've just been looking at text (the code they just wrote), it's often easiest to stay in the same mental mode and access the file using a CLI tool, rather than to switch to a different paradigm and use a GUI tool.

A programmer will often use both types of user interfaces in combination. For example, they may adjust a sound file using a GUI tool, then use a CLI to place the sound file into a particular folder or directory, mixing and matching GUI and CLI tools on-they-fly.
