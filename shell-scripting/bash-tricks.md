# Bash Tricks

## Three-Fingered Claw technique

These functions are \*NIX OS and shell flavor-robust. Put them at the beginning of your script \(bash or otherwise\), try\(\) your statement and code on.

Explanation \(based on flying sheep comment\).

* yell: print the script name and all arguments to stderr: 
  * $0 is the path to the script ;
  * $\* are all arguments.
  * &gt;&2 means &gt; redirect stdout to & pipe 2. pipe 1 would be stdout itself.
* die does the same as yell, but exits with a non-0 exit status, which means “fail”.
* try uses the \|\| \(boolean OR\), which only evaluates the right side if the left one failed.
  * $@ is all arguments again, but different.

```text
yell() { echo "$0: $*" >&2; }
die() { yell "$*"; exit 111; }
try() { "$@" || die "cannot $*"; }
```

## Pipe Output to Arguments

Here is a short-liner which will prepend piped arguments to your script arguments list:

```text
#!/bin/bash
args=$@
[[ -p /dev/stdin ]] && { mapfile -t; set -- "${MAPFILE[@]}"; set -- $@ $args; }

echo $@
```

Example use:

```text
$ ./script.sh arg1 arg2 arg3
> arg1 arg2 arg3

$ echo "piped1 piped2 piped3" | ./script.sh
> piped1 piped2 piped3

$ echo "piped1 piped2 piped3" | ./script.sh arg1 arg2 arg3
> piped1 piped2 piped3 arg1 arg2 arg3


# https://superuser.com/questions/461946/can-i-use-pipe-output-as-a-shell-script-argument
```

## Renaming files with mv

```text
root@kali:~/.ssh# mkdir x
root@kali:~/.ssh# mv x{,_COMPLETE}
root@kali:~/.ssh# ls
x_COMPLETE
```

## Linking

### Hard Link

```text
$ ln source_file link
```

### Soft/Symbolic Link

Soft linking is useful for adding programs to in PATH directories e.g. ~/bin/. Soft links are created with the `ln` command. For example, the following would create a soft link named `link1` to a file named `file1`, both in the current directory

```text
$ ln -s file1 link1
$ ls -l file1 link1 # verify new soft link
-rw-r--r-- 1 veryv wheel 0 Mar 7 22:01 file1
lrwxr-xr-x 1 veryv wheel 5 Mar 7 22:01 link1 -> file1
```



