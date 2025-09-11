# Arithmetic

CMD can perform *integer* arithmetic.

To evaluate an arithmetic expressions and store the results in a
variable, use the `SET` command with the `/A` (arithmetic) option.
(Note: when used interactively the result of the expressions evaluation
will be output to stdout; this does not happen inside scripts).

~~~cmd
> SET A=100
> SET B=12
> SET /A X=A*B
1200      :: <--- This does not get printed inside a script
> ECHO %X%
1200
> SET /A A+=1 > NUL:
> ECHO %A%
101
> SET /A C=A*B*2 > NUL:
> ECHO The answer is %C%
The answer is 2424
~~~

Notes:

- You can perform more than one arithmetic evaluation and assignment in one SET command by separating the expressions with a comma [,]
- Some characters used in arithmetic expressions, such as the carat symbol, may need to be quoted or escaped to function correctly.​
- Percent signs, when used in arithmetic expressions (as the modulo operator), need to be doubled [%%] to avoid confusion with the percent signs placed around variable names​
