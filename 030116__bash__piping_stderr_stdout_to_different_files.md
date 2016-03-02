### [BASH] Piping STDERR and STDOUT to different files

For me one of the greatest advantages of the bash is solving complex tasks by
piping a sequence of simple commands, each with a very specific responsibility.

At the beginning, I didn't know how to use stderr, so I printed everything to
STDOUT, and this would break the whole piping paradigm. It would also mix errors
and debug on the log file. Little did I know how simple it was to split this into
two different files, for instance:

``` bash
  the_command 1>> stdout.log 2>> stderr.log
```

This appends the output of *stdout* to a file called `stdout.log`, while appending
what comes out of *stderr* to `stderr.log`.
