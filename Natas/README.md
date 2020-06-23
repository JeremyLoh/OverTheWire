Natas teaches the basics of serverside web-security.

Each level of natas consists of its own website located at `http://natasX.natas.labs.overthewire.org`, where X is the level number. There is no SSH login. To access a level, enter the username for that level (e.g. natas0 for level 0) and its password.

Each level has access to the password of the next level. Your job is to somehow obtain that next password and level up. All passwords are also stored in `/etc/natas_webpass/`. E.g. the password for `natas5` is stored in the file `/etc/natas_webpass/natas5` and only readable by `natas4` and `natas5`.

Start here:

Username: natas0

Password: natas0

URL: http://natas0.natas.labs.overthewire.org

# References

1. [World Wide Web](https://developer.mozilla.org/en-US/docs/Glossary/World_Wide_Web)
1. [What is an Internet search engine?](https://developer.mozilla.org/en-US/docs/Glossary/Search_engine)
1. [Introduction to `robots.txt`](https://support.google.com/webmasters/answer/6062608?hl=en)
1. [HTTP Headers](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers)
1. [Using HTTP cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)
1. [Stateful information for the stateless HTTP protocol](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview#HTTP_is_stateless_but_not_sessionless)
