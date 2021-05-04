# Linux commands

## Help

|Command|Example|Comment|
|--------|---|---|
|man `<command>`|man cd<br />man ls|**Manual** <br> Get help (close with <kbd>q</kbd>).|
|`<command>` --help|cd --help|Also **help**.|
|<kbd>Tab</kbd> (1x or 2x) |&nbsp; |Auto completion.|
|<kbd>↑</kbd>|&nbsp;|See previous command.|
|<kbd>Ctrl</kbd>+<kbd>C</kbd>|&nbsp;|Kill the current process or command (e.g. if something hangs).|
|<kbd>Ctrl</kbd>+<kbd>D</kbd>|&nbsp;|Logout. Closes the console if you're not in an ssh session. Similar to `exit`. |
|<kbd>Ctrl</kbd>+<kbd>R</kbd>|&nbsp;|Search through your history. Start typing and it will auto-complete. Hit <kbd>Ctrl</kbd>+<kbd>r</kbd> again and it will cycle though the other auto-completion options. Hit <kbd>Enter</kbd> and the command will execute. Hit <kbd>←</kbd>,<kbd>→</kbd> to edit commands.|

## Basics

|Command|Example|Comment|
|---|---|---|
|sudo `<command>`| sudo ls | **Super user do** <br> Run a command with elevated privleges. Will ask you for a password. Only possible, if you were granted administrative rights on the system.
|cd `<folder>`|cd test <br> cd .. <br> cd - <br> cd ~ <br> cd /path/to/my/folder | **Change directory** <br>. (dot) is the current directory <br> .. (dotdot) is the upper/partent directory <br> / (slash) is the root directory <br> ~ (tilde) is your home directory <br> - (minus) switches to the previous directory|
|ls <br> ls `<options>` <br> ls `<folder>` <br> ls `<pattern>` | ls <br> ls -la <br> ls -l -a (same as above) <br> ls -halt (more arguments) <br> ls -d */ (list all directories) <br> ls test (contents of subfolder) <br> ls *.txt (show only .txt files) | **List** contents of a folder <br> -h human readable <br> -a all <br> -l more information <br> -t order by time |
|mkdir `<folder>` |mkdir test| **Make directory** <br> Creates a new folder with the given name.|
|pwd | | **Print working directory** <br> Shows the current path.|
|mv  `<source>` `<target>` | mv text.txt test <br> mv test.txt bla.txt |**Move** a file <br> Can also be used for renaming (second example)|
|cp `<source>` `<target>`| cp text.txt test <br> cp -p text.txt test | **Copy** a file <br> -p preserves mode, ownership, and timestamps<br> Can also rename. |
|rm `<file>` <br> rm -rf `<folder>`|rm text.txt <br> rm -rf test  <br> rm \*.tmp (removes all files with file ending \*.tmp)| **Remove** <br> *Warning: Cannot be undone!* <br> -f force, no confirmation<br> dialog, no warnings <br> -r recursive, for folders |
|clear| | **Clear** the console <br>Gives you a fresh view. Similar to <kbd>Ctrl</kbd>+<kbd>L</kbd>|

## More Basics

|Command|Example|Comment|
|---|---|---|
|head  `<file>` <br> tail `<file>` | head text.txt <br> head -n 20 text.txt | **Display first/last lines of file** <br> Default n=10.|
|less `<file>` | less text.txt | **Display contents of a file** <br> of a file, read-only <br> <kbd>h</kbd> help <br> <kbd>q</kbd> close<br> <kbd>f</kbd>,<kbd>b</kbd> forward, backward one page <br> <kbd>e</kbd>,<kbd>y</kbd> forward, backward single line <br>/`<word>` search <br> <kbd>n</kbd>,<kbd>p</kbd> next, previous `<word>` during search <br> -i activate case insentitive search |
|nano `<file>` | nano text.txt | **File editor** <br> <kbd>Ctrl</kbd>+<kbd>x</kbd> to close <br> <kbd>Alt</kbd>+<kbd>/</kbd> to go to the end of a file |
|chmod <permissions> <folder>|chmod 777 test|**Change permissions** <br> for file <br> 777 gives the folder all possible rights. <br> Further explanation see below. |
|chown `<username>` `<file>` | sudo chown alice folder | **Change file owner** |
|du `<directory>` | du -h <br> du -sh . <br> du -sh *  &#124; sort -h | **Disk usage** <br> -s summary <br> -h human readable |
|df `<directory>` | df -h | **Disk free** <br> Show remaining disk space. <br> -h human readable |
|htop| | **Task manager** <br> View currently running processes. <kbd>Q</kbd> to close.|

## Multiple Commands
|Command|Example|Comment|
|---|---|---|
| `<command1>` ; `<command2>` | | **Concatenate commands** <br> Execute `<command2>` after `<command1>`. |
| `<command1>` && `<command2>` | | **Double ampersand** <br> Execute `<command2>` after `<command1>` but only if `<command1>` finished successfully. |
| `<command>` > `<file>` <br> `<command>` >> `<file>` <br> `<command>` 2> `<file>` | ls -a > result.txt <br> ls -a >> result.txt | **Redirect** <br> the output of a command into a file <br> > creates/overwrites a file <br> >> creates/appends to a file <br> 2> redirects the errors |
| `<command1>` &#124; `<command2>` | history  &#124; less <br> ls  &#124; less | **Pipe** <br> the output of a command to less. <br> Especially useful for history command (displays the latest commands) or folders with many files in them (last example) |

## Search
[fselect](https://github.com/jhspetersson/fselect) - Search for files in a modern, SQL-like fashion.
TODO grep, find

## Screen
|Command|Comment|
|---|---|
|screen | Create a new session. |
|<kbd>Ctrl</kbd>+<kbd>A</kbd>,<kbd>D</kbd> | Detach from current screen session. |
|<kbd>Ctrl</kbd>+<kbd>D</kbd> | End current session. Similart to `exit`. |
|screen -r | Reattach to session. |
|screen -ls | List all sessions. |
|screen -S `<name>` -L | Create a new screen session `<name>` with logging enabled. |
|screen -r `<name>`| Reattach to session with `<name>` if there are multiple ones. |
|screen -rx `<name>`| Attach to session that is already attached. |
|<kbd>Ctrl</kbd>+<kbd>A</kbd>,<kbd>Esc</kbd> | Enter scroll mode. Use <kbd>↑</kbd> and <kbd>↓</kbd> or <kbd>Pg Up</kbd> and <kbd>Pg Dn</kbd> to scroll. Hit <kbd>Esc</kbd> to exit scroll mode. |

## Misc
|Command|Example|Comment|
|---|---|---|
|passwd `<username>` | passwd alice | **Change password** | 
|rsync `<source>` `<target>` | rsync -aP file.txt servername:/home/user/data | **Rsync** <br> copy files from/to a server |
|scp `<source>` `<target>` | `scp username@example.com:/my/folder/*.txt .` | **Secure copy**  <br> files from/to a server <br> -r recursive (include subfolders)<br> The example copies all files from the given directory then end in .txt to the local directory (dot) |
|ssh `<server>` <br> ssh -t `<server>` "`<command>`" | ssh `username@example.com` <br> ssh -t `username@example.com` "ls -a" | **Secure shell** <br> Connect to a server <br> -t Close connection immediately after the command is done <br> Further explanation see below. |
|stat `<filename>` | stat text.txt | Display file **Status**, creation date, <br>last modification date, etc. |
|su `<username>`| su root | **Switch user** |
|touch `<filename>` | touch text.txt <br> touch makefile | **Touch** a file.<br>Creates a new, empty file if the file does <br>not already exist.<br> Especially helpful to create makefiles under Windows.<br>Actually the command is used for changing file timestamps. |
|watch| watch -n60 ls | Repeat a command every n seconds. |
|which| which nano | Display where the command / program is coming from. |

## Cursor Tricks
|Command|Example|Comment|
|<kbd>Ctrl</kbd>+<kbd>A</kbd>|&nbsp;|Jump to beginning.|
|<kbd>Ctrl</kbd>+<kbd>E</kbd>|&nbsp;|Jump to end.|
|<kbd>Ctrl</kbd>+<kbd>W</kbd>|&nbsp;|Delete one word left of the cursor.|
|<kbd>Ctrl</kbd>+<kbd>U</kbd>|&nbsp;|Delete entire line.|
|<kbd>Ctrl</kbd>+<kbd>Y</kbd>|&nbsp;|Paste back what you just deleted.|

## Creating an SSH key

```bash
# Creating
ssh-keygen -t rsa -b 4096 -N "" -C "" -f keyname
mv keyname* ~/.ssh

# Setting access rights
chmod 700 ~/.ssh && chmod 600 ~/.ssh/*

# ~/.ssh/config
Host github
HostName github.com
User git
IdentityFile ~/.ssh/keyname

# This logs into the server, and copies the public key to it.
ssh-copy-id -i ~/.ssh/keyname user@remote_machine
```

```bash
# Checking the ssh procesd
ssh -T git@github.com
eval $(ssh-agent -s)
ssh-add ~/.ssh/keyname
ssh -T git@github.com
```

## Permissions

Type `chmod xxx <filename>` to change permissions where `xxx` is the numerical code from the table below.

```
Explaination of the Codes: . ... ... ...
                           (type) (user persmissions) (group permissions) (world permissions)
```
The first item can be `d` (a directory), `-` (a regular file) or `l` (a symbolic link).  
The following three triplets specify permissons for the `user`, `group` and `world` in that order.  
In each tripplet, permissions can be `r` (read), `w` (write), `x` (execute) or `-` (not assigned).  
Setting permissions can be done via numbers: `r=4`, `w=2`, `x=1` and `-=0`.  

|Setting|Code|Use Case|
|---|---|---|
|`----------`|000|Locking even yourself out. Use `chmod` again, if this happens. |
|`-r--------`|400|An auto-generated password file (e.g. `~/.google_authenticator`). |
|`-rw-------`|600|`~/.history`, all the ssh keys in your `~/.ssh` folder.|
|`-rwx------`|700|Your `~/.ssh` folder.|
|`-r--r--r--`|444|A textfile, that others should see as well, but nobody should modify it.|
|`-r-xr-xr-x`|555|A folder, that others should be able to `cd` into as well, but nobody should modify it.|
|`-rwxr-xr-x`|755|Files and folders you want other people to *see*. |
|`-rwxrwxrwx`|777|Files and folders you want other people to *see and modify*. The most open permission.|

Permissions on directory have the following meaning:  
The read bit allows to list the files within the directory.  
The write bit allows to create, rename, or delete files within the directory, and modify the directory's attributes.  
The execute bit allows to enter the directory, and access files and directories inside.  

To view permissions as numerical code: `stat -c %a <filename>`.

<details><summary>What does `s` mean? (click to expand)</summary>
"s", like "x", means something different for directories and regular files. 

For files, "x" means "executable" of course. For directories, it means "searchable." Without "x" permission on a directory, you can't set it to be your current directory, or get any of the file information like size, permissions, or inode number, so that you effectively can't access any of the files. If a directory has no "r" permission, you can't get a listing, but if you know a file is there, you can still access the file.

Now "s", for files, means "setuid exec." If a file has s permission, then it's executable, and furthermore, the user id and/or group id of the process is set to the user or group id of the owner of the file, depending on whether it's the user or group "s" that's set. This is a way to give limited root powers to a user -- a program that runs as root when an ordinary user executes it. For example, the "passwd" program, which can change otherwise write-protected files on behalf of a user, works this way: it's owned by the "bin" group (generally) and has g+s so that it can write to /etc/passwd and/or /etc/opasswd which are also owned by group "bin."

For directories, "s" means "sticky". If a directory has "s", then the owner and/or group of any files put into the directory are set to the owner/group of the directory. This is often used on CVS repositories, so that the files in the repository end up all owned by the same person and/or group, even though they're put in by different people. I use g+s on all the CVS repositories I set up.
</details>


## Snippets and Useful .bashrc Additions

```bash
# Finding out which linux you are using
uname -m && cat /etc/*release

# Bulk renaming of files
rename 's/ch0/ch/gi' *.tiff
```

```bash
# Make output of df and du human readable
alias df='df -h'
alias du='du -h'

# Count files in directory
alias fcount='ls -1 | wc -l'

# Disable "Save workspace" promt when closing R
alias R='R --no-save'
```

## Resources
 * [Presentation](https://ketancmaheshwari.github.io/pdfs/LPT_LISA.pdf)
 * [Linux Directories Explained in 100 Seconds](https://www.youtube.com/watch?v=42iQKuQodW4)
