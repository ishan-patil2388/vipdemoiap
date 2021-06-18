***************************
GVIM Commands
***************************



Global Commands
==================
.. list-table::  LIST
   :widths: 25 25
   :header-rows: 1

   * -  Commands
     -  Description
   * - :help keyword 
     -  open help for keyword
   * - :close 
     -  close current pane
   * - :saveas file 
     -  save file as
   * -  K 
     -  open man page for word under the cursor

Cursor movement
==================
.. list-table::  Cursor movement
   :widths: 25 25
   :header-rows: 1

   * -  Commands
     -  Description
   * - h 
     -   move cursor left
   * - j 
     -   move cursor down
   * - k 
     -   move cursor up
   * - l 
     -   move cursor right
   * - H 
     -   move to top of screen
   * - M 
     -   move to middle of screen
   * - L 
     -   move to bottom of screen
   * - w 
     -   jump forwards to the start of a word
   * - W 
     -   jump forwards to the start of a word (words can contain punctuation)
   * - e 
     -   jump forwards to the end of a word
   * - E 
     -   jump forwards to the end of a word (words can contain punctuation)
   * - b 
     -   jump backwards to the start of a word
   * - B 
     -   jump backwards to the start of a word (words can contain punctuation)
   * - % 
     -   move to matching character (default supported pairs: '()', '{}', '[]' 
   * - 0
     -   jump to the start of the line
   * - ^ 
     -   jump to the first non
   * - $ 
     -   jump to the end of the line
   * - g_ 
     -   jump to the last non
   * - gg 
     -   go to the first line of the document
   * - G 
     -   go to the last line of the document
   * - 5G 
     -   go to line 5
   * - fx 
     -   jump to next occurrence of character x
   * - tx 
     -   jump to before next occurrence of character x
   * - Fx 
     -   jump to previous occurence of character x
   * - Tx 
     -   jump to after previous occurence of character x
   * - ; 
     -   repeat previous f, t, F or T movement
   * - , 
     -   repeat previous f, t, F or T movement, backwards
   * - } 
     -   jump to next paragraph (or function/block, when editing code)
   * - { 
     -   jump to previous paragraph (or function/block, when editing code)
   * - zz 
     -   center cursor on screen
   * - Ctrl + e 
     -   move screen down one line (without moving cursor)
   * - Ctrl + y 
     -   move screen up one line (without moving cursor)
   * - Ctrl + b 
     -   move back one full screen
   * - Ctrl + f 
     -   move forward one full screen
   * - Ctrl + d 
     -   move forward 1/2 a screen
   * - Ctrl + u 
     -   move back 1/2 a screen

.. note::
      Tip Prefix a cursor movement command with a number to repeat it. For example, 4j moves down 4 lines.

Insert mode  
============
.. list-table::  Inserting/Appending text
   :widths: 25 25
   :header-rows: 1   

   * -  Commands
     -  Description
   * - i 
     -   insert before the cursor
   * - I 
     -   insert at the beginning of the line
   * - a 
     -   insert (append) after the cursor
   * - A 
     -   insert (append) at the end of the line
   * - o 
     -   append (open) a new line below the current line
   * - O 
     -   append (open) a new line above the current line
   * - ea 
     -   insert (append) at the end of the word
   * - Esc 
     -   exit insert mode


File Editing  
=============
.. list-table::  Editing text
   :widths: 25 25
   :header-rows: 1      

   * -  Commands
     -  Description
   * - r 
     -   replace a single character
   * - J 
     -   join line below to the current one with one space in between
   * - gJ 
     -   join line below to the current one without space in between
   * - gwip 
     -   reflow paragraph
   * - cc 
     -   change (replace) entire line
   * - c$ 
     -   change (replace) to the end of the line
   * - ciw 
     -   change (replace) entire word
   * - cw 
     -   change (replace) to the end of the word
   * - s 
     -   delete character and substitute text
   * - S 
     -   delete line and substitute text (same as cc)
   * - xp 
     -   transpose two letters (delete and paste)
   * - u 
     -   undo
   * - Ctrl + r 
     -   redo
   * - . 
     -   repeat last command

Marking text  
============
.. list-table::  Marking text (visual mode)
   :widths: 25 25
   :header-rows: 1      

   * -  Commands
     -  Description
   * - v 
     -   start visual mode, mark lines, then do a command (like y yank)
   * - V 
     -   start linewise visual mode
   * - o 
     -   move to other end of marked area
   * - Ctrl + v 
     -   start visual block mode
   * - O 
     -   move to other corner of block
   * - aw 
     -   mark a word
   * - ab 
     -   a block with ()
   * - aB 
     -   a block with {}
   * - ib 
     -   inner block with ()
   * - iB 
     -   inner block with {}
   * - Esc 
     -   exit visual mode

Visual commands  
===============
.. list-table::  Visual commands
   :widths: 25 25
   :header-rows: 1      

   * -  Commands
     -  Description
   * - > 
     -   shift text right
   * - < 
     -   shift text left
   * - y 
     -   yank (copy) marked text
   * - d 
     -   delete marked text
   * - ~ 
     -   switch case

Registers  
============
.. list-table::  Registers
   :widths: 25 25
   :header-rows: 1      

   * -  Commands
     -  Description
   * - :reg 
     -   show registers content
   * - "xy
     -  yank into register x
   * - "xp
     -  paste contents of register x


.. note::
      Tip Registers are being stored in ~/.viminfo, and will be loaded again on next restart of vim.
      Tip Register 0 contains always the value of the last yank command.

Marks  
============
.. list-table::  Marks
   :widths: 25 25
   :header-rows: 1      

   * -  Commands
     -  Description
   * - :marks 
     -   list of marks
   * - ma 
     -   set current position for mark A
   * - `a 
     -   jump to position of mark A
   * - y`a 
     -   yank text to position of mark A

Macros 
============
.. list-table::  Macros
   :widths: 25 25
   :header-rows: 1      

   * -  Commands
     -  Description
   * - qa 
     -   record macro a
   * - q 
     -   stop recording macro
   * - @a 
     -   run macro a
   * - @@ 
     -   rerun last run macro

.. note::
      Tip Prefix a cursor movement command with a number to repeat it. For example, 4j moves down 4 lines.

Cut and paste  
=============
.. list-table::  Cut and paste
   :widths: 25 25
   :header-rows: 1      

   * -  Commands
     -  Description
   * - yy 
     -   yank (copy) a line
   * - 2yy 
     -   yank (copy) 2 lines
   * - yw 
     -   yank (copy) the characters of the word from the cursor position to the start of the next word
   * - y$ 
     -   yank (copy) to end of line
   * - p 
     -   put (paste) the clipboard after cursor
   * - P 
     -   put (paste) before cursor
   * - dd 
     -   delete (cut) a line
   * - 2dd 
     -   delete (cut) 2 lines
   * - dw 
     -   delete (cut) the characters of the word from the cursor position to the start of the next word
   * - D 
     -   delete (cut) to the end of the line
   * - d$ 
     -   delete (cut) to the end of the line
   * - x 
     -   delete (cut) character

.. note::
      Tip Prefix a cursor movement command with a number to repeat it. For example, 4j moves down 4 lines.

Exiting  
============
.. list-table::  Exiting Commands
   :widths: 25 25
   :header-rows: 1      

   * -  Commands
     -  Description
   * - :w 
     -   write (save) the file, but don't exit
   * - :w !sudo tee % 
     -   write out the current file using sudo
   * - :wq or :x or ZZ 
     -   write (save) and quit
   * - :q 
     -   quit (fails if there are unsaved changes)
   * - :q! or ZQ 
     -   quit and throw away unsaved changes
   * - :wqa 
     -   write (save) and quit on all tabs

Search and replace  
==================
.. list-table::  Search and replace text
   :widths: 25 25
   :header-rows: 1      

   * -  Commands
     -  Description

   * - /pattern 
     -   search for pattern
   * - ?pattern 
     -   search backward for pattern
   * - \vpattern 
     -   'very magic' pattern: non-alphanumeric characters are interpreted as special regex symbols (no escaping needed)
   * - n 
     -   repeat search in same direction
   * - N 
     -   repeat search in opposite direction
   * - :%s/old/new/g 
     -   replace all old with new throughout file
   * - :%s/old/new/gc 
     -   replace all old with new throughout file with confirmations
   * - :noh 
     -   remove highlighting of search matches

Search in multiple files 
========================
.. list-table::  Search in multiple files
   :widths: 25 25
   :header-rows: 1      

   * -  Commands
     -  Description
   * - :vimgrep /pattern/ {file} 
     -   search for pattern in multiple files
   * - 
     -  e.g. :vimgrep /foo/ **/*
   * - :cn 
     -   jump to the next match
   * - :cp 
     -   jump to the previous match
   * - :copen 
     -   open a window containing the list of matches

Working with multiple files  
===========================
.. list-table::  Working with multiple files
   :widths: 25 25
   :header-rows: 1      

   * -  Commands
     -  Description
   * - :e file 
     -   edit a file in a new buffer
   * - :bnext or :bn 
     -   go to the next buffer
   * - :bprev or :bp 
     -   go to the previous buffer
   * - :bd 
     -   delete a buffer (close a file)
   * - :ls 
     -   list all open buffers
   * - :sp file 
     -   open a file in a new buffer and split window
   * - :vsp file 
     -   open a file in a new buffer and vertically split window
   * - Ctrl + ws 
     -   split window
   * - Ctrl + ww 
     -   switch windows
   * - Ctrl + wq 
     -   quit a window
   * - Ctrl + wv 
     -   split window vertically
   * - Ctrl + wh 
     -   move cursor to the left window (vertical split)
   * - Ctrl + wl 
     -   move cursor to the right window (vertical split)
   * - Ctrl + wj 
     -   move cursor to the window below (horizontal split)
   * - Ctrl + wk 
     -   move cursor to the window above (horizontal split)
   * - Ctrl + wT 
     -   move the current split window into its own tab

Tabs  
============
.. list-table::  Tab Operations
   :widths: 25 25
   :header-rows: 1      

   * -  Commands
     -  Description
   * - :tabnew <File-Name with absolute path>
     -  It will open a specified file in new tab
   * - :tabfind <File-Name>
     -  It will find a file in a directory recursively and then open it in a new tab.
        Before using this command, we need to set a path to determine which directories 
        should be searched when opening the specified file. To set a path below command is used.
   * - :set path=.,,**
     -  It will set a path for current directory. After setting this path, we can use tabfind command. 
   * - :tabfind
     -  command will tell to gvim to find a file in:
        1. directory containing current file (“.” in :set path command)
   * - 
     -  2. current directory (“empty text between two cammas” in :set path command)
   * - 
     -  3. directories under the current directory (“**” in a :set path command)
   * - :tab help
     -  It will open a new help window tab for gvim
   * - :tab drop <File-Name>
     -  It will open a file in a new tab or jump to a window/tab containing the file if it is open
   * - :tab split
     -  Copy a current window to a new tab of its own
   * - :tabs
     -  List all tabs including their display window
   * - :tabm 0 or :tabfirst
     -  Move current tab to first position
   * - :tabm or :tablast
     -  Move current tab to last position
   * - :tabm {i}
     -  Move current tab to (i+1)th position
   * - :tabp
     -  Go to previous tab
   * - :tabn
     -  Go to next tab

Command in Normal Mode  
=======================
.. list-table::  Command in Normal Mode
   :widths: 25 25
   :header-rows: 1      

   * -  Commands
     -  Description
   * - gt or :tabnext or :tabn 
     -   move to the next tab
   * - gT or :tabprev or :tabp 
     -   move to the previous tab
   * - <i>gt
     -  Go to ith tab
   * - #gt 
     -   move to tab number #
   * - :tabmove # 
     -   move current tab to the #th position (indexed from 0)
   * - :tabclose or :tabc 
     -   close the current tab and all its windows
   * - :tabonly or :tabo 
     -   close all tabs except for the current one
   * - :tabdo command 
     -   run the command on all tabs (e.g. :tabdo q 

.. note::
      Command in Normal Mode (above commands are in insert mode, where we have to use colon (:) to execute).

special commands  
=================
.. list-table::  Platinium User Commands
   :widths: 25 25
   :header-rows: 1      

   * -  Commands
     -  Description
   * - *
     -  search a word: place cursor on any word to be searched and press *
   * - 
     -  To find next occurrence press n To find previous occurrence press N
   * - :g//d
     -  This will deletes the lines which contains previous
   * - searched pattern:g!//d
     -  This will deletes the other  lines which doesn’t contains previous searched pattern
   * - “ctrl+v”  then  “down” or “up”  then
     -  Visual Mode:
   * -  “I” then “pattern1” then “esc”
     -  Pattern (Adding any text) will be added at the place of selection.
   * - gf
     -  open the file name under cursor:Place a cursor on file path and press gf.
   * - Ctrl+w+f
     -  split window and open a file:place a cursor on file path and press  Ctrl+w+f
   * - ctrl+p
     -  Auto fill.  While typing ctrl+p will shows the auto fill word’s (search signals)
   * - ctrl+x+f
     -  Auto fill the path.While typing any path,ctrl+x+f auto fills the path
   * - :%s/flower/rose/gc
     -  Replace the string flower by rose.,g – indicates global,c-conditional replacement, asks for replacement
   * - :%s/^/rose/gc
     -  add rose in beginning of all the line
   * - ctrl+a
     -  Increment number.Place cursor on any number and press "ctrl+a", then the number will be incremented by 1.
   * - ctrl+x
     -  Decrements number.Place cursor on any number and press "ctrl+x", then the number will be decremented by 1.
   * - Ctrl+j
     -  To wrap text
   * - :s/^/\t/
     -  To add Tab in previous line
   * - :s/^/\/\/
     -  To add comment in starting of the line
   * - ctrl+w then =
     -  to bring windows same size
   * - >
     -             give space before
   * - <
     -  To remove before sapce(indentd)
   * - "="
     -  To proper indent code
   * - gg then = then G
     -  To poper aligned program automatically
   * - ~
     -  change char small to cap or cap to small
   * - %
     -  to jump bracket
   * - % > or %<
     -  To shift bracket code to left or rigth
   * - di(
     -  To delete the data in ()
   * - di'
     -  Delete the data in ' '
   * - dip
     -  delete the paragraph
   * - ds"
     -  delete the surround "
   * - ys"
     -  to surround "
   * - ctrl+p
     -  for forword movement
   * - ctrl+o
     -  for previous movement
   * - 20,30s/\(.*\)/\t\t.\1(mem_pif.\1),/
     -  For module instatiation
   * - :s/.*\]//
     - To delete all previous data including ] 
   * - :s/\%d20c/abc 
     -  To print abc from 20 coloumn
   * - :%s/\(.*\n\)\{5\}/&\r/
     -      Insert a blank line every 5 lines

Feature Control Commands  
=========================
.. list-table::  Feature Control Commands 
   :widths: 25 25
   :header-rows: 1      

   * -  Commands
     -  Description
   * -  set nu                  
     -  Display line numbers  
   * -  set autoindent     
     -  Set Auto Indentation during text entry
   * -  set showmatch    
     -  Show Matching ( or { when ) or } is entered
   * -  set ignorecase     
     -  Set Ignore Case during searches
   * -  set colorcolumn=x
     -  \ -- Draw the color line
   * -  set ruler
     -  It will set the ruler
