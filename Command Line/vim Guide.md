# Vim Guide

Vim is case sensitive.

## Vim Settings

- `:set number` show line numbers
- `:set nonumber` hide line numbers

## Exiting and Entering Vim

- Enter vim with the `vi` or `vim` command. Generally, `vi` is symbolically linked to vim.
- Quit vim without saving with `:q!`
- Save and quit vim with `:wq`

## Moving the Cursor

- `Ctrl+f` down one page
- `Ctrl+b` up one page
- `G` go to the last line of the file
- `0` beginning of current line
- `$` end of current line
- `w` next word or punctuation mark
- `W` next word ignoring punctuation
- `b` previous word or punctuation mark
- `B` previous word ignoring punctuation

Often you can prefix a command with a number. For example, you can add a number before entering `Ctrl+j` to move a given number of lines down.

- `j` down one line
- `k` up one line
- `l` right one character
- `h` left one character
- number + `G` go to line number

## Editing

The classic `i` command enters insert mode. You'll notice however, that even you use the `0` command to get to the end of the line, vim won't put the cursor at the very end. That's because vim can only put the cursor before the last character of a line. So if you want to add some text to the end of a line, use the `a` command to *append*, which will move the cursor to past the last character.

The uppercase `A` version of append opens append mode and moves the cursor to the end of the line.

The lowercase `o` and uppercase `O` commands insert a newline. Lowercase `o` inserts a newline below the current line and uppercase `O` inserts one after the current line.
