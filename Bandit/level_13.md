# Bandit Level 13 -> Level 14

The password for the next level is stored in `/etc/bandit_pass/bandit14` and can only be read by user `bandit14`. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level.

Note: `localhost` is a hostname that refers to the machine you are working on

# ssh command (OpenSSH remote login client)

`-i` option: (identity file), Selects a file from which the identity (private key) for public key authentication is read.
The default is `~/.ssh/identity` for protocol version 1, and `~/.ssh/id_dsa`, `~/.ssh/id_ecdsa`, `~/.ssh/id_ed25519` and `~/.ssh/id_rsa` for protocol version 2.

# Command

```console
bandit13@bandit:~$ ls
sshkey.private
bandit13@bandit:~$ head -n 4 sshkey.private
-----BEGIN RSA PRIVATE KEY-----
MIIEpAIBAAKCAQEAxkkOE83W2cOT7IWhFc9aPaaQmQDdgzuXCv+ppZHa++buSkN+
gg0tcr7Fw8NLGa5+Uzec2rEg0WmeevB13AIoYp0MZyETq46t+jk9puNwZwIt9XgB
ZufGtZEwWbFWw/vVLNwOXBe4UWStGRWzgPpEeSv5Tb1VjLZIBdGphTIK22Amz6Zb

bandit13@bandit:~$ ssh -i sshkey.private bandit14@localhost
Could not create directory '/home/bandit13/.ssh'.
The authenticity of host 'localhost (127.0.0.1)' can't be established.
ECDSA key fingerprint is SHA256:98UL0ZWr85496EtCRkKlo20X3OPnyPSB5tB5RPbhczc.
Are you sure you want to continue connecting (yes/no)? yes
```

# PASSWORD

N.A, Used `ssh -i sshkey.private bandit14@localhost` on bandit13@bandit.labs.overthewire.org
