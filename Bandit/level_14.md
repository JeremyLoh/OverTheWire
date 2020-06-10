# Bandit Level 14 -> Level 15

The password for the next level can be retrieved by submitting the password of the current level to port 30000 on `localhost`.

# What is `localhost`

`localhost` is a hostname that refers to the current computer used to access it. It is used to access the network services that are running on the host via the loopback network interface. Using the loopback interface bypasses any local network interface hardware

# Ports

Any server machine makes its services available to the internet using numbered ports, one for each service that is available on the server.

e.g. If a server machine is running a Web Server and an FTP server, the Web Server would typically be running on port 80 and the FTP server would be available on port 21.

Clients would then connect to a service at a specific IP address and on a specific port.

If the server machine accepts connections on a port from the outside world, and if a firewall is not protecting the port, you can connect to the port from anywhere on the Internet and use the service. Note that there is nothing that forces, for example, a Web server to be on port 80. If you were to set up your own machine and load Web server software on it, you could put the Web server on port 918, or any other unused port, if you wanted to. Then, if your machine were known as xxx.yyy.com, someone on the Internet could connect to your server with the URL `http://xxx.yyy.com:918`. The ":918" explicitly specifies the port number, and would have to be included for someone to reach your server. When no port is specified, the browser simply assumes that the server is using the well-known port 80.

# echo command (display a line of text)

```console
echo [SHORT-OPTION]... [STRING]...
echo LONG-OPTION
```

Echo the STRING(s) to standard output.

# nc command (arbitrary TCP and UDP connections and listens)

The `nc` (or netcat) utility is used for just about anything under the sun involving TCP, UDP, or UNIX-domain sockets. It can open TCP connections, send UDP packets, listen on arbitrary TCP and UDP ports, do port scanning, and deal with both IPv4 and IPv6. Unlike telnet(1), `nc` scripts nicely, and separates error messages onto standard error instead of sending them to standard output, as telnet(1) does with some.

`-N` flag: Shutdown(2) the network socket after EOF on the input. Some servers require this to finish their work

# Command

```console
bandit14@bandit:~$ echo 4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e | nc localhost 30000
Correct!
BfMYroe26WYalil77FoDi9qh59eK5xNr
```

# PASSWORD

BfMYroe26WYalil77FoDi9qh59eK5xNr
