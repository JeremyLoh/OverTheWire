# Bandit Level 15 -> Level 16

The password for the next level can be retrieved by submitting the password of the current level to port 30001 on `localhost` using SSL encryption.

Helpful note: Getting “HEARTBEATING” and “Read R BLOCK”? Use -ign_eof and read the “CONNECTED COMMANDS” section in the manpage. Next to ‘R’ and ‘Q’, the ‘B’ command also works in this version of that command…

# [What is SSL?](https://www.ssl.com/faqs/faq-what-is-ssl/)

Secure Sockets Layer (SSL) and its successor, Transport Layer Security (TLS), are protocols for establishing authenticated and encrypted links between networked computers. Although the SSL protocol was deprecated with the release of TLS 1.0 in 1999, it is still common to refer to these related technologies as `SSL` or `SSL/TLS`.

## Keys, Certificates and Handshakes

SSL/TLS works by binding the identities of entities to [cryptographic key pairs](https://www.ssl.com/article/private-and-public-keys/) via digital documents known as [X.509 certificates](https://www.ssl.com/faqs/what-is-an-x-509-certificate/)

Each key pair has a private and public key. The private key is kept secure and the public key are widely distributed via a certificate.

There is a special mathematical relationship between the private and public key. This allows the public key to encrypt a message that can only be decrypted with the private key. The holder of the private key can also use the private key to `sign` other digital documents (e.g. web pages), and anyone with the public key can verify this signature.

If the SSL/TLS certificate itself is signed by a `publicly trusted certificate authority (CA)` (e.g. `SSL.com`), the certificate will be implicitly trusted by client software such as web browsers and operating systems.

Via the [SSL/TLS handshake](https://www.ssl.com/article/ssl-tls-handshake-overview/), the public and private keys can be used with publicly trusted certificate to negotiate an encrypted and authenticated communication session over the internet, even between two parties who have never met. (This is the foundation of secure web browsing and electronic commerce as it is known today).

## SSL/TLS and Secure Web Browsing

The most common use of SSL/TLS is secure web browsing via the `HTTPS` protocol. A properly configured public `HTTPS` website includes an SSL/TLS certificate that is signed by a publicly trusted CA.

Users visiting a `HTPS` website can be assured of:

1. `Authenticity`. The server presenting the certificate is in possession of the private key that matches the public key in the certificate
1. `Integrity`. Documents signed by the certificate (e.g. web pages) have not been altered in transit by a man in the middle.
1. `Encryption`. Communications between the client and server are encypted.

With an insecure `HTTP` website, data are sent via plain text, readily available to any eavesdropper with access to the data stream. Users also have no trusted third party assurance that the website they are visiting is what is claims to be.

# What is TLS?

Transport Layer Security (TLS) is a cryptographic protocol designed to provide communications security over a computer network.

Several versions of the protocol are used widely in applications such as web browsing, email, instant messaging, and voice over IP (VoIP).

Websites can use TLS to secure all communications between their servers and web browsers.

The TLS protocol aims primarily to provide privacy and data integrity between two or more comunicating computer applications. When secured by TLS, connections between a client (e.g. web browser) and a server (e.g. google.com) should have one or more of the following properties:

1. The connection is private (or secure) because symmetric cryptography (using the same cryptographic keys for both encryption of plaintext and decryption of ciphertext) is used to encrypt the data transmitted. The keys for this symmetric encryption are generated uniquely for each connection and are based on a shared secret that was negotiated at the start of the session (TLS handshake). The server and client negotiate the details of which encryption algorithm and cryptographic keys to use before the first byte of data is transmited. The negotiation of a shared secret is both `secure` (the negotiated secret is unavailable to eavesdroppers and cannot be obtained, even by an attacker who places themselves in the middle of the connection) and `reliable` (no attacker can modify the communications during the negotiation without being detected).
1. The identity of the communicating parties can be authenticated using `public-key cryptography`. This authentication can be made optional, but is generally required for at least one of the parties (typically the server).
1. The connection is `reliable` because each message transmitted includes a message integrity check using a `message authentication code` (MAC) (a short piece of information used to authenticate a message - to confirm that the message came from the stated sender) to prevent undetected loss or alteration of the data during transmission.

# openssl command (OpenSSL command line tool)

OpenSSL is a cryptography toolkit implementing the Secure Sockets Layer (SSL v2/v3) and Transport Layer Security (TLS v1) network protocols and related cryptography standards required by them.

`openssl command [ command_opts ] [ command_args ]`

`openssl list [ standard-commands | digest-commands | cipher-commands | cipher-algorithms | digest-algorithms | public-key-algorithms]`

`openssl no-XXX [ arbitrary options ]`

[s_client](https://linux.die.net/man/1/s_client): command parameter to `openssl`: Implements a generic SSL/TLS client which can establish a transparent connection to a remote server speaking SSL/TLS. It's intended for testing purposes only and provides only rudimentary interface functionality but internally uses mostly all functionality of the OpenSSL ssl library.

## Useful Options of [s_client](https://linux.die.net/man/1/s_client)

1. `-conect host:port`: This specifies the host and optional port to connect to. If not specified then an attempt is made to connect to the local host on port 4433.
1. `-ign_eof`: inhibit shutting down the connection when end of file is reached in the input.

s_client can be used to debug SSL servers. To connect to an SSL HTTP server the command:

`openssl s_client -connect servername:443`

would typically be used (https uses port 443). If the connection succeeds then an HTTP command can be given such as " GET /" to retrieve a web page.

# Command

`echo BfMYroe26WYalil77FoDi9qh59eK5xNr | openssl s_client -ign_eof -connect localhost:30001`

```console
bandit15@bandit:~$ echo BfMYroe26WYalil77FoDi9qh59eK5xNr | openssl s_client -ign_eof -connect localhost:30001
CONNECTED(00000003)
depth=0 CN = localhost
verify error:num=18:self signed certificate
verify return:1
depth=0 CN = localhost
verify return:1
---
Certificate chain
 0 s:/CN=localhost
   i:/CN=localhost
---
Server certificate
-----BEGIN CERTIFICATE-----
MIICBjCCAW+gAwIBAgIEDU18oTANBgkqhkiG9w0BAQUFADAUMRIwEAYDVQQDDAls
b2NhbGhvc3QwHhcNMjAwNTA3MTgxNTQzWhcNMjEwNTA3MTgxNTQzWjAUMRIwEAYD
VQQDDAlsb2NhbGhvc3QwgZ8wDQYJKoZIhvcNAQEBBQADgY0AMIGJAoGBAK3CPNFR
FEypcqUa8NslmIMWl9xq53Cwhs/fvYHAvauyfE3uDVyyX79Z34Tkot6YflAoufnS
+puh2Kgq7aDaF+xhE+FPcz1JE0C2bflGfEtx4l3qy79SRpLiZ7eio8NPasvduG5e
pkuHefwI4c7GS6Y7OTz/6IpxqXBzv3c+x93TAgMBAAGjZTBjMBQGA1UdEQQNMAuC
CWxvY2FsaG9zdDBLBglghkgBhvhCAQ0EPhY8QXV0b21hdGljYWxseSBnZW5lcmF0
ZWQgYnkgTmNhdC4gU2VlIGh0dHBzOi8vbm1hcC5vcmcvbmNhdC8uMA0GCSqGSIb3
DQEBBQUAA4GBAC9uy1rF2U/OSBXbQJYuPuzT5mYwcjEEV0XwyiX1MFZbKUlyFZUw
rq+P1HfFp+BSODtk6tHM9bTz+p2OJRXuELG0ly8+Nf/hO/mYS1i5Ekzv4PL9hO8q
PfmDXTHs23Tc7ctLqPRj4/4qxw6RF4SM+uxkAuHgT/NDW1LphxkJlKGn
-----END CERTIFICATE-----
subject=/CN=localhost
issuer=/CN=localhost
---
No client certificate CA names sent
Peer signing digest: SHA512
Server Temp Key: X25519, 253 bits
---
SSL handshake has read 1019 bytes and written 269 bytes
Verification error: self signed certificate
---
New, TLSv1.2, Cipher is ECDHE-RSA-AES256-GCM-SHA384
Server public key is 1024 bit
Secure Renegotiation IS supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
SSL-Session:
    Protocol  : TLSv1.2
    Cipher    : ECDHE-RSA-AES256-GCM-SHA384
    Session-ID: F0C79B4ED6B90623B3F8541BC88040D59BA27680E4FCB363F98EFEF4382E95A0
    Session-ID-ctx:
    Master-Key: BFCE8241227A09AFAAA0EFD8FFFFA895EED157E1A0047D0DB8F38CCDDC64102E181DC9F6DFF722088823E9E0AAB0C508
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - aa 02 e6 3a 2e 0b c8 5d-6f 54 4a 1b 5a e0 2c 0e   ...:...]oTJ.Z.,.
    0010 - e3 d7 ce 03 39 52 c6 fc-29 99 ba 62 55 c7 16 01   ....9R..)..bU...
    0020 - d4 9b 1f b2 52 92 9f 9b-81 8f c3 6f 85 f1 3a 64   ....R......o..:d
    0030 - 04 de 59 bb ef e4 3b c6-27 3c 70 2b 03 de 81 11   ..Y...;.'<p+....
    0040 - b7 2f 3a 54 2e ed bd cf-b8 58 8c a9 c0 c4 10 0c   ./:T.....X......
    0050 - 98 83 66 e9 45 84 50 a1-1c 52 4d 71 43 ab 2a e5   ..f.E.P..RMqC.*.
    0060 - db 63 e5 58 1d 33 46 e9-31 64 e1 1c e6 66 e9 b5   .c.X.3F.1d...f..
    0070 - 2e b2 e7 1a de ab d7 0e-fb 9b 20 1d 6b aa 23 b1   .......... .k.#.
    0080 - 79 0b a1 89 b4 16 d9 00-b3 3d a5 35 b8 be d2 00   y........=.5....
    0090 - 5f 12 9a 08 08 5c 9b b6-af 77 11 28 3a b1 14 30   _....\...w.(:..0

    Start Time: 1591945438
    Timeout   : 7200 (sec)
    Verify return code: 18 (self signed certificate)
    Extended master secret: yes
---
Correct!
cluFn7wTiGryunymYOu4RcffSxQluehd

closed
```

# PASSWORD

cluFn7wTiGryunymYOu4RcffSxQluehd
