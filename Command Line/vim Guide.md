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

| **Key**  | **Action**                        |
|----------|-----------------------------------|
| `Ctrl+f` | Down one page                     |
| `Ctrl+b` | Up one page                       |
| `G`      | Go to the last line of the file   |
| `0`      | Beginning of the current line     |
| `$`      | End of the current line           |
| `w`      | Next word or punctuation mark     |
| `W`      | Next word ignoring punctuation    |
| `b`      | Previous word or punctuation mark |
| `B`      | Previous word or punctuation mark |

Often you can prefix a command with a number. For example, you can add a number before entering `Ctrl+j` to move a given number of lines down.

- `j` down one line
- `k` up one line
- `l` right one character
- `h` left one character
- number, `Shift+g` go to line number

## Editing

The classic `i` command enters insert mode. You'll notice however, that even you use the `0` command to get to the end of the line, vim won't put the cursor at the very end. That's because vim can only put the cursor before the last character of a line. So if you want to add some text to the end of a line, use the `a` command to *append*, which will move the cursor to past the last character.

The uppercase `A` version of append opens append mode and moves the cursor to the end of the line.

The lowercase `o` and uppercase `O` commands insert a newline. Lowercase `o` inserts a newline below the current line and uppercase `O` inserts one after the current line.

## Deleting Text

The basic delete commands in Vim are the `x` and `d` commands. You can use the `x` command on its own to delete a single character. The `d` command works with other keys to delete specific regions of text.

| **Key**       | **Deletes**                                       |
|---------------|---------------------------------------------------|
| `x`           | Current character                                 |
| `3x`          | Current character and the next two characters     |
| `dd`          | Current line                                      |
| `5dd`         | Current line and the next four lines              |
| `dw`          | Next word if the cursor is at the start of a word |
| `d$`          | Remainder of line after cursor                    |
| `d0`          | Line before the cursor                            |
| `d^`          | Previous word or punctuation mark                 |
| `dG`          | Current line to the end of the file               |
| `d,6,Shift+g` | Current line to line 6                            |

You can undo a delete operation with the `u` command.

## Copy, Cut, Paste

Deleting text in Vim also adds it to the clipboard. A delete command bundles in a cut fro free!

Copying in Vim is called *yanking*, which is unfortunate because that is the term for pasting in the terminal. To yank (copy) text in Vim, use the `y` command. The `y` command has all of the extensions that the `d` command has. For example `yy` yanks the current line, `yw` copies the current word, and so on.

To paste text use the `p` command.

You can access early items in the cut and yank register. Register entries are numbered 0 to 9. Access the register with the `"` character. So to paste the third last item, use `"3p`.
