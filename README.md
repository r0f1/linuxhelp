# Linux commands

## Help

|Command|Example|Comment|
|--------|---|---|
|man `<command>`|man cd<br />man ls|**Manual** <br> Get help (close with <kbd>q</kbd>).|
|`<command>` --help|cd --help|Also **help**.|
|<kbd>Tab</kbd> (1x or 2x) |&nbsp; |Auto completion.|
|<kbd>↑</kbd>|&nbsp;|See previous command.|
|<kbd>Ctrl</kbd>+<kbd>c</kbd>|&nbsp;|Kill the current process or command (e.g. if something hangs).|
|<kbd>Ctrl</kbd>+<kbd>d</kbd>|&nbsp;|Logout. Closes the console if you're not in an ssh session.|
|<kbd>Ctrl</kbd>+<kbd>r</kbd>|&nbsp;|Search through your history. Start typing and it will auto-complete. Hit <kbd>Ctrl</kbd>+<kbd>r</kbd> again and it will cycle though the other auto-completion options. Hit <kbd>Enter</kbd> and the command will execute. Hit <kbd>←</kbd>,<kbd>→</kbd> to edit commands.


## Basic

|Command|Example|Comment|
|---|---|---|
|cd `<foldername>`|cd test <br> cd .. <br> cd - <br> cd ~ <br> cd /path/to/my/folder | **Change directory** <br>. (dot) is the current directory <br> .. (dotdot) is the upper/partent directory <br> / (slash) is the root directory <br> ~ (tilde) is your home directory <br> - (minus) switches to the previous directory|
|ls <br> ls `<options>` <br> ls `<foldername>` <br> ls `<pattern>` | ls <br> ls -la <br> ls -l -a (same as above) <br> ls -halt (more arguments) <br> ls -d */ (list all directories) <br> ls test (contents of subfolder) <br> ls *.sas (show only .sas files) | **List** contents of a folder <br> -h human readable <br> -a all <br> -l more information <br> -t order by time |
|mv  `<source>` `<target>` | mv text.txt test <br> mv test.txt bla.txt |**Move** a file <br> Can also be used for renaming (second example)|
|cp `<source>` `<target>`| cp text.txt test <br> cp -p text.txt test | **Copy** a file <br> -p preserves mode, ownership, and timestamps<br> Can also rename. |
|rm `<filename>` <br> rm -rf `<foldername>`|rm text.txt <br> rm -rf test  <br> rm \*.tmp (removes all files with file ending \*.tmp)| **Remove** <br> *warning: cannot be undone!* <br> -f force, no confirmation<br> dialog, no warnings <br> -r recursive, for folders |
|sudo `<command>`| sudo ls | **super user do** <br> Run a command with elevated privleges. Will ask you for a password. Only possible, if you were granted administrative rights on the system.
|less `<filename>` | less text.txt | **display contents** <br> of a file, read-only <br> <kbd>h</kbd> help <br> <kbd>q</kbd> close<br> <kbd>f</kbd>,<kbd>b</kbd> forward, backward one page <br> <kbd>e</kbd>,<kbd>y</kbd> forward, backward single line <br>/`<word>` search <br> <kbd>n</kbd>,<kbd>p</kbd> next, previous `<word>` during search <br> -i activate case insentitive search |
| `<command>` &#124; less| history  &#124; less <br> ls  &#124; less | **pipe** <br> the output of a command to less. <br> Especially useful for history command (displays the latest commands) or folders with many files in them (last example) |
|nano `<filename>` | nano text.txt | **file editor** <br> <kbd>Ctrl</kbd>+<kbd>x</kbd> to close <br> <kbd>Alt</kbd>+<kbd>/</kbd> to go to the end of a file |
|pwd | | **Print working directory** <br> shows the current path|
|clear| | **Clear** the console <br>gives you a fresh view|
|mkdir `<foldername>` |mkdir test | **Make directory** <br> creates a new folder with the given name|
|chmod <permissions> <foldername>|chmod 777 test|**Change permissions** <br> for file <br> 777 gives the folder all possible rights |
|chown `<username>` `<file>` | sudo chown alice folder | **change file owner** |
|htop| | View currently running processes. |

## Advanced

|Command|Example|Comment|
|---|---|---|
|du `<directory>` | du -h <br> du -sh . <br> du -sh *  &#124; sort -h | **disk usage** <br> -s summary <br> -h human readable |
|df `<directory>` | df -h | **disk free** <br> Show remaining disk space <br> -h human readable |
|ssh `<server>` <br> ssh -t `<server>` "`<command>`" | ssh `username@example.com` <br> ssh -t `username@example.com` "ls -a" | **secure shell** <br> Connect to a server <br> -t Close connection immediately after the command is done |
|exit | | Quit server connection |
|scp `<source>` `<target>` | `scp username@example.com:/my/folder/*.txt .` | **secure copy**  <br> files from/to a server <br> -r recursive (include subfolders)<br> The example copies all files from the given directory then end in .txt to the local directory (dot) |
|rsync `<source>` `<target>` | rsync -aP file.txt servername:/home/user/data | **rsync** <br> copy files from/to a server |
| `<command>` > `<filename>` <br> `<command>` >> `<filename>` | ls -a > result.txt <br> ls -a >> result.txt | **redirect** <br> the output of a command into a file <br> > creates/overwrites a file <br> >> creates/appends to a file |

## Lesser used

|Command|Example|Comment|
|---|---|---|
|touch `<filename>` | touch text.txt <br> touch makefile | **touch** a file.<br>Creates a new, empty file if the file does <br>not already exist.<br> Especially helpful to create makefiles under Windows.<br>Actually the command is used for changing file timestamps. |
|stat `<filename>` | stat text.txt | Display file **status**, creation date, <br>last modification date, etc. |
|su `<username>`| su root | **switch user** |
|passwd `<username>` | passwd alice | **change password** | 
|usermod `<options>` `LOGIN` | usermod -g grpname alice | **modify a user account** |
|getent group `<groupname>` | | **view members of group** |
|id `<username>`<br>groups `<username>` | | **view groups of user** |
|ls -1 &#124; wc -l | | Count number of files in current directory. |
|watch| watch -n60 ls | Repeat a command every n seconds. |
|which | which nano | Display where the command / program is coming from. |

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

## Screen

|Command|Comment|
|---|---|
|screen | Create a new session. |
|screen -S `<name>` -L | Create a new screen session `<name>` with logging enabled. |
|<kbd>Ctrl</kbd>+<kbd>A</kbd>,<kbd>D</kbd> | Detach from current session. |
|screen -ls | List all sessions. |
|screen -r | Reattach to session. |
|screen -r `<name>`| Reattach to session with `<name>` if there are multiple ones. |
|screen -rx `<name>`| Attach to session that is already attached. |
|<kbd>Ctrl</kbd>+<kbd>A</kbd>,<kbd>Esc</kbd> | Enter scroll mode. Use <kbd>↑</kbd> and <kbd>↓</kbd> or <kbd>Pg Up</kbd> and <kbd>Pg Dn</kbd> to scroll. Hit <kbd>Esc</kbd> to exit scroll mode. |

## Misc

```bash
# Finding out which linux you are using
uname -m && cat /etc/*release

# Bulk renaming of files
rename 's/ch0/ch/gi' *.tiff

# Rebinding keyboard shotcut Ctrl+C to Ctrl+J
stty intr ^J
```

### Creating an SSH key

```bash
# Creating
ssh-keygen -t rsa -b 4096 -N "" -C "" -f keyname

# Setting access rights
chmod 700 ~/.ssh && chmod 600 ~/.ssh/*

# ~/.ssh/config
Host github
HostName github.com
User git
IdentityFile ~/.ssh/id_keyname
```

```bash
# Checking the ssh procesd
ssh -T git@github.com
eval $(ssh-agent -s)
ssh-add ~/.ssh/keyname
ssh -T git@github.com
```

### Useful .bashrc additions

```bash
# Detailed ls output
alias ls='ls --color=auto --group-directories-first --time-style=iso --quoting-style=literal'
alias ll='ls -Fails'

# Make output of df and du human readable
alias df='df -h'
alias du='du -h'

# Count files in directory
alias fcount='ls -1 | wc -l'

# Disable "Save workspace" promt when closing R
alias R='R --no-save'

# Make FFPlay a bit more sane
alias ffplay='ffplay -hide_banner -fast -autoexit -infbuf'
```
