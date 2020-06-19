# Bandit Level 27 -> Level 28

There is a git repository at `ssh://bandit27-git@localhost/home/bandit27-git/repo`. The password for the user `bandit27-git` is the same as for the user `bandit27`.

Clone the repository and find the password for the next level.

# `git-clone`

Using `git clone` to clone repository to directory

1. `git clone <repository> <directory>`

   `repository`: The (possibly remote) repository to clone from. See the GIT URLS section below for more information on specifying repositories.

   `directory`: The name of a new directory to clone into. The "humanish" part of the source repository is used if no directory is explicitly given (repo for /path/to/repo.git and foo for host.xz:foo/.git). Cloning into an existing directory is only allowed if the directory is empty.

## GIT URL

In general, URLs contain information about the transport protocol, the address of the remote server, and the path to the repository. Depending on the transport protocol, some of this information may be absent.

Git supports ssh, git, http, and https protocols (in addition, ftp, and ftps can be used for fetching, but this is inefficient and deprecated; do not use it).

The native transport (i.e. git:// URL) does no authentication and should be used with caution on unsecured networks.

e.g. For SSH,

`ssh://[user@]host.xz[:port]/path/to/repo.git/`

In this case, the password for the ssh is the password for user bandit27

# Command to execute

```console
bandit27@bandit:~$ mkdir /tmp/cloned27
bandit27@bandit:~$ cd /tmp/cloned27

bandit27@bandit:/tmp/cloned27$ git clone ssh://bandit27-git@localhost/home/bandit27-git/repo .
Cloning into '.'...
Could not create directory '/home/bandit27/.ssh'.
The authenticity of host 'localhost (127.0.0.1)' can't be established.
ECDSA key fingerprint is SHA256:98UL0ZWr85496EtCRkKlo20X3OPnyPSB5tB5RPbhczc.
Are you sure you want to continue connecting (yes/no)? yes
Failed to add the host to the list of known hosts (/home/bandit27/.ssh/known_hosts).
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit27-git@localhost's password:
remote: Counting objects: 3, done.
remote: Compressing objects: 100% (2/2), done.
Receiving objects: 100% (3/3), 287 bytes | 0 bytes/s, done.
remote: Total 3 (delta 0), reused 0 (delta 0)
bandit27@bandit:/tmp/cloned27$ ls
README

bandit27@bandit:/tmp/cloned27$ cat README
The password to the next level is: 0ef186ac70e04ea33b4c1853d2526fa2
```

# PASSWORD

0ef186ac70e04ea33b4c1853d2526fa2
