# Windows vs. Linux Scripting 

Windows shell scripting is similar to Linux shell scripting in many
ways.

However, since Windows and Linux (and other Unix-like operating systems)
have different technical heritages, some of the syntax and approaches
are very different.

## An Abundance of Shells 

We\'ve looked at scripting on Linux systems using the *bash* shell \--
which is the most widely-deployed shell on Linux and other Unix-like
systems. There are many other shells on similar systems, including:​

- sh – the original Unix shell ("Bourne Shell"), written by Steven Bourne​
- ksh – the Korn shell, written by David Korn​
- csh – the C shell, which has a C-like syntax​
- fish – the Friendly Interactive shell​
- Zsh – the Z shell, similar to ksh​

Many of these have a syntax based on and similar to the original Bourne
shell, which is standardized in the POSIX.1 standard (or IEEE Standard
1003.1), and these shells have a lot in common.​

On Windows, there are two main shells:

- CMD - The Windows command shell, which is the traditional Windows shell. 
Although based on traditional DOS command syntax, the CMD shell has been 
considerably expanded, with many new features added over the last few years.​

- PowerShell – this is a new Windows command shell, which combines scripting 
with object-oriented programming. It is pre-installed for interactive use on 
current Windows systems; however, the execution of PowerShell scripts is 
disabled by default on all Windows "client" (non-server) systems, including 
Seneca lab computers.​

​Due to PowerShell scripting being disabled by default, and because
object oriented programming is not taught in the first semester
programming courses, we will focus on scripting using the traditional
Windows CMD shell.​

## Cross-Platform Scripting 

There are several possible approaches to writing scripts that will work
on both Linux and Windows systems, as well as other common operating
systems such as Mac OS:​

- Bash or Zsh – bash is the default shell on most Linux systems, and zsh 
is the default shell on most Mac OS systems; either shell can be easily 
used on either system. Both shells are available as third-party add-ons 
for the Windows operating system, usually shipped with a collection of 
GNU utilities compiled for use with Windows (for example, 
see [https:gitforwindows.org/](https:gitforwindows.org/))​

- PowerShell – installed by default on current Windows systems, it is also 
available for Linux and Mac OS systems, although it is not commonly used on 
those systems yet (see [https://github.com/PowerShell/PowerShell](https://github.com/PowerShell/PowerShell)i )

## Other Interpreted Languages 

In addition to shell scripting languages, there are other interpreted
languages that are well suited for cross-platform development, including
Python and Perl.​

​When should you use a shell scripting langauge?​

- Shell scripting languages are ideally suited for process control – 
executing, managing, and combining external programs to accomplish tasks.​

- Shell scripting languages are not well-suited for implementing advanced 
processing algorithms, because they generally lack features such as good 
floating-point support, typed variables, and strong support for large 
arrays and hashes.​

## Windows \"Shell Scripts\" vs. Batch Files\" 

DOS and early Windows systems were inherently interactive in nature, and
early scripts were called \"batch files\" because they were viewed as
similar to non-interactive batch processing on mainframe systems.​

This terminology has stuck, and Windows shell scripts are still often
called \"batch files\" (hence the occasional use of the .bat extension
instead of .cmd).​​

The concept of a \"batch file\" and a \"shell script\" are roughly
equivalent.​

## Basic Requirements for Shell Scripts ##

Remember these requirements? They apply to Windows scripts too:

1\. **Create a text file containing shell commands.** Use any text
editor, such as Notepad, to create the file.

2\. **Tell the operating system which shell to use to execute the
commands.​** In Windows, the filename extension is used to associate a
file with a program, and this mechanism is used to associate a script
with a command interpreter.​ ​

- For CMD scripts, the extension `.cmd` is used.​ For historical reasons, 
the extension `.bat` is also accepted.​

- For PowerShell scripts, the extension `.ps1` is used.​ The reason that 
`.ps` isn't used is that that extension was already used for PostScript files.​ (As a reminder: We're not going to write PowerShell scripts in this course).​

3\. **Ensure that the script file has the appropriate permissions.​**
On Windows, the ability to read the script file is sufficient (and this
is the default permission, so no change is usually required for scripts
that you create for your own use; the situation may be different for
scripts that are shared to other machines over the network or to other
users on your system).​

# Command Echos​ 

Windows defaults to displaying each command in a script before executing
it (the opposite of the default in the bash shell). If you do not want
each command to be displayed, you can:​

- Add an @ sign in front of each command, or​
- Issue the echo off command.​

Usually, you\'ll combine these in a script, using this as one of the
first lines:​

~~~cmd
@echo off​
~~~


