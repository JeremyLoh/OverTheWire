# Bandit Level 5 -> Level 6

The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

1. human-readable
1. 1033 bytes in size
1. not executable

## Given directories

`maybehere00`, `maybehere01`, ... , `maybehere16`, `maybehere17`

Each file in directory may have spaces in the filename or `.` or `-`

## Check for human readable files

```shell
find . -type f
```

`find . -type [c]`

1. Where `c` is a type, f is for regular file

## Check for 1033 bytes in size file

```shell
find . -type f -size 1033c
```

`-size n`: where n is the units of space

n can contain suffixes:

1. `b` for 512-byte blocks (default if no suffix used)
1. `c` for bytes
1. `w` for two-byte words
1. `k` for Kilobytes (units of 1024 bytes)
1. `M` for Megabytes (units of 1048576 bytes)
1. `G` for Gigabytes (units of 1073741824 bytes)

## Check for files that are not executable

`-executable`: Check for files and directories which are searchable and that are executable

`\! -executable`: Check for files and directories that are not executable

## Final Command

```shell
find . -type f -size 1033c \! -executable
```

_Result_

`./maybehere07/.file2`

`cat ./maybehere07/.file2`

# PASSWORD

DXjZPULLxYr17uwoI01bNLQbtFemEgo7
