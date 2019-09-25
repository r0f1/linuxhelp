## Creating an SSH key

```
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

## .bashrc

```
# Detailed ls output
alias ll='ls -halt'

# Count files in directory
alias fcount='ls -1 | wc -l'

# Disable "Save workspace" promt when closing R
alias R='R --no-save'
```
