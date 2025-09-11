# Environment Variables 

By default, all variables are environment variables, inherited by child
processes.​​

Environment variables are commonly used to pass configuration
information to programs and to configure how programs operate.​

You can view all of the current variables with the *set* command;
you\'ll probably want to pipe the output through *more*. ​ Environment
variables are used by all processes, not just the shell!​

## Common Environment Variables 

| Environment Variable | Purpose | Examples |
|:---                  |:---     |:---      |
| CD | Current directory | ''ECHO %CD%'' |
| TIME | Current time (HH:MM:SS) | ''ECHO %TIME%'' |
| DATE | Current date in local format | ''ECHO %DATE%'' |
| ERRORLEVEL | The error code / exit status of the last command executed (note that some commands or programs do not set this variable as expected). | ''DIR \FileThatDoesNotExist ''\\ ''ECHO %ERRORLEVEL%'' |
| PATH | A semicolon [;] separated list of directories that will be searched when looking for a command | ''PATH="$PATH;\SpecialDirectory"''
| PROMPT | The prompt presented by the shell. | ''SET PROMPT=Enter a command: ''\\ ''SET PROMPT=$P$G '' |
| RANDOM | A random integer (0-32767) | ECHO %RANDOM% |

Note that the *prompt* and *path* programs may also be used to adjust
the PROMPT and PATH environment variables, respectively.
