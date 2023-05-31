#### Key Bindings

| Shortcut | Use |
| --- | --- |
| h, j, k, l | Move cursor left, down, up, right |
| i | Enter insert mode at cursor position |
| a | Enter insert mode after cursor |
| A | Enter insert mode at end of line |
| o | Begin a new line below the cursor and enter insert mode |
| O | Begin a new line above the cursor and enter insert mode |
| w | Move cursor to beginning of next word |
| b | Move cursor to beginning of previous word |
| e | Move cursor to end of current word |
| gg | Go to first line of document |
| G | Go to last line of document |
| :w | Save changes to file |
| :q | Quit Vim |
| :q! | Quit Vim without saving changes |

#### Command Mode Actions

Standard | Vim | Meaning
---|---|---
cut | d | delete
copy | y | yank
paste | P/p | put

#### Delete

action | result
---|---
dd | delete current file
3dd | delete the next three lines
dw | delete the current word
d3w | delete the next three words
d4h | delete four characters to the left

#### Change

action | result
--- | ---
dd | change current line
cw | change current word
c3w | change the next three words
c5h | change five characters to the left

#### Yank

action | result
--- | ---
yy | yank current line
3yy | yank the next three lines
yw | yank the current word
y$ | yank to the end to the line

#### Put

action | result
--- | ---
p | put (paste) after cursor
P | put before cursor

### Searching in Vim

Searching in Vim if powerful than the good old ctrl+f because it supports both literal text and regex.

To search forward from the current position of the cursor, use the `/` to start the search, type a search term, and then press the *Enter* key to begin the search. The cursor will move to the first match that is found.

To proceed to the next match using the same pattern press the `n` key. To go back to the previous match, press the `N` key.

#### Insert Mode

This mode is used to add text to the document.

Input | Purpose
--- | ---
a | enter insert mode right after the cursor
A | enter insert mode at the end of the line
i | enter the insert mode before the cursor 
I | enter the insert mode at the beginning of the line
o | enter the insert mode on a blank line after the cursor
O | enter the insert mode on a blank line before the cursor

#### Some commonly used commands

Input | Purpose
--- | ---
:w | write current file to the filesystem
:w *filename* | save a copy of the current file as the *filename*
:w! | force writing to the current file
:1 | go to line number 1 or whatever number is given
:e *filename* | open *filename*
:q | quit if no changes were made to the file
:q! | quit without saving the changes to file

