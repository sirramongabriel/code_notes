# Vim
Model editing: A number of different keyboards that change meaning depending on the mode.

### Navigation

    ^E - scroll window down
    ^Y - scroll window up
    ^I - scroll down one page
    ^B - scroll up one page
    H - move curser to top of window
    M - move curser to middle of window
    L - move curser to bottom of window
    gg - go to top of file
    G - go to bottom of file

 Switch between buffers
 
    ^ + ww 
    ^ _ w (h,j,k,l) i.e. ^wh moves to buffer on the left

### Text Objects

    w - words
    s - sentences
    p - paragraphs
    t - tags
    
### Motions
    
    a - all
    i - in 
    t - 'til (until)
    f - find forward
    F - find backward
    
### Commands

    d - delete (also cut)
    c - change (delete, then place in insert mode)
    y - yank (copy)
    v - visually select
    
### In action

    diw - delete in word
    dis - delete in sentence
    di" - delete in " "
    dip - delete in paragraph
    dit - delete in tag
    
    caw - change all word 
    ciw - change in word
    ctw - change until word
    cip - change in paragraph
    cis - change in sentence
    
    yi) - yank(copy) all text inside parenthesis
    yi' - yank(copy) all text inside single-quotes
    yaw - yank(copy) all of the word
    
    va" - visually select all inside double-quotes, including the quotes
    vi" - visually select all inside double-quotes, not including the quotes
    
### Additional Commands

    The dot (.) command - repeats most recent vim command
    p  - paste below current line
    P  - paste above current line
    dd - delete the current line
    yy - yank(copy) the current line
    D  - delete until end of line
    C  - change until end of line
    I  - move to beginning of line
    A  - move to end of line
    o  - insert new line above current line and enter insert mode
    O  - insert new line below current line and enter insert mode
    t. - duplicate line (like atom/sublime's [cmd+d])
    t7 - copy after line 7
    
### Using tab pages

##### Open/close tabs
When starting vim, the <code>-p flag</code> opens each specified file in a separate tab (up to the value of 'tabpagemax' option)

    - vim -p first_file.py second_file.rb
    - vim -p *.txt *.md

Once in vim thera are many commands that can directly create/close tabs

    - :tabedit {file_name} - edits file in a new tab
    - :tabfind {file_name} - open new tab with file_name given, searching the 'path' to locate the file
    - :tabclose - closes current tab
    - :tabclose {i} close i-th tab
    - :tabonly - close all other tabs, show only the current tab
    - :tabe <file_name>

##### :tab command-line modifier

    - :tab ball - show each buffer in a tab
    - :tab help - open new help window in it's own tab page
    - :tab drop {file_name} - open file in new tab or jump to a new tab of it's own
    - :tab split - copy current window to a new tab of it's own
    - :sp my_file.txt - creates a new window in the current tab, editing the specified file
    - ^W T - movew window to a new tab
    - :tab sp - splits current window but open this split in a new tab
    - ^W c closes current window and closes tab if it's the last visible window

    
If the current file contains the name of another file, place cursor on the name & type 'gf' to edit (go to file) the file. Typing ^W 'gf' displays the file in a new tab.

##### Tab Navigation

    - :tabs - listsl all tabs including their displayed windows
    - :tab 0 - moves current tab into first place
    - :tab m - moves current tab into last place
    - :tabm{i} - moves current tab into position (i + 1)
    - :tabn - go to next tab
    - :tabp - go to previous tab
    - :tabfirst - go to first tab
    - :tablast - go to last tab

##### Tab Navigation in Normal Mode

    - gt - got to next tab
    - gT - go to previous tab
    - {i}gt - go to tab in position {i}
