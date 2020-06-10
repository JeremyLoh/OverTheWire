# Bandit Level 12 -> Level 13

The password for the next level is stored in the file `data.txt`, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)

# What is a hex dump?

A hex dump is a hexadecimal view of computer data, from RAM or from a computer file or storage device.

Looking at a hex dump of data is usually done in the context of either debugging or reverse engineering.

In a hex dump, each byte (8 bits) is represented as a two-digit hexadecimal number.

Hex dumps are commonly organized into rows of 8 or 16 bytes, sometimes separated by whitespaces.

Some hex dumps have the hexadecimal memory address at the beginning and/or a checksum byte at the end of each line.

# xxd command

Make a hexdump or do the reverse.

## xxd command format

1. xxd -h[elp]
1. xxd [options]infile [outfile]]
1. xxd -r[evert][options] [infile [outfile]]

xxd creates a hex dump of a given file or standard input. It can also convert a hex dump back to its original binary form

If no `infile` is given, standard input is read.

If `infile` is specified as a `-` character, then input is taken from standard input.

If no `outfile` is given (or a `-` character is in its place), the results are sent to standard output.

## Converting hexdump to binary

`-r` flag: Reverse operation, convert (or patch) hexdump into binary. If not writing to stdout, xxd writes into its output file without truncating it. Use the combination -r -p to read plain hexadecimal dumps without line number information and without a particular column layout. Additional Whitespace and line breaks are allowed anywhere.

# tar (an archiving utility)

GNU tar is an archiving program designed to store multiple files in a single file (an archive), and to manipulate such archives. The archive can be either a regular file or a device (e.g. a tape drive, hence the name of the program, which stands for tape archiver), which can be located either on the local or on a remote machine.

`x` option is used to extract files from an archive.

`f` option takes an argument that sets the name of the archive to operate upon.

`tar -xf ARCHIVE.tar`

# gzip (file extension .gz) (Compress or expand files)

Gzip reduces the size of the named files using Lempel-Ziv coding (LZ77). Whenever possible, each file is replaced by one with the extension .gz, while keeping the same ownership modes, access and modification times.

By default, gzip keeps the original file name and timestamp in the compressed file.

Compressed files can be restored to their original form using gzip -d or gunzip or zcat. If the original name saved in the compressed file is not suitable for its file system, a new name is constructed from the original one to make it legal.

`-d` option: To decompress gzip files

# bzip2, bunzip2 (possible file extension .bz2) (File compression method)

bzip2 expects a list of file names to accompany the command-line flags. Each file is replaced by a compressed version of itself, with the name "original_name.bz2"

bzip2 and bunzip2 will by default not overwrite existing files. If you want this to happen, specify the `-f` flag

e.g. `bzip2 -d FILENAME.bz2`

# Commands to execute

1. Make temp directory
   1. `mkdir /tmp/dir`
1. Copy `data.txt` to temp directory
   1. `cp ~/data.txt /tmp/dir`
1. Reverse hex dump and store the file with its original name, `data`

1. Check file type of `data`
   1. `file data`
1. Rename `data` to its correct file extension
1. Perform relevant decompression of file

```console
bandit12@bandit:~$ ls
data.txt

bandit12@bandit:~$ mkdir /tmp/dir
bandit12@bandit:~$ cp ~/data.txt /tmp/dir
bandit12@bandit:~$ cd /tmp/dir
bandit12@bandit:/tmp/dir$ ls
data.txt

bandit12@bandit:/tmp/dir$ xxd -r data.txt data
bandit12@bandit:/tmp/dir$ ls
data  data.txt
bandit12@bandit:/tmp/dir$ file data
data: gzip compressed data, was "data2.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix

bandit12@bandit:/tmp/dir$ mv data data2.gz
bandit12@bandit:/tmp/dir$ ls
data2.gz  data.txt
bandit12@bandit:/tmp/dir$ gzip -d data2.gz
bandit12@bandit:/tmp/dir$ ls
data2  data.txt
bandit12@bandit:/tmp/dir$ file data2
data2: bzip2 compressed data, block size = 900k

bandit12@bandit:/tmp/dir$ mv data2 data3.bz2
bandit12@bandit:/tmp/dir$ ls
data3.bz2  data.txt
bandit12@bandit:/tmp/dir$ bzip2 -d data3.bz2
bandit12@bandit:/tmp/dir$ ls
data3  data.txt
bandit12@bandit:/tmp/dir$ file data3
data3: gzip compressed data, was "data4.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix

bandit12@bandit:/tmp/dir$ mv data3 data4.gz
bandit12@bandit:/tmp/dir$ ls
data4.gz  data.txt
bandit12@bandit:/tmp/dir$ gzip -d data4.gz
bandit12@bandit:/tmp/dir$ ls
data4  data.txt
bandit12@bandit:/tmp/dir$ file data4
data4: POSIX tar archive (GNU)

bandit12@bandit:/tmp/dir$ mv data4 data5.tar
bandit12@bandit:/tmp/dir$ ls
data5.tar  data.txt
bandit12@bandit:/tmp/dir$ tar -xf data5.tar
bandit12@bandit:/tmp/dir$ ls
data5.bin  data5.tar  data.txt
bandit12@bandit:/tmp/dir$ file data5.bin
data5.bin: POSIX tar archive (GNU)

bandit12@bandit:/tmp/dir$ mv data5.bin data6.tar
bandit12@bandit:/tmp/dir$ ls
data5.tar  data6.tar  data.txt
bandit12@bandit:/tmp/dir$ tar -xf data6.tar
bandit12@bandit:/tmp/dir$ ls
data5.tar  data6.bin  data6.tar  data.txt
bandit12@bandit:/tmp/dir$ file data6.bin
data6.bin: bzip2 compressed data, block size = 900k

bandit12@bandit:/tmp/dir$ mv data6.bin data7.bz2
bandit12@bandit:/tmp/dir$ ls
data5.tar  data6.tar  data7.bz2  data.txt
bandit12@bandit:/tmp/dir$ bzip2 -d data7.bz2
bandit12@bandit:/tmp/dir$ ls
data5.tar  data6.tar  data7  data.txt
bandit12@bandit:/tmp/dir$ file data7
data7: POSIX tar archive (GNU)

bandit12@bandit:/tmp/dir$ mv data7 data8.tar
bandit12@bandit:/tmp/dir$ ls
data5.tar  data6.tar  data8.tar  data.txt
bandit12@bandit:/tmp/dir$ tar -xf data8.tar
bandit12@bandit:/tmp/dir$ ls
data5.tar  data6.tar  data8.bin  data8.tar  data.txt
bandit12@bandit:/tmp/dir$ file data8.bin
data8.bin: gzip compressed data, was "data9.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix

bandit12@bandit:/tmp/dir$ mv data8.bin data9.gz
bandit12@bandit:/tmp/dir$ gzip -d data9.gz
bandit12@bandit:/tmp/dir$ ls
data5.tar  data6.tar  data8.tar  data9  data.txt
bandit12@bandit:/tmp/dir$ file data9
data9: ASCII text
bandit12@bandit:/tmp/dir$ cat data9
The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
```

# PASSWORD

8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
