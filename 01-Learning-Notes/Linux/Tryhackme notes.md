# Linux Commands Notes

* `echo "text"` - to display text on screen
* `whoami` - to display the current user (Note: use `pwd` to display current working directories)
* `ls` - used to list the files and folders in current directory
* `cd` - to change directory
* `cat` - to display contents of the file
* `pwd` - to print current working directory
* `find -name file_name.txt` - to find a file in the device
* `wc` - to count the number of entries
* `grep "text" file_name.txt` - to find text in file_name.txt
* `grep -R "text" /Directory` - to find text in all files in directory folder and all its sub folders
* `&` or `ctrl + z` - is used to run command in background
* `command1 && command2` - `&&` used to run command2 after successful completion of command1
* `echo text > file_name` - `>` sends text into file
* `echo text >> file_name` - `>>` sends text into bottom of the file without clearing past data
* `ssh username@ip_address` - to connect securely to a remote device
* `ls -a` - `-a` shows entries starting with `.` (hidden files)
* `--help` - to list the possible options that the command accepts
* `man command` - to see manual for the command
* `touch file_name` - to create a file
* `mkdir folder_name` - to create a folder
* `rm file` - to remove a file
* `rm -R folder` - to remove a folder
* `cp file1 file2` - copy from file1 to file2
* `mv file1 file2` - move file1 contents to file2
* `file file_name` - show file type
* `su user_name` - to switch users
* `nano file_name` - nano is a terminal-based file editor
* `scp file_name username@ip_address:file/location` - to transfer file data from the attack device to a remote device
* `scp username@ip_address:file/location file_name` - to transfer file data from a remote device to the attack device
* `python3 -m http.server` - `-m` tells the Python interpreter to locate a specific built-in or installed module and execute it as a script
* `wget http://ip_address/file_name` - to download a file from server hosted device
* `top` - gives you real-time statistics about the processes running on your system instead of a one-time view
* `kill pid` - kills the process with given id
* `systemctl option service` - to make a process turn on during boot
