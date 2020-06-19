# Bandit Level 29 -> Level 30

There is a git repository at `ssh://bandit29-git@localhost/home/bandit29-git/repo`. The password for the user `bandit29-git` is the same as for the user `bandit29`.

Clone the repository and find the password for the next level.

# git-branch

An `-r` option can be given to list all the remote-tracking branches.

An `-a` shows both local and remote branches.

1. Git local branch

   A local branch is a branch that only the local user can see. It exists on the local machine

1. Git remote branch

   A remote branch is a branch on a remote location (most cases `origin`). You can push any newly created local branch to the remote branch. This allows for other users to track it!

# Command to execute

```console
bandit29@bandit:~$ mkdir /tmp/cloned29
bandit29@bandit:~$ cd /tmp/cloned29

bandit29@bandit:/tmp/cloned29$ git clone ssh://bandit29-git@localhost/home/bandit29-git/repo .
Cloning into '.'...
Could not create directory '/home/bandit29/.ssh'.
The authenticity of host 'localhost (127.0.0.1)' can't be established.
ECDSA key fingerprint is SHA256:98UL0ZWr85496EtCRkKlo20X3OPnyPSB5tB5RPbhczc.
Are you sure you want to continue connecting (yes/no)? yes
Failed to add the host to the list of known hosts (/home/bandit29/.ssh/known_hosts).
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit29-git@localhost's password:
remote: Counting objects: 16, done.
remote: Compressing objects: 100% (11/11), done.
remote: Total 16 (delta 2), reused 0 (delta 0)
Receiving objects: 100% (16/16), done.
Resolving deltas: 100% (2/2), done.
bandit29@bandit:/tmp/cloned29$ ls
README.md
bandit29@bandit:/tmp/cloned29$ cat README.md
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: <no passwords in production!>

bandit29@bandit:/tmp/cloned29$ git branch -a
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/dev
  remotes/origin/master
  remotes/origin/sploits-dev

bandit29@bandit:/tmp/cloned29$ git checkout dev
Branch dev set up to track remote branch dev from origin.
Switched to a new branch 'dev'
bandit29@bandit:/tmp/cloned29$ ls
code  README.md

bandit29@bandit:/tmp/cloned29$ cat README.md
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: 5b90576bedb2cc04c86a9e924ce42faf

```

# PASSWORD

5b90576bedb2cc04c86a9e924ce42faf
