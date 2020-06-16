# Bandit Level 19 -> Level 20

To gain access to the next level, you should use the `setuid` binary in the home directory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (`/etc/bandit_pass`), after you have used the setuid binary.

# What is `setuid`?

https://www.computerhope.com/jargon/s/setuid.htm

`setuid`, which stands for `set user ID on execution`, is a special type of file permission in Unix and Unix-like operating systems such as Linux and BSD. It is a security tool that permits users to run certain programs with escalated privileges.

When an executable file's `setuid` permission is set, users may execute that program with a level of access that matches the user who owns the file.

For instance, when a user wants to change their password, they run the `passwd` command. The `passwd` program is owned by the `root` account and marked as setuid, so the user is temporarily granted root access for that very limited purpose.

## Viewing the `setuid` permission of a file

Done by viewing the file's permissions with the `ls -l` command, the `setuid` permission is displayed as an `s` in the `user execute bit position`.

e.g.

```console
ls -l /usr/bin/passwd
-rwsr-xr-x 1 root 54192 Nov 20 17:03 /usr/bin/passwd
```

## Setting the `setuid` permission of a file

Use the permission identifier `u+s` with the `chmod` command.

`chmod u+s FILENAME`

Non-executable files can be marked as `setuid`, but it has no effect. Marking them `setuid` does not automatically make them executable. In this case, the permission bit shows up as an uppercase `S`.

# Command

```console
bandit19@bandit:~$ ls
bandit20-do
bandit19@bandit:~$ ./bandit20-do
Run a command as another user.
  Example: ./bandit20-do id
bandit19@bandit:~$ ./bandit20-do id
uid=11019(bandit19) gid=11019(bandit19) euid=11020(bandit20) groups=11019(bandit19)
bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20
GbKksEFF4yrVs6il55v6gwY5aVje5f0j
```

# PASSWORD

GbKksEFF4yrVs6il55v6gwY5aVje5f0j
