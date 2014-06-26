drun - A gtk run dialog
=======================

Features
--------

- Tab completion
- History
- Runs files, directories, urls, and executables
- Runs on thunar/nautilus file and directory selections
- Spelling correction
- Recursive directory completion
- Completions ordered using history
- Completes parameters from history

<h2>Installing</h2>

Requirements:

- ruby
- ruby-gnome2
- gtk+

Download and extract the archive. Copy drun to somewhere in the system path such as /usr/local/bin.
It can then be run by executing 'drun'.

Usage
-----

Type in a command, and press return to run it. Tab, up, and down can be used to
cycle through possible completions for that command. Delete can be used to remove
a completion from the list and history. Escape dismisses the completions or exits.
Return runs a command, and Shift+Return runs a command in a terminal. Control+R toggles
a bash style reverse interactive search. Alt+up changes to the parent directory, Alt+down
changes back to the last directory.

If you press tab on an empty entry, then you will get a list of recently run commands
in the order that you last ran them. Otherwise, it will attempt to complete an executable,
directory, or file. The completions will then be ordered by how many times they were previously
run. A name beginning with an equals symbol will be expanded based on where it is located in
the system path. A '*' can be used in a path as a glob operator. If no completions are found,
then your input will be manipulated based on spell checking to find any possible completions.

The programs used to run files, directories, and urls can be edited in ~/.drunrc:

	http-handler = firefox
	ssh-handler = xterm -e ssh
	file-handler = gnome-open
	directory-handler = nautilus
	terminal-handler = xterm -e

Normally, drun will run commands in the current directory it was launched in.
If a single directory is passed in as a parameter, then it will run the command in that directory.
If a non-directory or multiple files are passed in as a parameter, then it will run the command in the directory of the first parameter, and
append the list of files to the end of the command.

Custom run actions can be added to thunar's right-click menu by configuring them from thunar's edit menu. For example, use `drun %N` to as a
"Run" command, and `drun` as a "Run in Directory" command.

Windows Support
---------------

Some support for windows has been added.

First, install the dependencies: [Ruby](http://rubyinstaller.org/) and
[ruby-gnome2](http://prdownloads.sourceforge.net/ruby-gnome2/ruby-gnome2-0.16.0-1-i386-mswin32.exe?download)
(See ruby gnome's [Install guide for Windows](http://ruby-gnome2.sourceforge.jp/hiki.cgi?Install+Guide+for+Windows)).
Then the ruby program can be run by opening it with "rubyw.exe / Ruby interpreter (GUI)".

If you create a shortcut to the program, but add " --shortcut" to the end of the target field in the properties dialog, then
launching the shortcut will cause the program to run in the background. The dialog then can be shown at any time by pressing Win+w.
The shortcut can be placed in the startup items folder so it runs on system startup.

Configuration files are stored in the profile home (eg c:\documents and settings\user).
Backslashes or forward slashes can be used for directory separators. Backslashes followed by a letter don't need to be escaped.
Paths are quoted with double quotes to allow paths with spaces (backslashes can't be used to escape paths as they are used for directory separators instead).
ssh-handler, and terminal-handler don't have reasonable defaults for Windows. The other handlers should work though.
If the first path is a shortcut, it is resolved to its target. Other paths are unchanged.
