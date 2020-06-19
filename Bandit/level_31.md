# Bandit Level 31 -> Level 32

There is a git repository at `ssh://bandit31-git@localhost/home/bandit31-git/repo`. The password for the user `bandit31-git` is the same as for the user `bandit31`.

Clone the repository and find the password for the next level.

# [.gitignore](https://www.atlassian.com/git/tutorials/saving-changes/gitignore)

Git sees every file in your working copy as one of three things:

1. `tracked` - a file which has been previously staged or committed
1. `untracked` - a file which has not been staged or committed
1. `ignored` - a file which Git has been explicitly told to ignore

Ignored files are usually build artifacts and machine generated files that can be derived from your repository source or should otherwise not be committed. Some common examples are:

1. dependency caches, such as the contents of `/node_modules` or `/packages`
1. compiled code, e.g. `.o`, `.class`, `.pyc` files
1. build output directories, e.g. `/bin`, `/out`, `/target`
1. files generated at runtime, e.g. `.log`, `.lock`, `.tmp`
1. hidden system files, e.g. `.DS_Store`, `Thumbs.db`
1. personal IDE config files, e.g. `.idea/workspace.xml`

Ignored files are tracked in a special file named `.gitignore` that is checked in at the root of your repository. There is no explicit git ignore command: instead the `.gitignore` file must be edited and committed by hand when you have new files that you wish to ignore. `.gitignore` files contain patterns that are matched against file names in your repository to determine whether or not they should be ignored.

# Command to execute

```console
bandit31@bandit:~$ mkdir /tmp/cloned31
bandit31@bandit:~$ cd /tmp/cloned31
bandit31@bandit:/tmp/cloned31$ git clone ssh://bandit31-git@localhost/home/bandit31-git/repo .
Cloning into '.'...
Could not create directory '/home/bandit31/.ssh'.
The authenticity of host 'localhost (127.0.0.1)' can't be established.
ECDSA key fingerprint is SHA256:98UL0ZWr85496EtCRkKlo20X3OPnyPSB5tB5RPbhczc.
Are you sure you want to continue connecting (yes/no)? yes
Failed to add the host to the list of known hosts (/home/bandit31/.ssh/known_hosts).
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit31-git@localhost's password:
remote: Counting objects: 4, done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 4 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (4/4), done.

bandit31@bandit:/tmp/cloned31$ ls
README.md
bandit31@bandit:/tmp/cloned31$ cat README.md
This time your task is to push a file to the remote repository.

Details:
    File name: key.txt
    Content: 'May I come in?'
    Branch: master

bandit31@bandit:/tmp/cloned31$ echo May I come in? > key.txt
bandit31@bandit:/tmp/cloned31$ ls
key.txt  README.md

bandit31@bandit:/tmp/cloned31$ ls -a
.  ..  .git  .gitignore  key.txt  README.md
bandit31@bandit:/tmp/cloned31$ cat .gitignore
*.txt
bandit31@bandit:/tmp/cloned31$ vim .gitignore
bandit31@bandit:/tmp/cloned31$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   .gitignore

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        key.txt

no changes added to commit (use "git add" and/or "git commit -a")

bandit31@bandit:/tmp/cloned31$ git add key.txt
bandit31@bandit:/tmp/cloned31$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   key.txt

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   .gitignore

bandit31@bandit:/tmp/cloned31$ git commit -m "Add key.txt"
[master 9c6a6be] Add key.txt
 1 file changed, 1 insertion(+)
 create mode 100644 key.txt

bandit31@bandit:/tmp/cloned31$ git remote
origin
bandit31@bandit:/tmp/cloned31$ git push origin master
Could not create directory '/home/bandit31/.ssh'.
The authenticity of host 'localhost (127.0.0.1)' can't be established.
ECDSA key fingerprint is SHA256:98UL0ZWr85496EtCRkKlo20X3OPnyPSB5tB5RPbhczc.
Are you sure you want to continue connecting (yes/no)? yes
Failed to add the host to the list of known hosts (/home/bandit31/.ssh/known_hosts).
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit31-git@localhost's password:
Counting objects: 3, done.
Delta compression using up to 2 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 322 bytes | 0 bytes/s, done.
Total 3 (delta 0), reused 0 (delta 0)
remote: ### Attempting to validate files... ####
remote:
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote:
remote: Well done! Here is the password for the next level:
remote: 56a9bf19c63d650ce78e6ec0354ee45e
remote:
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote:
To ssh://localhost/home/bandit31-git/repo
 ! [remote rejected] master -> master (pre-receive hook declined)
error: failed to push some refs to 'ssh://bandit31-git@localhost/home/bandit31-git/repo'
```

# PASSWORD

56a9bf19c63d650ce78e6ec0354ee45e
