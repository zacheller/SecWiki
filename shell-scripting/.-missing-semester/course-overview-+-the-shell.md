# Course overview + the shell

## Lecture Notes

In this lecture, we will focus on the Bourne Again SHell, or “bash” for short. This is one of the most widely used shells, and its syntax is similar to what you will see in many other shells.

If the shell is asked to execute a command that doesn’t match one of its programming keywords, it consults an _environment variable_ called `$PATH` that lists which directories the shell should search for programs when it is given a command:

```text
missing:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
missing:~$ which echo
/bin/echo
missing:~$ /bin/echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```

When we run the `echo` command, the shell sees that it should execute the program `echo`, and then searches through the `:`-separated list of directories in `$PATH` for a file by that name. When it finds it, it runs it \(assuming the file is _executable_; more on that later\). We can find out which file is executed for a given program name using the `which` program. We can also bypass `$PATH` entirely by giving the _path_ to the file we want to execute.

 One thing you need to be root in order to do is writing to the `sysfs` file system mounted under `/sys`. `sysfs` exposes a number of kernel parameters as files, so that you can easily reconfigure the kernel on the fly without specialized tools.

For example, the brightness of your laptop’s screen is exposed through a file called `brightness` under

```text
/sys/class/backlight
```

By writing a value into that file, we can change the screen brightness. Your first instinct might be to do something like:

```text
$ sudo find -L /sys/class/backlight -maxdepth 2 -name '*brightness*'
/sys/class/backlight/thinkpad_screen/brightness
$ cd /sys/class/backlight/thinkpad_screen
$ sudo echo 3 > brightness
An error occurred while redirecting file 'brightness'
open: Permission denied
```

 This error may come as a surprise. After all, we ran the command with `sudo`! This is an important thing to know about the shell. Operations like `|`, `>`, and `<` are done _by the shell_, not by the individual program. `echo` and friends do not “know” about `|`.

Using this knowledge, we can work around this:

```text
$ echo 3 | sudo tee brightness
```

Since the `tee` program is the one to open the `/sys` file for writing, and _it_ is running as `root`, the permissions all work out. You can control all sorts of fun and useful things through `/sys`, such as the state of various system LEDs \(your path might be different\):

```text
$ echo 1 | sudo tee /sys/class/leds/input6::scrolllock/brightness
```

## Exercises

* For this course, you need to be using a Unix shell like Bash or ZSH. If you are on Linux or macOS, you don’t have to do anything special. If you are on Windows, you need to make sure you are not running cmd.exe or PowerShell; you can use [Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/) or a Linux virtual machine to use Unix-style command-line tools. To make sure you’re running an appropriate shell, you can try the command `echo $SHELL`. If it says something like `/bin/bash` or `/usr/bin/zsh`, that means you’re running the right program.
  * `echo $SHELL`:`/bin/bash`
* Create a new directory called `missing` under `/tmp`.
  * `mkdir /tmp/missing`
* Look up the `touch` program. The `man` program is your friend.
  * `man touch`
* Use `touch` to create a new file called `semester` in `missing`.
  * `touch /tmp/missing/semester`
* Write the following into that file, one line at a time:

  ```text
  #!/bin/sh
  curl --head --silent https://missing.csail.mit.edu
  ```

  The first line might be tricky to get working. It’s helpful to know that `#` starts a comment in Bash, and `!` has a special meaning even within double-quoted \(`"`\) strings. Bash treats single-quoted strings \(`'`\) differently: they will do the trick in this case. See the Bash [quoting](https://www.gnu.org/software/bash/manual/html_node/Quoting.html) manual page for more information.

  * `echo '#!/bin/sh' >> semester`
  * `echo 'curl --head --silent` [`https://missing.csail.mit.edu`](https://missing.csail.mit.edu)`' >> semester`

* Try to execute the file, i.e. type the path to the script \(`./semester`\) into your shell and press enter. Understand why it doesn’t work by consulting the output of `ls` \(hint: look at the permission bits of the file\).
  * no execution bit
* Run the command by explicitly starting the `sh` interpreter, and giving it the file `semester` as the first argument, i.e. `sh semester`. Why does this work, while `./semester` didn’t?
  * `./semester`asks the kernel to run `semester` as a program, and the kernal \(program loader\) will check permissions first, **and then** use `/bin/bash` \(or `sh` or `zsh` etc\) to actually execute the script.
  * `sh semester`asks the kernel \(program loader\) to run `/bin/sh`, not the program so the execute permissions of the file do not matter.
* Look up the `chmod` program \(e.g. use `man chmod`\).
* Use `chmod` to make it possible to run the command `./semester` rather than having to type `sh semester`. How does your shell know that the file is supposed to be interpreted using `sh`? See this page on the [shebang](https://en.wikipedia.org/wiki/Shebang_%28Unix%29) line for more information.
  * `chmod +x semester`
  * The shebang is parsed as an interpreter directive by the program loader mechanism.  The loader executes the specified [interpreter](https://en.wikipedia.org/wiki/Interpreter_%28computing%29) program, passing to it as an argument the path that was initially used when attempting to run the script, so that the program may use the file as input data.
* Use `|` and `>` to write the “last modified” date output by `semester` into a file called `last-modified.txt` in your home directory.
  * \`stat -c '%y' semester 2020-09-07 21:10:47.638196300 -0700 &gt; ~/last-modified.txt\`
* Write a command that reads out your laptop battery’s power level or your desktop machine’s CPU temperature from `/sys`. Note: if you’re a macOS user, your OS doesn’t have sysfs, so you can skip this exercise.
  * `cat /sys/class/power_supply/BAT0/*`

