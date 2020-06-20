# Leviathan Level 1

```console
leviathan1@leviathan:~$ ls
check
leviathan1@leviathan:~$ file check
check: setuid ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=c735f6f3a3a94adcad8407cc0fda40496fd765dd, not stripped
leviathan1@leviathan:~$ ./check
password: password
Wrong password, Good Bye ...
```

Check for printable characters in `check` using `strings`

# `strings` - print the strings of printable characters in files

For each file given, GNU strings prints the printable character sequences that are at least 4 characters long (or the number given with the options below) and are followed by an unprintable character.

strings is mainly useful for determining the contents of non-text files.

To give minimum character sequence length, provide option `-n min-len`.

```console
leviathan1@leviathan:~$ strings -n 2 check
ELF
td
td
td
/lib/ld-linux.so.2
GNU
GNU
@Io
libc.so.6
_IO_stdin_used
puts
setreuid
printf
getchar
system
geteuid
strcmp
__libc_start_main
__gmon_start__
GLIBC_2.0
ii
h
%
h(
%$
h0
%(
h8
PTRhp
QVh;
-4
h4
t&
-4
Ph4
t&
=4
L$
SQ
sex
secrf
et
god
love
u+
SP
Y[]
UWVS
l$
t%1
t$,
t$,U
[^_]
password:
/bin/sh
Wrong password, Good Bye ...
;0
zR
;*2$"
ux
u|
 i
$D
(D
,A
0M
 G
GCC: (Debian 6.3.0-18+deb9u1) 6.3.0 20170516
crtstuff.c
__JCR_LIST__
deregister_tm_clones
__do_global_dtors_aux
completed.6587
__do_global_dtors_aux_fini_array_entry
frame_dummy
__frame_dummy_init_array_entry
check.c
__FRAME_END__
__JCR_END__
__init_array_end
_DYNAMIC
__init_array_start
__GNU_EH_FRAME_HDR
_GLOBAL_OFFSET_TABLE_
__libc_csu_fini
strcmp@@GLIBC_2.0
__x86.get_pc_thunk.bx
printf@@GLIBC_2.0
getchar@@GLIBC_2.0
_edata
geteuid@@GLIBC_2.0
__data_start
puts@@GLIBC_2.0
system@@GLIBC_2.0
__gmon_start__
__dso_handle
_IO_stdin_used
setreuid@@GLIBC_2.0
__libc_start_main@@GLIBC_2.0
__libc_csu_init
_fp_hw
__bss_start
main
__TMC_END__
.symtab
.strtab
.shstrtab
.interp
.note.ABI-tag
.note.gnu.build-id
.gnu.hash
.dynsym
.dynstr
.gnu.version
.gnu.version_r
.rel.dyn
.rel.plt
.init
.plt.got
.text
.fini
.rodata
.eh_frame_hdr
.eh_frame
.init_array
.fini_array
.jcr
.dynamic
.got.plt
.data
.bss
.comment
```

# [Spying on Running Programs (strace. ltrace, system calls vs library calls)](https://www.youtube.com/watch?v=2AmP7Pse4U0)

System call - When a process requests something from the operating system

Viewing system calls in linux

`man syscalls`

Library call - When a process requests into an existing library (e.g. C standard library) (might call system calls, could keep process in user mode)

`strace` - trace system calls and signals

1. In the simplest case strace runs the specified command until it exits. It intercepts and records the system calls which are called by a process and the signals which are received by a process. The name of each system call, its arguments and its return value are printed on standard error or to the file specified with the -o option.

`ltrace` - A library call tracer

1. ltrace is a program that simply runs the specified command until it exits. It intercepts and records the dynamic library calls which are called by the executed process and the signals which are received by that process. It can also intercept and print the system calls executed by the program. Its use is very similar to strace(1).

# Checking library calls made by `check`

```console
leviathan1@leviathan:~$ ltrace ./check
__libc_start_main(0x804853b, 1, 0xffffd784, 0x8048610 <unfinished ...>
printf("password: ")                                                      = 10
getchar(1, 0, 0x65766f6c, 0x646f6700password: idk
)                                     = 105
getchar(1, 0, 0x65766f6c, 0x646f6700)                                     = 100
getchar(1, 0, 0x65766f6c, 0x646f6700)                                     = 107
strcmp("idk", "sex")                                                      = -1
puts("Wrong password, Good Bye ..."Wrong password, Good Bye ...
)                                      = 29
+++ exited (status 0) +++
```

# PASSWORD

`sex`
