# Bandit Level 25 -> Level 26

Logging in to `bandit26` from `bandit25` should be fairly easy… The shell for user `bandit26` is not `/bin/bash`, but something else. Find out what it is, how it works and how to break out of it.

# Trying to login to `bandit26` using ssh and identity file

```console
bandit25@bandit:~$ ssh bandit26@localhost -i bandit26.sshkey
Could not create directory '/home/bandit25/.ssh'.
The authenticity of host 'localhost (127.0.0.1)' can't be established.
ECDSA key fingerprint is SHA256:98UL0ZWr85496EtCRkKlo20X3OPnyPSB5tB5RPbhczc.
Are you sure you want to continue connecting (yes/no)? yes
...
  Enjoy your stay!

  _                     _ _ _   ___   __
 | |                   | (_) | |__ \ / /
 | |__   __ _ _ __   __| |_| |_   ) / /_
 | '_ \ / _` | '_ \ / _` | | __| / / '_ \
 | |_) | (_| | | | | (_| | | |_ / /| (_) |
 |_.__/ \__,_|_| |_|\__,_|_|\__|____\___/
Connection to localhost closed.
```

# [Understanding the /etc/passwd file format](https://www.cyberciti.biz/faq/understanding-etcpasswd-file-format/)

Traditionally, the `/etc/passwd` file is used to keep track of every registered user that has access to a system.

These information are required by users during login. The `/etc/passwd` file should have general read permissions as many command utilities use it to map user IDs to usernames. However, write access to the file must only be for the superuser/root account!

It is a colon-separated file that contains the following:

1. Username

   It is used when the user logs in. It should be between 1 and 32 characters in length.

1. Encrypted password

   An `x` character indicates that the encrypted password is stored in `/etc/shadow` file. You need to use the `passwd` command to compute the hash of a password typed at the `CLI` or to store/update the hash of the password in the `/etc/shadow` file.

1. User ID number (UID)

   Each user must be assigned a user ID (UID). UID 0 (zero) is reserved for root and UIDs 1-99 are reserved for other predefined accounts. UIDs 100-999 are reserved by the system for administrative and system accounts/groups.

1. User's group ID number (GID)

   The primary group ID (stored in `/etc/group` file)

1. User ID info

   The comment field that allows for extra information about the user to be added (e.g. user's full name, phone number). This field can be utilized by the `finger` command

1. User home directory

   The absolute path to the directory the user will be in when they login. If the directory does not exist, then the home directory becomes `/`

1. Shell

   The absolute path of a command or shell (typically `/bin/bash`). It does not have to be a shell

```console
bandit25@bandit:~$ grep bandit26 /etc/passwd
bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext
```

The shell absolute path for `bandit26` is `/usr/bin/showtext`

```console
bandit25@bandit:~$ cat /usr/bin/showtext
#!/bin/sh

export TERM=linux

more ~/text.txt
exit 0
```

1. `export TERM=linux`

   Sets the terminal emulator to `linux`

1. `more ~/text.txt`

   Shows `text.txt` in current directory

# [`more` command](https://linux.die.net/man/1/more)

Allows for the filtering of view of a file line by line. Accessing the `man` pages utilizes `more`.

`more` is used to view the text files in the command prompt, displaying one screen at a time in case the file is large (For example log files). The more command also allows the user do scroll up and down through the page.

# Steps to execute

The terminal window needs to shrink vertically, to allow for the `more` command to be executed (as the content in `text.txt` will be too long to print to the screen).

Pressing `v` in `more` will start up an editor at current line. The editor is taken from the environment variable VISUAL if defined, or EDITOR if VISUAL is not defined, or defaults to "vi" if neither VISUAL nor EDITOR is defined.

Executing command inside `VIM`

1. `:!COMMAND` : execute COMMAND with a shell

Access the configured shell

1. `:shell`: Start a shell

Editing another file inside `VIM`

1. `:e FILE`

[How to run Unix commands from within Vim?](https://superuser.com/a/285506)

```console
bandit25@bandit:~$ ls
bandit26.sshkey
bandit25@bandit:~$ ssh bandit26@localhost -i bandit26.sshkey

v
:e /etc/bandit_pass/bandit26
5czgV9L3Xx8JPOyRbXh6lQbmIOWvPT6Z
```

# Getting out of the default shell for `bandit26`

`:set shell=/bin/bash`

`:shell`

# PASSWORD

5czgV9L3Xx8JPOyRbXh6lQbmIOWvPT6Z
