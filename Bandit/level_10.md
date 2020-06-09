# Bandit Level 10 -> Level 11

The password for the next level is stored in the file data.txt, which contains base64 encoded data

# What is Base64?

Base64 is a group of binary-to-text encoding schemes that represent binary data in an ASCII string format by translating it into a radix-64 representation.

Base64 encoding schemes are commonly used when there is a need to encode binary data that needs to be stored and transfered over media that are designed to deal with ASCII.

[Base64 (MDN Web Docs Glossary)](https://developer.mozilla.org/en-US/docs/Glossary/Base64)

# base64 Command

`base64`: encode/decode data and print to standard output

`-d` flag: decode data

# Command

```console
bandit10@bandit:~$ cat data.txt
VGhlIHBhc3N3b3JkIGlzIElGdWt3S0dzRlc4TU9xM0lSRnFyeEUxaHhUTkViVVBSCg==

bandit10@bandit:~$ base64 -d data.txt
The password is IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
```

# PASSWORD

IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
