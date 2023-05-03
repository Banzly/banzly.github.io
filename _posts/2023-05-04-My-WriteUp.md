---
title: CTF WRITEUP
date: 2023-05-02 02:54:40 +/-TTTT
categories: [ctf, learning]
tags: [ctf]     # TAG names should always be lowercase
---

# ANGSTROM CTF 2023 
* Category Web

`SPEED RUN `

Celeste Speedrunning Associationweb20704 I love Celeste Speedrunning so much!!! It's so funny to watch!!!

Here's my favorite site!

Author: paper

# Recon
When entering the website, there is a chall definition:

Welcome to Celeste's speedrun records!!! Current record holder (beat them in /play for a flag!): Old Lady: 0 seconds Madeline: 10 seconds Badeline: 10.1 seconds

In the directory: `https://mount-tunnel.web.actf.co/play` If we look at the source code :
```html
<form action="/submit" method="POST">
  <input type="text" style="display: none;" value="1682888046.9222546" name="start" />
  <input type="submit" value="Press when done!" />
</form>
```

Keep in mind the action form refers/submit with the method: POST.

So....????

How to finish?
```py
import requests

r = requests.post("https://chall/submit", data={"start":"1685888046.9222546"}) #change random value 
print(r.text)
```
Flag : 
```
actf{wait_until_farewell_speedrun}
```

`DIRECTORY`

This is one of the directories of all time, and I would definitely rate it out of 10.

Author: JoshDaBosh

Lets Open web: Simple web which has 5000 folders on the web.

when i try to view one folder it just shows text : `your flag is in another file`

# How To Solve?
```py
wget -r -np https://directory.web.actf.co/

# -r to another page on the same website and download it too.
# -np Options from the url to start with

# grep -r "actf" .
```

# flag
```
actf{y0u_f0und_me_b51d0cde76739fa3}
```