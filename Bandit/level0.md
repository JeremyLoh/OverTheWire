# Bandit Level 0

The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0.

## SSH Command in Linux

The ssh command provides a secure encrypted connection between two hosts over an insecure network. This connection can also be used for terminal access, file transfers, and for tunneling other applications. Graphical X11 applications can also be run securely over SSH from a remote location.

https://www.ssh.com/ssh/command/

## Specifying different username

`ssh alternative-user@sample.ssh.com`

## Executing remote commands on the server (without login)

`ssh hostname command`
e.g. `ssh sample.ssh.com ls -la`

Once host is added (server to connect to), it will be added to the list of known hosts (~/.ssh/known_hosts)

Each server has a [host key](https://www.ssh.com/ssh/host-key), (A cyptographic key used to authenticate computers in the SSH protocol)

## Specifying port number

With _-p_ flag
e.g. `ssh -p 2220 bandit0@bandit.labs.overthewire.org`
