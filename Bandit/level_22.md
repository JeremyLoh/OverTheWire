# Bandit Level 22 -> Level 23

A program is running automatically at regular intervals from `cron`, the time-based job scheduler. Look in `/etc/cron.d/` for the configuration and see what command is being executed.

NOTE: Looking at shell scripts written by other people is a very useful skill. The script for this level is intentionally made easy to read. If you are having problems understanding what it does, try executing it to see the debug information it prints.

# Command

```console
bandit22@bandit:~$ cd /etc/cron.d
bandit22@bandit:/etc/cron.d$ ls
cronjob_bandit15_root  cronjob_bandit22  cronjob_bandit24
cronjob_bandit17_root  cronjob_bandit23  cronjob_bandit25_root
bandit22@bandit:/etc/cron.d$ cat cronjob_bandit23
@reboot bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
* * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
```

cronjob_bandit23 executes the following command:

`@reboot bandit23 /usr/bin/cronjob_bandit23.sh &> /dev/null`

# /usr/bin/cronjob_bandit23.sh (shell script)

```console
bandit22@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit23.sh
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget
```

1.  `myname=$(whoami)`

    Use [command substitution](https://www.cyberciti.biz/faq/unix-linux-bsd-appleosx-bash-assign-variable-command-output/) feature of bash. It allows you to run a shell command and store its output to a bash variable.

    Do not put any spaces after the equals sign and command must be on right side of `=`

    `myname` is `bandit23` as `whoami` prints the effective userid (NEED TO SET TO NEXT LEVEL USER)

1.  mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

    1. `md5sum` - compute and check MD5 message digest. Print or check MD5 (128-bit) checksums.
       With no FILE, or when FILE is -, read standard input.

    e.g.

    `bandit22@bandit:/etc/cron.d$ echo test | md5sum`

    `d8e8fca2dc0f896fd7cb4cb0031ba249 -`


    1. [cut](https://www.computerhope.com/unix/ucut.htm) - remove sections from `each line` of files. Print selected parts of lines from each FILE to standard output. With no FILE, or when FILE is -, read standard input.

         1. `-d` flag: to specify field delimiter, instead of TAB
         1. `-f` flag: indicate fields to select

    `cut -d ' ' -f 1`
        1. Use space as delimiter for `md5sum` output
        1. Obtain first value obtained from result of cut (based on delimiter)

    `mytarget` will be md5sum of `I am user bandit23`

`cat /etc/bandit_pass/$myname > /tmp/$mytarget`

1. Password will be saved in `/tmp/$mytarget`

Command to execute

```console
bandit22@bandit:/tmp$ myname=bandit23
bandit22@bandit:/tmp$ echo I am user $myname | md5sum | cut -d ' ' -f 1
8ca319486bfbbc3663ea0fbe81326349
bandit22@bandit:/tmp$ cat /tmp/8ca319486bfbbc3663ea0fbe81326349
jc1udXuA1tiHqjIsL8yaapX5XIAI6i0n
```

# PASSWORD

`jc1udXuA1tiHqjIsL8yaapX5XIAI6i0n`
