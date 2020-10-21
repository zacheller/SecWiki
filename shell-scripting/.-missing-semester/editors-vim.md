# Editors \(Vim\)

{% embed url="https://sanctum.geek.nz/arabesque/vi-mode-in-bash/" caption="$ set -o vi" %}

## vimtutor

### Lesson 1 SUMMARY

* The cursor is moved using either the arrow keys or the hjkl keys.
  * `h` \(left\) `j` \(down\) `k` \(up\) `l` \(right\)
* To start Vim from the shell prompt type: vim FILENAME 
* To exit Vim type:  
  * `:q!`  to trash all changes. OR type: 
  * `:wq`  to save the changes.
* To delete the character at the cursor type: `x`
* To insert or append text type: 
  * `i` insert before the cursor
  * `A` append after the line

NOTE: Pressing `<ESC>` will place you in Normal mode or will cancel an unwanted and partially completed command.

### Lesson 2 SUMMARY

* To delete from the cursor up to the next word type:    `dw`
* To delete from the cursor to the end of a line type:    `d$`
* To delete a whole line type: `dd`
* To repeat a motion prepend it with a number: `2w`
* The format for a change command is: `operator [number] motion`
  * where: `operator` - is what to do, such as `d` for delete
  * `[number]` - is an optional count to repeat the motion
  * `motion` - moves over the text to operate on, such as `w` \(word\), `$` \(to the end of line\), etc.
* To move to the start of the line use a zero: `0`
* To undo previous actions, type: `u` \(lowercase u\)
* To undo all the changes on a line, type: `U` \(capital U\)
* To undo the undo's, type: `CTRL-R`

### Lesson 3 SUMMARY

* To put back text that has just been deleted, type `p`. This puts the deleted text AFTER the cursor \(if a line was deleted it will go on the line below the cursor\).
* To replace the character under the cursor, type `r` and then the character you want to have there.
* The change operator allows you to change from the cursor to where the motion takes you. e.g. Type `ce` to change from the cursor to the end of the word, `c$` to change to the end of a line.
* The format for change is: `c   [number]   motion`

### Lesson 4 SUMMARY

* `CTRL-G` displays your location in the file and the file status.
  * `G` moves to the end of the file. 
  * `number G` moves to that line number.
  * `gg` moves to the first line.
* After a search type `n` to find the next occurrence in the same direction or `N` to search in the opposite direction. `CTRL-O` takes you back to older positions, `CTRL-I` to newer positions.
  * Typing `/` followed by a phrase searches FORWARD for the phrase.
  * Typing `?` followed by a phrase searches BACKWARD for the phrase. 
* Typing `%` while the cursor is on a `(`,`)`,`[`,`]`,`{`, or `}` goes to its match.

| Substitution | cmd |
| :--- | :--- |
| To substitute new for the first old in a line | :s/old/new |
| To substitute new for all 'old's on a line |  :s/old/new/g |
| To substitute phrases between two line \#'s | :\#,\#s/old/new/g |
| To substitute all occurrences in the file | :%s/old/new/g |
| To ask for confirmation each time add 'c' | :%s/old/new/gc |

### Lesson 5 SUMMARY

* `:!command` executes an external command.

Some useful examples are:

| \(Windows\) | \(Unix\) |  |
| :--- | :--- | :--- |
| :!dir | :!ls | shows a directory listing |
| :!del FILENAME | :!rm FILENAME | removes file FILENAME |

* `:w` FILENAME writes the current Vim file to disk with name FILENAME.
* `v` motion `:w FILENAME` saves the Visually selected lines in file FILENAME.
* `:r` FILENAME retrieves disk file FILENAME and puts it below the cursor position.
* `:r !dir` reads the output of the `dir` command and puts it below the cursor position.

### Lesson 6 SUMMARY

* Type `o` to open a line BELOW the cursor and start Insert mode.
* Type `O` to open a line ABOVE the cursor.
* Type `a` to insert text AFTER the cursor.
* Type `A` to insert text after the end of the line.
* The `e` command moves to the end of a word.
* The `y` operator yanks \(copies\) text, `p` puts \(pastes\) it.
* Typing a capital `R` enters Replace mode until `<ESC>` is pressed.
* Typing ":set xxx" sets the option "xxx". Some options are: 

  * 'ic' 'ignorecase' ignore upper/lower case when searching
  * 'is' 'incsearch' show partial matches for a search phrase
  * 'hls' 'hlsearch' highlight all matching phrases

  You can either use the long or the short option name.

* Prepend "no" to switch an option off: `:set noic`

### Lesson 7 SUMMARY

* Type `:help` or press `<F1>` or `<HELP>` to open a help window.
* Type `:help cmd` to find help on `cmd`.
* Type `CTRL-W CTRL-W` to jump to another window.
* Type :q to close the help window.
* Create a vimrc startup script to keep your preferred settings.
* When typing a : command, press `CTRL-D` to see possible completions. Press `<TAB>` to use one completion.





