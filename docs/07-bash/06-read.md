# Reading Variable Values from Stdin: read 

The *read* command reads a line of text from stdin and assigns it to the
specified variable. For example, `read A` reads a line of text and
assigns it to the variable *A*.

The *read* command can also send a prompt to stdout using the -p option:

~~~plain
$ read -p "Enter your name: " NAME
Enter your name: Chris
$ echo $NAME
Chris
~~~

Here is a script which uses a couple of *read* statements:

~~~bash
#!/usr/bin/bash
read -p "Please enter your name: " NAME
echo "Pleased to meet you, $NAME"
read -p "Please enter a filename: " FILE
echo "Saving your name into the file..."
echo "NAME=$NAME" >>$FILE
echo "Done."
~~~

