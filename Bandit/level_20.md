# Bandit Level 20 -> Level 21

There is a `setuid` binary in the home directory that does the following: it makes a connection to `localhost` on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (`bandit20`). If the password is correct, it will transmit the password for the next level (`bandit21`).

# nc command

In the simplest usage, `nc host port` creates a TCP connection to the given port on the given target host.

Your standard input is then sent to the host, and anything that comes back across the connection is sent to your standard output. This continues indefinitely, until the network side of the connection shuts down. Note that this behavior is different from most other applications which shut everything down and exit after an end-of-file on the standard input.

Netcat can also function as a server, by listening for inbound connections on arbitrary ports and then doing the same reading and writing. With minor limitations, netcat doesn't really care if it runs in "client" or "server" mode -- it still shovels data back and forth until there isn't any more left. In either mode, shutdown can be forced after a configurable time of inactivity on the network side.

# Command

Use netcat (nc) to setup a listening server that would reply with the password of `bandit20` when a connection is requested.

Server

```console
bandit20@bandit:~$ cat /etc/bandit_pass/bandit20
GbKksEFF4yrVs6il55v6gwY5aVje5f0j

bandit20@bandit:~$ cat /etc/bandit_pass/bandit20 | nc -l localhost -p 4242
gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr
```

Client

```console
bandit20@bandit:~$ ls
suconnect
bandit20@bandit:~$ ./suconnect
Usage: ./suconnect <portnumber>
This program will connect to the given port on localhost using TCP. If it receives the correct password from the other side, the next password is transmitted back.
bandit20@bandit:~$ ./suconnect 4242
Read: GbKksEFF4yrVs6il55v6gwY5aVje5f0j
Password matches, sending next password
```

# PASSWORD

gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr
