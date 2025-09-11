# Arithmetic

Bash can perform integer arithmetic.

To evaluate an arithmetic expression and return a value, use *\$(( ))*:

~~~plain
$ A=100
$ B=12
$ echo $((A*B))
1200
$ echo $((B++))
12
$ echo $B
13
~~~

Note that inside the double-parenthesis, spaces don\'t matter, and it is
not necessary to use a dollar-sign \[\$\] in front of variables being
accessed.

To evaluate an arithmetic expression without returning a value, use *((
))*:

~~~plain
$ A=100
$ B=13
$ ((A++))
$ echo $A
101
$ ((C=A*B*2))
$ echo "The answer is $C"
The answer is 2626
~~~