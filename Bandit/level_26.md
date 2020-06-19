# Bandit Level 26 -> Level 27

Good job getting a shell! Now hurry and grab the password for bandit27!

# Exiting default shell set to `/usr/bin/showtext`

1. Reduce terminal height so that `more` is executed to show text
1. Enter `vi` by pressing `v` to start up an editor at current line (default editor is `vi`)
1. Set shell variable to bash temporarily using `:set shell=/bin/bash`
1. Access shell using `:shell` in `vi`

The current shell can be checked inside `vi` by running `:set shell?`

To change the shell for `vi` permanently, update the `.vimrc` file

    `set shell=bash`

# Command to execute, after entering default shell (`/bin/bash`)

```console
bandit26@bandit:~$ ls
bandit27-do  text.txt
bandit26@bandit:~$ cat text.txt
  _                     _ _ _   ___   __
 | |                   | (_) | |__ \ / /
 | |__   __ _ _ __   __| |_| |_   ) / /_
 | '_ \ / _` | '_ \ / _` | | __| / / '_ \
 | |_) | (_| | | | | (_| | | |_ / /| (_) |
 |_.__/ \__,_|_| |_|\__,_|_|\__|____\___/
bandit26@bandit:~$ file bandit27-do
bandit27-do: setuid ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=8e941f24b8c5cd0af67b22b724c57e1ab92a92a1, not stripped
bandit26@bandit:~$ ./bandit27-do
Run a command as another user.
  Example: ./bandit27-do id
bandit26@bandit:~$ ./bandit27-do cat /etc/bandit_pass/bandit27
3ba3118a22e93127a4ed485be72ef5ea
```

Everything in Linux is considered as a file.

In Linux, file extension does not matter and it may not give a exact picture of file type.

1. `setuid ELF 32-bit LSB executable` is a 32 bit 'application' (that could also run on 64-bit) that elevates permissions. When the file is run, it would be executed with the identity of the owner of the file, rather than the identity of the person who runs the program.

   LSB means “least significant byte” which means the file in intended to run on a little endian computer architecture like x86

# PASSWORD

3ba3118a22e93127a4ed485be72ef5ea
