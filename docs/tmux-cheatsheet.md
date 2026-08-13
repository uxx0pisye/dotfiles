# Tmux Cheatsheet

## Sessions
- `tmux new -s name` — new session
- `tmux ls` — list sessions
- `tmux attach -t name` — attach
- `Ctrl-b d` — detach

## Windows & Panes
- `Ctrl-b c` — new window
- `Ctrl-b ,` — rename window
- `Ctrl-b %` — split vertical
- `Ctrl-b "` — split horizontal
- `Ctrl-b arrow` — move between panes

## Misc
- `Ctrl-b z` — zoom pane
- `Ctrl-b [` — copy mode (q to exit)
- `Ctrl-b ?` — list all key bindings

## Resize pane
- `Ctrl-b :resize-pane -D 10` (or -U, -L, -R)

## Kill
- `Ctrl-b x` — kill pane
- `tmux kill-session -t name` — kill session
