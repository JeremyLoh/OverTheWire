# Bandit Level 30 -> Level 31

There is a git repository at `ssh://bandit30-git@localhost/home/bandit30-git/repo`. The password for the user `bandit30-git` is the same as for the user `bandit30`.

Clone the repository and find the password for the next level.

# [git-tag](https://www.atlassian.com/git/tutorials/inspecting-a-repository/git-tag)

Create, list, delete or verify a tag object signed with GPG

Add a tag reference in refs/tags/, unless -d/-l/-v is given to delete, list or verify tags.

Tags are ref's that point to specific points in Git history. Tagging is generally used to capture a point in history that is used for a marked version release (i.e. v1.0.1). A tag is like a branch that doesn’t change. Unlike branches, tags, after being created, have no further history of commits.

# [git-show](https://www.atlassian.com/git/tutorials/git-show)

`git-show` is a command line utility that is used to view expanded details on Git objects such as blobs, trees, tags, and commits. `git-show` has specific behavior per object type.

Tags show the tag message and other objects included in the tag. Trees show the names and content of objects in a tree. Blobs show the direct content of the blob. Commits show a commit log message and a diff output of the changes in the commit.

# Command to execute

```console
bandit30@bandit:~$ mkdir /tmp/cloned30
bandit30@bandit:~$ cd /tmp/cloned30
bandit30@bandit:/tmp/cloned30$ git clone ssh://bandit30-git@localhost/home/bandit30-git/repo .
Cloning into '.'...
Could not create directory '/home/bandit30/.ssh'.
The authenticity of host 'localhost (127.0.0.1)' can't be established.
ECDSA key fingerprint is SHA256:98UL0ZWr85496EtCRkKlo20X3OPnyPSB5tB5RPbhczc.
Are you sure you want to continue connecting (yes/no)? yes
Failed to add the host to the list of known hosts (/home/bandit30/.ssh/known_hosts).
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit30-git@localhost's password:
remote: Counting objects: 4, done.
remote: Total 4 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (4/4), done.
bandit30@bandit:/tmp/cloned30$ ls
README.md
bandit30@bandit:/tmp/cloned30$ cat README.md
just an epmty file... muahaha

bandit30@bandit:/tmp/cloned30$ git tag
secret
bandit30@bandit:/tmp/cloned30$ git show secret
47e603bb428404d265f59c42920d81e5
```

# PASSWORD

47e603bb428404d265f59c42920d81e5
