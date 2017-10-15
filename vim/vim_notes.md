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
    p - paste below current line
    P - paste above current line
    dd - delete the current line
    yy - yank(copy) the current line
    D - delete until end of line
    C - change until end of line
    I - move to beginning of line
    A - move to end of line
    o - insert new line above current line and enter insert mode
    O - insert new line below current line and enter insert mode