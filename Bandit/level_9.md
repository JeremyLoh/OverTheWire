# Bandit Level 9 -> Level 10

The password for the next level is stored in the file `data.txt` in one of the few human-readable strings, preceded by several ‘=’ characters.

# grep command

By default, linux uses GNU grep

```console
bandit9@bandit:~$ grep -V
grep (GNU grep) 2.27
```

`-P` flag: Use Perl-compatible regular expressions (PCREs)

e.g. \d{3}-\d{3}-\d{4}

# strings command

[GNU binutils: Collection of binary tools](https://www.gnu.org/software/binutils/)

Install via `sudo apt install binutils`

Print the sequences of printable characters in files
For each file given, GNU strings prints the printable character sequences that are at least 4 characters long
(or the number given with the options below) and are followed by an unprintable character.

# Command

```console
bandit9@bandit:~$ strings data.txt | grep -P "=+ "
========== the*2i"4
========== password
Z)========== is
&========== truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
```

# PASSWORD

truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
