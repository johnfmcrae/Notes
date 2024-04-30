# Bash Scripting

You can run a shell script with either the shell interpreter or the bash interpreter. Use `sh <script name>` for the former and `bash <script name>` for the latter.

You can also add a *shebang* to the top of the script to specify which interpreter to use. You need to specify the path to the interpreter, which you can find using the `which` command.

```sh
#!/bin/bash
echo hello world
```

## Variables

Declare variables by using a single equals sign (`=`) without any spaces around it. Call variables by placing a `$` in front of it.

```sh
MESSAGE="Hello world"
echo $MESSAGE
```

Use `read` to get user input.


## Loops and Conditionals

Conditionals use the `if`, `else`, and `elif` keywords in bash. You must also specify the code to run with a `then` command and close the conditional with a `fi`.

```sh
if [[ condition == true ]]
then
    echo Hello!
elif [[ otherCondition == true ]]
then
    echo Wow!
else
    echo That's it folks!
fi
```

You don't need the `then` after an `else`. Notice that above we're using double square brackets. You can also use a semicolon for the condition.

```sh
if [ condition == true ];
then
    echo "It is true"
fi
```

A `true` value in the shell is returned as a 0 and a `false` is returned as a 1. Think of these values as the number of errors returned by the command line.
