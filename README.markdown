To use it:
````bash
tmux-manager <project> # launch it with rails 3 configuration
tmux-manager <project> engine # launch it with engine configuration
tmux-manager <project> rails2 # launch it with rails 2 configuration
````

Sample configuration:
````
set -sg escape-time 1
set -g base-index 1
set-window-option -g pane-base-index 1
set-window-option -g automatic-rename off

# pane configuration
bind | split-window -h
bind - split-window -v

bind h select-pane -L
bind j select-pane -D
bind k select-pane -U
bind l select-pane -R

bind -r H resize-pane -L 5
bind -r J resize-pane -D 5
bind -r K resize-pane -U 5
bind -r L resize-pane -R 5

# maximize a pane
unbind Up
bind Up new-window -d -n tmp \; swap-pane -s tmp.1 \; select-window -t tmp
unbind Down
bind Down last-window \; swap-pane -s tmp.1 \; kill-window -t tmp

# mouse configuration
setw -g mode-mouse off

# vim mode
setw -g mode-keys vi
unbind [
bind Escape copy-mode
unbind p
bind p paste-buffer
bind -t vi-copy 'v' begin-selection
bind -t vi-copy 'y' copy-selection

# custom design
set -g default-terminal "screen-256color"
set -g status-fg white
set -g status-bg black

setw -g window-status-fg cyan
setw -g window-status-bg default
setw -g window-status-attr dim

setw -g window-status-current-fg white
setw -g window-status-current-bg red
setw -g window-status-current-attr bright

set -g pane-border-fg green
set -g pane-active-border-fg yellow

set -g message-fg white
set -g message-bg black
set -g message-attr bright

set -g status-left-length 40
set -g status-left "#[fg=green]Session: #S #[fg=yellow]#I #[fg=cyan]#P"
set -g status-right "#[fg=cyan]%d %b %R"

set -g status-utf8 on
set -g status-interval 60
set -g status-justify centre
setw -g monitor-activity on
set -g visual-activity on
````