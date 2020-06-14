# Bandit Level 17 -> Level 18

There are 2 files in the homedirectory: `passwords.old` and `passwords.new`. The password for the next level is in `passwords.new` and is the only line that has been changed between `passwords.old` and `passwords.new`

`NOTE`: if you have solved this level and see ‘Byebye!’ when trying to log into `bandit18`, this is related to the next level, `bandit19`

# chmod command

Change file permissions

`chmod` changes the file mode bits of each given file according to mode, which can be either a symbolic representation of changes to make, or an octal number representing the bit pattern for the new mode bits.

A numeric mode is from one to four octal digits (0-7), derived by adding up the bits with values 4, 2, and 1. Omitted digits are assumed to be leading zeros.

The first digit selects the set user ID (4) and set group ID (2) and restricted deletion or sticky (1) attributes.

The second digit selects permissions for the user who owns the file: read (4), write (2), and execute (1); the third selects permissions for other users in the file's group, with the same values; and the fourth for other users not in the file's group, with the same values.

# diff command

Compare files line by line

# Command

```console
jeremy@Jeremy-PC:~$ ls -l
total 4
-rwxrwxrwx 1 jeremy jeremy 1700 Jun 14 20:10 bandit17.key
jeremy@Jeremy-PC:~$ chmod 700 bandit17.key
jeremy@Jeremy-PC:~$ ls -l
total 4
-rwx------ 1 jeremy jeremy 1700 Jun 14 20:10 bandit17.key
jeremy@Jeremy-PC:~$ ssh -p 2220 bandit17@bandit.labs.overthewire.org -i bandit17.key
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit17@bandit:~$ diff passwords.new passwords.old
42c42
< kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
---
> w0Yfolrc5bwjS4qw5mq1nnQi6mF03bii
```

# PASSWORD

kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
