# sed

#### Leverage line numbers to grab certain lines

```text
$ searchsploit ProFtpd 1.3.5 | nl | sed -n '4,6p'
     4  ProFTPd 1.3.5 - 'mod_copy' Command Execution (Metasploit)                               | linux/remote/37262.rb
     5  ProFTPd 1.3.5 - 'mod_copy' Remote Command Execution                                     | linux/remote/36803.py
     6  ProFTPd 1.3.5 - File Copy                                                               
```



