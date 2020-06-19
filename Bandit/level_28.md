# Bandit Level 28 -> Level 29

There is a git repository at `ssh://bandit28-git@localhost/home/bandit28-git/repo`. The password for the user `bandit28-git` is the same as for the user `bandit28`.

Clone the repository and find the password for the next level.

# git-log

`git log [<options>] [<revision range>] [[--] <path>...]`

Shows the commit logs.
The command takes options applicable to the git rev-list command to control what is shown and how, and options
applicable to the git diff-\* commands to control how the changes each commit introduces are shown.

# git-checkout

Updates files in the working tree to match the version in the index or the specified tree. If no paths are given, git checkout will also update HEAD to set the specified branch as the current branch.

`git checkout [-q] [-f] [-m] [--detach] <commit>`

1. Prepare to work on top of <commit>, by detaching HEAD at it (see "DETACHED HEAD" section), and updating the index and the files in the working tree. Local modifications to the files in the working tree are kept, so that the resulting working tree will be the state recorded in the commit plus the local modifications.

   When the <commit> argument is a branch name, the --detach option can be used to detach HEAD at the tip of the branch (git checkout <branch> would check out that branch without detaching HEAD).

   Omitting <branch> detaches HEAD at the tip of the current branch.

# Commands to execute

```console
bandit28@bandit:~$ mkdir /tmp/cloned28
bandit28@bandit:~$ cd /tmp/cloned28
bandit28@bandit:/tmp/cloned28$ git clone ssh://bandit28-git@localhost/home/bandit28-git/repo .
Cloning into '.'...
Could not create directory '/home/bandit28/.ssh'.
The authenticity of host 'localhost (127.0.0.1)' can't be established.
ECDSA key fingerprint is SHA256:98UL0ZWr85496EtCRkKlo20X3OPnyPSB5tB5RPbhczc.
Are you sure you want to continue connecting (yes/no)? yes
Failed to add the host to the list of known hosts (/home/bandit28/.ssh/known_hosts).
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit28-git@localhost's password:
remote: Counting objects: 9, done.
remote: Compressing objects: 100% (6/6), done.
remote: Total 9 (delta 2), reused 0 (delta 0)
Receiving objects: 100% (9/9), done.
Resolving deltas: 100% (2/2), done.

bandit28@bandit:/tmp/cloned28$ ls
README.md
bandit28@bandit:/tmp/cloned28$ cat README.md
# Bandit Notes
Some notes for level29 of bandit.

## credentials

- username: bandit29
- password: xxxxxxxxxx

bandit28@bandit:/tmp/cloned28$ git log
commit edd935d60906b33f0619605abd1689808ccdd5ee
Author: Morla Porla <morla@overthewire.org>
Date:   Thu May 7 20:14:49 2020 +0200

    fix info leak

commit c086d11a00c0648d095d04c089786efef5e01264
Author: Morla Porla <morla@overthewire.org>
Date:   Thu May 7 20:14:49 2020 +0200

    add missing data

commit de2ebe2d5fd1598cd547f4d56247e053be3fdc38
Author: Ben Dover <noone@overthewire.org>
Date:   Thu May 7 20:14:49 2020 +0200

    initial commit of README.md

bandit28@bandit:/tmp/cloned28$ git checkout c086d11a00c06
Note: checking out 'c086d11a00c06'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b <new-branch-name>

HEAD is now at c086d11... add missing data
bandit28@bandit:/tmp/cloned28$ ls
README.md
bandit28@bandit:/tmp/cloned28$ cat README.md
# Bandit Notes
Some notes for level29 of bandit.

## credentials

- username: bandit29
- password: bbc96594b4e001778eee9975372716b2

```

# Alternative method

Use `git log -p` to check the diff introduced in each commit

We can limit the output to only the last entry using `-1` (`git log -p -1`)

# PASSWORD

bbc96594b4e001778eee9975372716b2
