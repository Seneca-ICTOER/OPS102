# Parameters

Arguments to a script are called parameters. You can access the parameters using the special variables `$0`, `$1`, `$2`, and so forth. `$0` contains the name of the script, `$1` contains the first parameter, `$2` contains the second parameter, and so forth.

The special variable `$#` contains the total number of parameters.

Here is a simple script which shows you what parameters have been received:

~~~bash
#!/usr/bin/bash​
echo "Number of parameters:  $#"​
echo "Parameter 0:           $0"​
echo "Parameter 1:           $1"​
echo "Parameter 2:           $2"​
echo "Parameter 3:           $3"​
echo "Parameter 4:           $4"
~~~

When you run this script with three parameters (red, green, and blue),
you get this output:

~~~bash
$ ./params red green blue​
Number of parameters:  3​
Parameter 0:           ./params
Parameter 1:           red​
Parameter 2:           green​
Parameter 3:           blue​
Parameter 4:
~~~

The `shift` command discards parameter `$1` and moves each of the remaining parameters to the previous position (so the value in parameter `$2` is moved to `$1`, and `$3` is moved to `$2`). We can modify the previous script to demonstrate this:

~~~bash
$ cat params2​
#!/usr/bin/bash​
echo "Number of parameters:  $#"​

echo "Parameter 0:           $0"​
echo "Parameter 1:           $1"​
echo "Parameter 2:           $2"​
echo "Parameter 3:           $3"​
echo "Parameter 4:           $4"

echo "---- Performing shift ----"
shift

echo "Parameter 0:           $0"​
echo "Parameter 1:           $1"​
echo "Parameter 2:           $2"​
echo "Parameter 3:           $3"​
echo "Parameter 4:           $4"

$ ./params2 red green blue
Number of parameters:  3
Parameter 0:           ./params2
Parameter 1:           red
Parameter 2:           green
Parameter 3:           blue
Parameter 4:           
---- Performing shift ----
Parameter 0:           ./params2
Parameter 1:           green
Parameter 2:           blue
Parameter 3:           
Parameter 4:  
~~~

The `shift` command is useful for looping through parameters, and for accessing parameters higher than number 9.
