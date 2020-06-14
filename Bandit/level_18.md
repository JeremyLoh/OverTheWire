# Bandit Level 18 -> Level 19

The password for the next level is stored in a file `readme` in the home directory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.

# ssh command

`ssh [-46AaCfGgKkMNnqsTtVvXxYy] [-B bind_interface] [-b bind_address] [-c cipher_spec] [-D [bind_address:]port] [-E log_file] [-e escape_char] [-F configfile] [-I pkcs11] [-i identity_file] [-J destination] [-L address] [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port] [-Q query_option] [-R address] [-S ctl_path] [-W host:port] [-w local_tun[:remote_tun]] destination [command]`

ssh (SSH client) is a program for logging into a remote machine and for executing commands on a remote machine.

It is intended to provide secure encrypted communications between two untrusted hosts over an insecure network. X11 connections, arbitrary TCP ports and UNIX-domain sockets can also be forwarded over the secure channel.

ssh connects and logs into the specified destination, which may be specified as either [user@]hostname or a URI of the form ssh://[user@]hostname[:port]. The user must prove his/her identity to the remote machine.

If a command is specified, it is executed on the remote host instead of a login shell.

# Command

```console
jeremy@Jeremy-PC:~$ ssh -p 2220 bandit18@bandit.labs.overthewire.org "cat readme"
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit18@bandit.labs.overthewire.org's password:
IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x
```

# PASSWORD

IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x
