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


     