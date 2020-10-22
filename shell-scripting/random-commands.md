# Random Commands



```text
grep -oE "flagF{.*}"

       -o, --only-matching
              Print  only  the matched (non-empty) parts of a matching line, with each such part on a separate output line.

       -E, --extended-regexp
              Interpret PATTERNS as extended regular expressions (EREs, see below).
```

```text
# bc: basic calculator

$ echo "scale=2 ; $TOTAL_DST / $TOTAL_FILES" | bc

$ bc <<<"scale=2; $var1 / $var2"

$ echo "12+5" | bc
17
```

```text
# jq for json manipulation

$ TOTAL_FILES=$(cat incidents.json | jq '.[][] .file_hash' | tr -d '"' | sort | uniq -c | wc -l)
$ TOTAL_DST=$(cat incidents.json | jq '.[][] .ticket_id' | tr -d '"' | sort | uniq -c | wc -l)
```

```text
 lsattr - list existing file attributes
$ lsattr /bin/nsh
----i---------e---- /bin/nsh

chattr - change attribute
$ sudo chattr -i /bin/nsh

$ lsattr /bin/nsh
--------------e---- /bin/nsh
```

```text
# shows all running processes and the command lines used to startup the processes 
ps -eafw
```

```text
# ooked up google bots @https://support.google.com/webmasters/answer/1061943?hl=en
# chose user agent "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)" to pretend to be google

$ curl -s --user-agent "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)" http://2018shell.picoctf.com:46162/flag | grep -oE "picoCTF{.*}"
picoCTF{s3cr3t_ag3nt_m4n_ac87e6a7}
```

```text
$ readelf -h be-quick-or-be-dead-1 
ELF Header:
  Magic:   7f 45 4c 46 02 01 01 00 00 00 00 00 00 00 00 00 
  Class:                             ELF64
  Data:                              2's complement, little endian
  Version:                           1 (current)
  OS/ABI:                            UNIX - System V
  ABI Version:                       0
  Type:                              EXEC (Executable file)
  Machine:                           Advanced Micro Devices X86-64
  Version:                           0x1
  Entry point address:               0x4005a0
  Start of program headers:          64 (bytes into file)
  Start of section headers:          7312 (bytes into file)
  Flags:                             0x0
  Size of this header:               64 (bytes)
  Size of program headers:           56 (bytes)
  Number of program headers:         9
  Size of section headers:           64 (bytes)
  Number of section headers:         31
  Section header string table index: 28

```

```text
EOG(1)                               General Commands Manual                              EOG(1)

NAME
       eog - a GNOME image viewer

SYNOPSIS
       eog [options] files...
```

```text
paste - merge lines of files

$ cat scores | sort | uniq -c | sort -nk1,1 | awk '{print $2}' | paste -sd,
4730,4755,4780,4785,4855,4864,4879,4884,4905,4930,4994,5003,5030,5054,5094,5124
```



