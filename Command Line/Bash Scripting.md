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