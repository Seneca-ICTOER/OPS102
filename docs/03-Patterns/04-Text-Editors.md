# Text Editors 

It's often necessary to edit a text file containing a script, program,
data, or configuration information. There are many text editors
available.

## Default Text Editors 

It is useful to learn how to use the text editor(s) provided by
default with each operating system, because these editors will be
available on almost any computer you use without installing any
additional software. In other words, you'll be able to confidently walk up to 
any system, anywhere, and edit a file!

### Linux Default Text Editor 

On Linux systems, most distributions (the organizations or companies
responsible for maintaining and distributing the system) have
standardized on the *nano* editor as the default CLI/TUI text editor
(replacing the less-user-friendly but more-powerful *vi* editor). To
start nano, type *nano* and optionally provide a filename:

~~~plain
nano
nano file
~~~

Nano provides a help display at the bottom of the screen. The carat ^
symbol indicates the control key, so the help text \"\^X Exit\" means
that you would press Ctrl-X to exit from the editor.

Since Linux systems provide multiple desktop GUI environments, the
default GUI text editor(s) will vary with the installed desktop GUI. For
example, on Linux desktops using the Gnome environment, the default GUI
text editor is *Gedit* or *Gnome Text Editor*; on Linux desktops using
the KDE desktop, the default GUI text editor is a program called *Kate*.

### Windows Default Text Editor 

The current versions of Windows (Windows 10 & 11) do not provide a
CLI/TUI text editor (previous versions of Windows did provide a CLI text
editor, and there is a current discussion about ading this back in).
However, you can run the GUI Notepad editor, either from the Start Menu,
or from the command line (as long as you are not accessing the Windows
system remotely through a non-graphical connection), optionally providing
a filename to be edited:

~~~plain
notepad
notepad file
~~~

## Other Text Editors 

There are **many** other text editors available for both platforms,
and many editors are available that work on multiple operating systems.
For example, *nano* and *vi* are available for Windows systems, and
editors similar to *notepad* are available on Linux.

There are also several categories of software that are (arguably) a type
of text editor, including:

1. Basic text editors
1. Code editors, for editing software and configuration files, with features such as tooltip help, syntax highlighting, bracket matching, and automatic indentation
1. Word processors, for editing documents, with features such as spell 
checking, visual formatting, advanced layout features such as columns
and tables

Software developers and system administrators have strong opinions about
their tools, and particularly about their text editors. Things to
consider when selecting any type of text editor include:

- Interface: does the editor use a graphical user interface, a text user interface, or can it operate in both modes?
- Tools: does the editor have useful tools such as syntax highlighting for common languages and configuration files? Does the list of supported languages include the ones you want to use?
- Visual complexity: some users prefer an editor with on-screen controls (or help) for most or all of the actions they may perform so that they can access these features quickly. Others prefer a less-cluttered screen which dedicates maximum screen space to content and minimizes distractions.
- Previews and integration with other tools: can the software provide visual previews, such as HTML and CSS display for web documents, LaTeX rendering, and accessibility assessments? Can you directly invoke publishing, content conversion, file transfer, or compilation processes from within the editor?
- Feature control: can you easily turn features on and off? For example, can you disable spell checking or syntax highlighting if your file contains a section that is in a different language? Can you disable auto-correction when it is not relevant to the project at hand?

Most software developers and system administrators use multiple editors
for different tasks - for example, they may choose one editor for quick
cnfiguration changes, another editor (or IDE) for larger development
tasks, and multiple editors for different types of documentation.

Note that features intended for one editing task can be a nuscience in
another context. For example, a word processor will often convert double
quote characters into "smart quotes" (look closely at the quotation
characters in this line), where the opening and closing quote characters
are distinct characters. While these look great and are good for general
writing, they are problematic in code and in examples that may appear in
documentation, because they will be rejected by some types of software
which expect straight double-quotes (such as most shells).