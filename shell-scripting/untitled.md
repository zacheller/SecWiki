# .bashrc

```text
# copy file contents to clipboard
clip(){
xclip -sel c < $1
}

# make directory and enter it
mcd()
{
    test -d "$1" || mkdir "$1" && cd "$1"
}

# go up x directories
# (c) 2007 stefan w. GPLv3          
function up {
ups=""
for i in $(seq 1 $1)
do
        ups=$ups"../"
done
cd $ups
}

#Search Forward through bash command history (Ctrl-S)
stty -ixon

# Auto no-check-certificate for wget
wgetnc()
{
    wget --no-check-certificate $1	
}

### WSL
notepad(){
        /mnt/c/Windows/notepad.exe $1
}
paint(){
        /mnt/c/Windows/System32/mspaint.exe $1
}
sublime(){
        /mnt/c/Program\ Files/Sublime\ Text\ 3/sublime_text.exe $1
}
alias subl='sublime'
alias note='notepad'

alias cdd="cd $DRAFTS"
alias cdp="cd $POSTS"

```

