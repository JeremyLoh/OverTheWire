# Bandit Level 21 -> Level 22

A program is running automatically at regular intervals from `cron`, the time-based job scheduler. Look in `/etc/cron.d/` for the configuration and see what command is being executed.

# Command executed by cron

```console
bandit21@bandit:~$ cd /etc/cron.d
bandit21@bandit:/etc/cron.d$ ls
cronjob_bandit15_root  cronjob_bandit22  cronjob_bandit24
cronjob_bandit17_root  cronjob_bandit23  cronjob_bandit25_root
bandit21@bandit:/etc/cron.d$ cat cronjob_bandit22
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
```

Input

`@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null`

1. [@reboot](https://www.cyberciti.biz/faq/linux-execute-cron-job-after-system-reboot/) is used to run a job at startup (boot time), after the Linux reboot command.

1. [&>](http://www.tldp.org/LDP/abs/html/io-redirection.html): used to redirect both `stdout` and `stderr`

1. [/dev/null](https://www.journaldev.com/35489/dev-null-in-linux) is a null device file. It will discard anything written to it and will return `EOF` on reading. It is not an executable file, we cannot use piping using | operator to redirect to /dev/null. The only way is to use file redirections (>, >>, or <, <<).

Output

1. `* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null`

# /usr/bin/cronjob_bandit22.sh (Bash script)

```console
bandit21@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit22.sh
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```

1. `#!/bin/bash` means we have a bash script file
1. `chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv`

   User can read and write

   Group can read

   Other can read

1. `cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv`

   The password of `bandit22` is being redirected to a file `/tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv`

To obtain the password, we can `cat` the file!

```console
bandit21@bandit:/etc/cron.d$ cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI
```

# PASSWORD

Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI
