# Leviathan Level 0

Leviathan’s levels are called `leviathan0`, `leviathan1`, … etc. and can be accessed on `leviathan.labs.overthewire.org` through SSH on port 2223.

To login to the first level use:

```
Username: leviathan0
Password: leviathan0
```

Data for the levels can be found in the home directories. You can look at `/etc/leviathan_pass` for the various level passwords.

# Command to execute

```console
jeremy@Jeremy-PC:~$ ssh -p 2223 leviathan0@leviathan.labs.overthewire.org
The authenticity of host '[leviathan.labs.overthewire.org]:2223 ([176.9.9.172]:2223)' can't be established.
ECDSA key fingerprint is SHA256:98UL0ZWr85496EtCRkKlo20X3OPnyPSB5tB5RPbhczc.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes

leviathan0@leviathan:~$ ls -a
.  ..  .backup  .bash_logout  .bashrc  .profile
leviathan0@leviathan:~/.backup$ ls
bookmarks.html
leviathan0@leviathan:~/.backup$ cat bookmarks.html | grep -i password
<DT><A HREF="http://leviathan.labs.overthewire.org/passwordus.html | This will be fixed later, the password for leviathan1 is rioGegei8m" ADD_DATE="1155384634" LAST_CHARSET="ISO-8859-1" ID="rdf:#$2wIU71">password to leviathan1</A>
```

# PASSWORD FOR `leviathan1`

rioGegei8m
