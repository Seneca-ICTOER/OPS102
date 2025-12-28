# Basic Requirements for Shell Scripts 
Remember these requirements? They apply to Windows scripts too:

1\. **Create a text file containing shell commands.​** Use any text
editor, such as Notepad, to create the file.

2\. **Tell the operating system which shell to use to execute the
commands.** In Windows, the filename extension is used to associate a
file with a program, and this mechanism is used to associate a script
with a command interpreter.​ ​

- For CMD scripts, the extension ".cmd" is used.​ For historical reasons, the extension ".bat" is also accepted.​
- For PowerShell scripts, the extension ".ps1" is used.​ The reason that ".ps" isn't used is that that extension was already used for PostScript files.​ (As a reminder: We're not going to write PowerShell scripts in this course).​

3\. **Ensure that the script file has the appropriate permissions.​**
On Windows, the ability to read the script file is sufficient (and this
is the default permission, so no change is usually required for scripts
that you create for your own use; the situation may be different for
scripts that are shared to other machines over the network or to other
users on your system).​
