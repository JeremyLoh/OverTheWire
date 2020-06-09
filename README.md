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

Finding a line of text (password) in `data.txt` that only occurs once.

# References

1. [Searching Through Man Page](https://askubuntu.com/a/20753)
1. [What does `~/` mean?](https://askubuntu.com/a/85150)
1. [Shell Scripting: Loops](https://www.shellscript.sh/loops.html)
1. [Piping and Redirection](https://ryanstutorials.net/linuxtutorial/piping.php)
