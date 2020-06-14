# OverTheWire

My notes for games available on https://overthewire.org/wargames/

The wargames offered by the OverTheWire community can help you to learn and practice security concepts in the form of fun-filled games.

## Bandit Wargame

### Level 0

Using SSH

### Level 0 -> Level 1

SSH to different user on same server with `ssh bandit1@localhost`

### Level 1

Reading contents of file with a dash name `-`

### Level 2

Reading contents of file with spaces in the filename

### Level 3

Viewing hidden files with `ls -a`

### Level 4

Looping over a list of files, check for human readable file using `file` command

### Level 5

Finding a file based on given requirements:

1. human-readable
1. 1033 bytes in size
1. not executable

### Level 6

Finding a password file stored _somewhere on the server_ and has the following properties:

1. Owned by user `bandit7`
1. Owned by group `bandit6`
1. 33 bytes in size

### Level 7

Finding a password stored in the file `data.txt` next to the word `millionth`

### Level 8

Finding a line of text (password) in `data.txt` that only occurs once

### Level 9

Finding a password in `data.txt` that is one of the few human-readable strings, preceded by several `=` characters

### Level 10

Finding a password in `data.txt`that contains base64 encoded data

### Level 11

Finding a password in `data.txt`, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions (ROT13 algorithm)

### Level 12

Finding a password stored in the file `data.txt`, which is a hexdump of a file that has been repeatedly compressed. (Used commands: `mkdir`, `cp`, `mv`, `file`, `xxd` `bzip2`, `gzip`, `tar`)

### Level 13

The password for the next level is stored in `/etc/bandit_pass/bandit14` and can only be read by user `bandit14`. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level.

### Level 14

The password for the next level can be retrieved by submitting the password of the current level to port 30000 on `localhost`.

### Level 15

The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption.

Helpful note: Getting “HEARTBEATING” and “Read R BLOCK”? Use -ign_eof and read the “CONNECTED COMMANDS” section in the manpage. Next to ‘R’ and ‘Q’, the ‘B’ command also works in this version of that command…

### Level 16

The credentials for the next level can be retrieved by submitting the password of the current level to a port on `localhost` in the range 31000 to 32000.

First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

### Level 17

There are 2 files in the homedirectory: `passwords.old` and `passwords.new`. The password for the next level is in `passwords.new` and is the only line that has been changed between `passwords.old` and `passwords.new`

`NOTE`: if you have solved this level and see ‘Byebye!’ when trying to log into `bandit18`, this is related to the next level, `bandit19`

### Level 18

The password for the next level is stored in a file `readme` in the home directory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.

# Markdown

1. [Code highlight in Markdown](https://stackoverflow.com/a/52586193)
1. [Markdown Reference](https://guides.github.com/features/mastering-markdown/)

# References

1. [Linux Man Pages](https://linux.die.net/man/)
1. [GNU binutils: Collection of binary tools](https://www.gnu.org/software/binutils/)
   1. Install via `sudo apt install binutils`
1. [Searching Through Man Page](https://askubuntu.com/a/20753)
1. [What does `~/` mean?](https://askubuntu.com/a/85150)
1. [Shell Scripting: Loops](https://www.shellscript.sh/loops.html)
1. [Piping and Redirection](https://ryanstutorials.net/linuxtutorial/piping.php)
1. [Base64 (MDN Web Docs Glossary)](https://developer.mozilla.org/en-US/docs/Glossary/Base64)
1. [How does tr '[a-z]' '[n-za-m]' work?](https://unix.stackexchange.com/a/19774)
1. [What is SSL?](https://www.ssl.com/faqs/faq-what-is-ssl/)
1. [s_client](https://linux.die.net/man/1/s_client)
1. [Running Nmap on WSL](https://exploits.run/nmap-wsl/)
1. [Nmap Cheat Sheet](https://hackertarget.com/nmap-cheatsheet-a-quick-reference-guide/)
1. [Linux diff command](https://www.computerhope.com/unix/udiff.htm)
