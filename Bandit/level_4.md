# Bandit Level 4 -> Level 5

The password for the next level is stored in the only human-readable file in the `inhere` directory. Tip: if your terminal is messed up, try the “reset” command.

## Shell Scripting: Loops

Semicolon needs to be present if running shell command as consecutive commands on the terminal.

e.g.

```shell
# Do something (echo) with all files

for i in *;
do
    echo "file $i";
done;
```

http://www.metagenomics.wiki/tools/ubuntu-linux/shell-loop

## Method to solve

1. Find file with human readable text
   1. Loop over all files in directory
   1. Use `file` command to determine file type

```shell
for i in *;
do
    file ./$i;
done;
```

_Output_

```console
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
```

_Open file with ASCII text_

```shell
cat ./-file07
```

# PASSWORD

koReBOKuIDDepwhWk7jZC0RTdopnAYKh
