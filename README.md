.tmux.conf 
================================================================

Self-contained, pretty and versatile `.tmux.conf` configuration file.


Installation
------------

Requirements:

  - tmux **`>= 3.0`** running inside Linux
  - outside of tmux, `$TERM` must be set to `xterm-256color`

## Installation
⚠️ Before installing, you may want to backup your existing configuration.
1. Clone this repository
2. Copy `.tmux.conf` to your home directory
3. Run `tmux source-file ~/.tmux.conf`
   
Installing in `~`:
```
$ cd
$ git clone https://github.com/ayanul/tmux.git
$ cp .tmux/.tmux.conf ~/.tmux.conf
// or create link
$ ln -s -f .tmux/.tmux.conf ~/.tmux.conf
```

If you're a Vim user, setting the `$EDITOR` environment variable to `vim` will
enable and further customize the vi-style key bindings (see [tmux manual]((https://github.com/tmux/tmux/wiki))).

If you're new to tmux, I recommend you to read [Welcome to tmux!](https://github.com/tmux/tmux/wiki).


Bindings
--------

tmux may be controlled from an attached client by using a key combination of a
prefix key, followed by a command key. This configuration uses `C-a` as a
secondary prefix while keeping `C-b` as the default prefix. In the following
list of key bindings:
  - `<prefix>` means you have to either hit <kbd>Ctrl</kbd> + <kbd>a</kbd> or <kbd>Ctrl</kbd> + <kbd>b</kbd>
  - `<prefix> c` means you have to hit <kbd>Ctrl</kbd> + <kbd>a</kbd> or <kbd>Ctrl</kbd> + <kbd>b</kbd> followed by <kbd>c</kbd>
  - `<prefix> C-c` means you have to hit <kbd>Ctrl</kbd> + <kbd>a</kbd> or <kbd>Ctrl</kbd> + <kbd>b</kbd> followed by <kbd>Ctrl</kbd> + <kbd>c</kbd>

The following custom configurations are used:

| Key Binding | Command | Action |
| --- | --- | --- |
| `<prefix>` + <kbd>a</kbd> | send-prefix | Prefix key |
| `<prefix>` + <kbd>e</kbd> | setw synchronize-panes on | Synchronize panes on |
| `<prefix>` + <kbd>E</kbd> | setw synchronize-panes off | Synchronize panes off |
| `<prefix>` + <kbd>R</kbd> | refresh-client | Refresh client |
| `<prefix>` + <kbd>r</kbd> | source-file ~/.tmux.conf | Reloaded tmux config. |
| `<prefix>` + <kbd>q</kbd> | confirm-before kill-pane | Kill pane and window confirmation |
| `<prefix>` + <kbd>Q</kbd> | confirm-before kill-window | Kill pane and window confirmation |
| `<prefix>` + <kbd>C-q</kbd> | confirm-before kill-session | Kill session confirmation |
| `<prefix>` + <kbd>M-t</kbd> | new-session | New session |
| `<prefix>` + <kbd>t</kbd> | new-window | New window |
| `<prefix>` + <kbd>c</kbd>,<kbd>C-t</kbd> |  | New window with and split horizontally |
| `<prefix>` + <kbd>_</kbd> | split-window -l 20 -c "#{pane_current_path}" node | Open panel with NodeJS |
| `<prefix>` + <kbd>g</kbd>,<kbd>C-g</kbd>,<kbd>_</kbd> | split-window | Splits the current pane vertically |
| `<prefix>` + <kbd>h</kbd>,<kbd>C-h</kbd>,<kbd>|</kbd> | split-window -h | Splits the current pane vertically |
| `<prefix>` + <kbd>n</kbd>,<kbd>C-n</kbd> | next-window | Select the next window. |
| `<prefix>` + <kbd>C-p</kbd> | previous-window | Select the previous window (by default) |
| `<prefix>` + <kbd>C-a</kbd> | last-window | Select the last window |
| `<prefix>` + <kbd>C-O</kbd> | rotate-window | Rotate window |
| `<prefix>` + <kbd>space</kbd> | select-pane -t:.+ | Select pane by mouse click |
| `Ctrl` + <kbd>h</kbd>,<kbd>j</kbd>,<kbd>k</kbd>,<kbd>l</kbd> | tmux select-pane -`L,U,L,R` | Let you navigate panes ala Vim |
| `<prefix>` + <kbd>H</kbd>,<kbd>J</kbd>,<kbd>K</kbd>,<kbd>L</kbd> | resize-pane -`L,U,L,R` 50 | Resize the pane down by 50 |
| `<prefix>` + <kbd>up</kbd>,<kbd>down</kbd>,<kbd>left</kbd><kbd>right</kbd> | resize-pane -`L,U,L,R` 5 | Resize the pane down by 5 |
| `<prefix>` + <kbd>M-o</kbd> | display-panes | display a visible indicator of each pane shown by target-client. |
| `<prefix>` + <kbd>C-l</kbd> |  | Clear console |
| `<prefix>` + <kbd>b</kbd> | list-buffers | List buffers |
| `<prefix>` + <kbd>P</kbd> | choose-buffer | Lets you choose the paste-buffer to paste from |
| `<prefix>` + <kbd>x</kbd> | delete-buffer | Delete buffer |
| `<prefix>` + <kbd>?</kbd> |  | List key bindings (by default) |
| ||||



Additionally, `copy-mode-vi` matches [my own Vim configuration][]

[my own Vim configuration]: https://github.com/gpakosz/.vim.git

Bindings for `copy-mode-vi`:

- <kbd>space</kbd> begins selection / visual mode
- <kbd>H</kbd> jumps to the start of line
- <kbd>L</kbd> jumps to the end of line
- <kbd>enter</kbd> copies the selection to the top paste-buffer
- <kbd>Escape</kbd> cancels the current operation

Theme
===

The main colors are put in separate constants. The color chart is shown below.
--------

```
color_orange="colour166" 
color_purple="colour135" 
color_green="colour076"  
color_blue="colour39"    
color_yellow="colour220"
color_red="colour160"
color_black="colour234"
color_white="colour253" 
color_gray="colour253"
```
The top panel is configured here
```
set -g status-left "$wg_session"
set -g status-right "#{prefix_highlight} $wg_is_keys_off $wg_is_zoomed #{sysstat_cpu} | #{sysstat_mem} | #{sysstat_swap} | #{sysstat_loadavg}"
```

You can use this table to customize the color
--------

![colour](https://user-images.githubusercontent.com/11617213/233860116-54911439-64d7-40ee-a88a-145ebc87f8e4.png)

Plugins
===

`prefix` + <kbd>I</kbd>
- Installs new plugins from GitHub or any other git repository
- Refreshes TMUX environment

`prefix` + <kbd>U</kbd>
- updates plugin(s)

`prefix` + <kbd>alt</kbd> + <kbd>u</kbd>
- remove/uninstall plugins not on the plugin list


The following plugins are used
--------

| Plugin | Description |  Link |
| --- | --- | --- | 
| tmux-plugins/tpm | Tmux Plugin Manager | https://github.com/tmux-plugins/tpm |
| tmux-plugins/tmux-prefix-highlight | Highlight Tmux prefix key | https://github.com/tmux-plugins/tmux-prefix-highlight |
| tmux-plugins/tmux-open | Open highlighted file or url | https://github.com/tmux-plugins/tmux-open |
| samoshkin/tmux-plugin-sysstat | Show system stats in Tmux status bar | https://github.com/samoshkin/tmux-plugin-sysstat |
| tmux-plugins/tmux-copycat | Enhance Tmux search | https://github.com/tmux-plugins/tmux-copycat |
| tmux-plugins/tmux-yank | Copy to system clipboard |  https://github.com/tmux-plugins/tmux-yank |
| tmux-plugins/tmux-resurrect | Save and restore Tmux sessions | https://github.com/tmux-plugins/tmux-resurrect |
| tmux-plugins/tmux-continuum | Continuous saving of Tmux environment | https://github.com/tmux-plugins/tmux-continuum |
| tmux-plugins/tmux-sensible | Basic Tmux settings |  https://github.com/tmux-plugins/tmux-sensible |

