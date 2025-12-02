# GUI vs CLI: Advantages and Disadvantages 

Both graphical user interfaces (GUIs) and Command Line Interfaces (CLIs)
have strengths and weaknesses, making them suited for different types of
use.

The visual nature of a graphical user interface makes it well-suited for
creating, editing, and viewing visual media, such as photos, videos,
presentations, and highly-formatted documents. A GUI is also well-suited
to dense displays of visual information, such as data dashboards.
However, many GUIs are not well-suited to automation, and the large
amount of information in the display may consume a lot of network
bandwidth if the GUI is used over a remote connection.

On the other hand, a CLI is well-suited to task automation, and many
tasks may require fewer steps to perform than when using a GUI. CLIs
generally require much less bandwidth when used over a network, making
them well-suited to remote administration tasks.

To compare the data demands of the two types of user interfaces,
consider the amount of information that needs to be sent to the display
to update it:

-  A GUI on a 1920x1080 ("full high definition") monitor displays about
6 megabytes of data (2 million pixels x 3 bytes per pixel) at one time

-  A CLI (or TUI) on an 80x25 character terminal displays about 
2 kilobytes of data (0.002 megabytes) at one time

As an example of the strengths of each type of user interface, consider
the task of croping, resizing, and changing the format of photographs:

-  A GUI immediately shows the effect of changes and allows the 
adjustments to be easily fine-tuned, producing exact results for a small 
number of photos. However, it may take many steps to perform the edits, 
so editing hundreds of photographs will take a very long time. 

-  A CLI is well-suited to automation. Edits could be applied to hundreds
of pictures in a few seconds, *if* the edits can be adequately described on
the command-line.

A programmer will often use both types of user interfaces in combination. For 
example, they may adjust a sound file using a GUI, then use a CLI to
place the sound file into a particular folder or directory. This is because 
programmer has been writing code to access the file, and it seems intuitive to 
use the same text-based reference to the file to manage the file.