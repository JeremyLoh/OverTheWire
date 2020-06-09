# Bandit Level 11 -> Level 12

The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

# Rot13 Algorithm

ROT13 ("rotate by 13 places", sometimes hyphenated ROT-13) is a simple letter substitution cipher that replaces a letter with the 13th letter after it, in the alphabet. ROT13 is a special case of the Caesar cipher which was developed in ancient Rome.

## Mapping

a-m => n-z

    1. abcdefghijklm => nopqrstuvwxyz

n-z => a-m

    1. nopqrstuvwxyz => abcdefghijklm

# tr command

```console
tr [OPTION]... SET1 [SET2]
```

Translate, squeeze, and/or delete characters from `standard input`, writing to `standard output`.

It converts characters from one set to another (if SET2 is given).

[How does tr '[a-z]' '[n-za-m]' work?](https://unix.stackexchange.com/a/19774)

# Command

Redirect `data.txt` to `tr` command

```console
bandit11@bandit:~$ tr [a-zA-Z] [n-za-mN-ZA-M] < data.txt
The password is 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
```

# PASSWORD

5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
