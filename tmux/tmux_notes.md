# tmux

^b - gets tmux's attention, so talking to tmux syntax is 

```
^b + <command>
```
### Commands

    ^b + c - opens new window
    ^b + , - renames window while inside of it
    
##### Navigation of windows

Move to different windows

    ^b + p - previous window
    ^b + n - next window
    ^b + w - list windows
    
##### Navigation of panes

Panes are splits inside a window

    ^b + % - split window vertically
    ^b + : - split window horizontally
    
##### Sessions

    tmux new -s <new_session_name> - creates a new tmux session named 'new_session_name'
    
    ^b + d or tmux detach - detach the curretnly attached session
    
    tmux list-sessions - lists existing tmux sessions
    
    tmux attach -t <session_name> - attaches to an existing session named 'session_name'
    
    tmux switch -t <session_name> - switches to an existing session named 'session_name'
    
    tmux kill-sessions - destroys all tmux sessions
    
    tmux kill-session <session_name> - kills specified tmux session
    
    pkill -f tmux or tmux kill-server - ends all tmux sessions
    
    tmux kill-session -a - closes all other sessions except the one you are in


     
#tmux shortcuts & cheatsheet

<i>[source: github](https://gist.github.com/MohamedAlaa/2961058)</i>

start new: 

```ruby 
tmux
```

start new with session name: 

```ruby
tmux new -s <session_name>
```

attach to session:

```ruby
tmux a # (or at, or attach)
```

attatch to named: 

```ruby
tmux a -t <name>
```

list sessions:

```ruby
tmux ls
```

kill session: 

```ruby
tmux kill-session -t <session_name>
```

end tmux (kill all session):

```ruby
tmux kill-server
```

## Windows (tabs)

note: all commands prefixed with ' ```^b``` '

```ruby
i.e. ^b + c - create window/tab
```

```ruby
c - create window
w - list window
n - next window
p - previous window
f - find window
, - name window
& - kill window
```


## Panes (splits)
```ruby
% - vertical split
" - horizontal split
o - swap panes
q - show pane numbers
x - kill pane
+ - break pane into window 
- - restore pane from window
spacebar - toggle between layouts
q - show pane #s, when #s show up type the key to goto that pane
{ - move current pane left
} - move current pane right
z - toggle pane zoom
```

## Resizing Panes

```ruby 
all commands prefixed with ^b
```

```ruby
resize-pane -D (resizes current pane down)
resize-pane -U (resizes current pane upward)
resize-pane -L (resizes current pane left)
resize-pane -R (resizes current pand right)
resize-pane -D 20 (resizes current pane down by 20 cells)
resize-pane -U 20 (resizes current pane up by 20 cells)
resize-pane -L 20 (resizes current pane left by 20 cells)
resize-pane -R 20 (resizes current pane right by 20 cells)
resize-pane -t -D 2 20 (resizes pane with id of 2 down by 20 cells)
```