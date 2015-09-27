# tmuxinator
###Executing commands sequentially in different panes and windows

Open terminal

$ sudo apt-get install tmux

$ sudo apt-get install ruby

$ sudo su

$ gem install tmuxinator

Exit from su

The directory .tmuxinator contains the config file.

$ export EDITOR='gedit'

$ echo $EDITOR

Ignore if already included in ~/.bashrc

###To start new session

$ tmux new-session

Result:A green strip must appear at bottom

###To create a new project session:

$ mux new project_name

Result:config file opens in default editor 
###Writing the config file

A default config file will look like this:

####### ~/.tmuxinator/sample.yml

name: sample
root: ~/

####### Optional. tmux socket
####### socket_name: foo

####### Runs before everything. Use it to start daemons etc.
####### pre: sudo /etc/rc.d/mysqld start

####### Runs in each window and pane before window/pane specific commands. Useful for setting up interpreter versions.
####### pre_window: rbenv shell 2.0.0-p247

####### Pass command line options to tmux. Useful for specifying a different tmux.conf.
####### tmux_options: -f ~/.tmux.mac.conf

####### Change the command to call tmux.  This can be used by derivatives/wrappers like byobu.
####### tmux_command: byobu

####### Specifies (by name or index) which window will be selected on project startup. If not set, the first window is used.
####### startup_window: logs

windows:
  - editor:
      layout: main-vertical
      panes:
        - vim
        - guard
  - server: bundle exec rails s
  - logs: tail -f log/development.log

