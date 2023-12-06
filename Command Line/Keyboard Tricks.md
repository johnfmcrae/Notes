# Command Line Keyboard Tricks

## Cursor Movement

From [Shotts](https://www.oreilly.com/library/view/the-linux-command/9781593273897/)

| **Key**  | **Action**                                |
|--------- |-------------------------------------------|
| Ctrl+a   | Move cursor to the beginning of the line. |
| Ctrl+e   | Move cursor to the end of the line.       |
| Ctrl+f   | Move cursor forward one character.        |
| Ctrl+b   | Move cursor backward one character.       |
| Alt+f    | Move cursor forward one word.             |
| Alt+b    | Move cursor backward one word.            |
| Ctrl+l   | Same as the `clear` command               |

## Killing and Moving Text

The familiar concept of copying pasting has an approximate analog in Unix called *killing* and *yanking*. These commands cover deleting text, storing that text in something called the *kill ring* and accessing the text stored in that ring.

### Deleting and Killing

In Unix, you can use the `Delete` and `Backspace` keys as expected. You can also use the `Alt+\` command to delete blank space.

*Killing* text deletes it from its current location and places it in the kill ring. The two basic commands to kill text are:

- `Ctrl+k`: Kill text from the cursor location to the end of line
- `Ctrl+u`: Kill text from the cursor location to the beginning of the line.

### Yanking

*Yanking* is analogous to *pasting*. However, because we kill text into the kill ring, we get the built-in benefit of a text buffer to work with.

To yank the last item in the kill ring, use `Ctrl+y`.

If you want to access earlier items in the kill ring, you can use the yank-pop command with`Alt+y`. However, to use the yank-pop command, you need to use the basic yank command with `Ctrl+y` first.

So for example, let's say you kill a few items with `Ctrl+K`. Now, you want to yank one of the earlier items in the kill ring. You start by using `Ctrl+y` then cycle through the ring with `Alt+y`.
