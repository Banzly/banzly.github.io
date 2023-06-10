---
title: PYTHON REQUEST
date: 2023-06-11 00:29:40 +/-TTTT
categories: [learning, web]
tags: [ctf]     # TAG names should always be lowercase
---

# Python’s Requests Library 

`Requests library` is one of the integral part of Python for making HTTP requests to a specified URL. Whether it be REST APIs or Web Scraping, requests is must to be learned for proceeding further with these technologies. When one makes a request to a URI, it returns a response. Python requests provides inbuilt functionalities for managing both the request and response.

`Why learn Python requests module?`

Requests is an Apache2 Licensed HTTP library, that allows to send HTTP/1.1 requests using Python.
To play with web, Python Requests is must. Whether it be hitting APIs, downloading entire facebook pages, and much more cool stuff, one will have to make a request to the URL.
Requests play a major role is dealing with `REST APIs`, and `Web Scraping`.
Checkout an Example Python Script using Requests and Web Scraping – Implementing Web Scraping in Python with `BeautifulSoup`.

# Installing Requests
```
pip install requests
```

# Making a Request

`Python requests` module has several built-in methods to make Http requests to specified URI using `GET, POST, PUT, PATCH or HEAD requests`. A Http request is meant to either retrieve data from a specified URI or to push data to a server. It works as a request-response protocol between a client and a server. Let’s demonstrate how to make a GET request to an `endpoint`.

GET method is used to retrieve information from the given server using a given URI. The GET method sends the encoded user information appended to the page request. The page and the encoded information are separated by the `?` character.

For example:
```
https://www.example.com/search?q=hello

```

Python’s requests module provides in-built method called `get()` for making a GET request to a specified URI.

* `HTTP METHOD `

| Method | Description                                                                                                                  |
|--------|------------------------------------------------------------------------------------------------------------------------------|
| GET    | GET method is used to retrieve information from the given server using a given URI.                                         |
| POST   | POST request method requests that a web server accepts the data enclosed in the body of the request message, most likely for storing it. |
| PUT    | The PUT method requests that the enclosed entity be stored under the supplied URI. If the URI refers to an already existing resource, it is modified and if the URI does not point to an existing resource, then the server can create the resource with that URI. |
| DELETE | The DELETE method deletes the specified resource.                                                                             |
| HEAD   | The HEAD method asks for a response identical to that of a GET request, but without the response body.                       |
| PATCH  | It is used for modify capabilities. The PATCH request only needs to contain the changes to the resource, not the complete resource. |


* `Response Method`

| Method/Attribute                     | Description                                                                                                                |
|--------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| response.headers                     | Returns a dictionary of response headers.                                                                                  |
| response.encoding                    | Returns the encoding used to decode `response.content`.                                                                    |
| response.elapsed                     | Returns a `timedelta` object with the time elapsed from sending the request to the arrival of the response.                |
| response.close()                     | Closes the connection to the server.                                                                                       |
| response.content                     | Returns the content of the response, in bytes.                                                                             |
| response.cookies                     | Returns a `CookieJar` object with the cookies sent back from the server.                                                   |
| response.history                     | Returns a list of response objects holding the history of request (URL).                                                   |
| response.is_permanent_redirect       | Returns `True` if the response is a permanent redirected URL, otherwise `False`.                                           |
| response.is_redirect                 | Returns `True` if the response was redirected, otherwise `False`.                                                           |
| response.iter_content()              | Iterates over the response.content.                                                                                        |
| response.json()                      | Returns a JSON object of the result (if the result was written in JSON format, otherwise raises an error).                |
| response.url                         | Returns the URL of the response.                                                                                           |
| response.text                        | Returns the content of the response, in Unicode.                                                                           |
| response.status_code                 | Returns a number that indicates the status (200 is OK, 404 is Not Found, etc.).                                            |
| response.request                     | Returns the request object that requested this response.                                                                   |
| response.reason                      | Returns a text corresponding to the status code.                                                                           |
| response.raise_for_status()          | Raises an `HTTPError` object if an error has occurred during the process.                                                  |
| response.ok                          | Returns `True` if status_code is less than 200, otherwise `False`.                                                         |
| response.links                       | Returns the header links.                                                                                                  |


Let’s try making a request for example purposes.

```py
import requests
   
# Making a GET request
r = requests.get('http://httpbin.org/get')
  
# check status code for response received
print(r.status_code) # success code - 200
print(dir(r)) #  you can see the complete list of attributes and methods available on that response object
print(help(r)) # for help
print(r.headers) # We can view the server’s response headers
print(r.text) # # print content of request
print(r.content) #  response body as bytes
print(r.encoding) # encoding property
```

if you want to download content in the browser, just a simple script. 

for example.

```py
import requests 

r = requests.get('https://imgs.xkcd.com/comics/python.png')

with open('comic.png', 'wb') as f:
    f.write(r.content)
```

# Custom Headers

If you’d like to add HTTP headers to a request, simply pass in a dict to the headers parameter.

For example, we didn’t specify our content-type in the previous example :

```py
import json
url = 'https://api.github.com/some/endpoint'
payload = {'some': 'data'}
headers = {'content-type': 'application/json'}

r = requests.post(url, data=json.dumps(payload), headers=headers)
```

# POST requests
Typically, you want to send some form-encoded data — much like an HTML form. To do this, simply pass a dictionary to the data argument. Your dictionary of data will automatically be form-encoded when the request is made :

```py
payload = {'key1': 'value1', 'key2': 'value2'}
r = requests.post("http://httpbin.org/post", data=payload)
print r.text
{
  ...
  "form": {
    "key2": "value2",
    "key1": "value1"
  },
  ...
}
```

There are many times that you want to send data that is not form-encoded. If you pass in a string instead of a dict, that data will be posted directly.

For example, the GitHub API v3 accepts JSON-Encoded POST/PATCH data:

```py
import json
url = 'https://api.github.com/some/endpoint'
payload = {'some': 'data'}

r = requests.post(url, data=json.dumps(payload))
```

# POST a Multipart-Encoded File

Requests makes it simple to upload Multipart-encoded files :

```py
url = 'http://httpbin.org/post'
files = {'file': open('report.xls', 'rb')}

r = requests.post(url, files=files)
r.text
{
  ...
  "files": {
    "file": "<censored...binary...data>"
  },
  ...
}
```

You can set the filename explicitly:

```py
url = 'http://httpbin.org/post'
files = {'file': ('report.xls', open('report.xls', 'rb'))}

r = requests.post(url, files=files)
r.text
{
  ...
  "files": {
    "file": "<censored...binary...data>"
  },
  ...
}
```
If you want, you can send strings to be received as files:

```py
url = 'http://httpbin.org/post'
files = {'file': ('report.csv', 'some,data,to,send\nanother,row,to,send\n')}

r = requests.post(url, files=files)
r.text
{
  ...
  "files": {
    "file": "some,data,to,send\\nanother,row,to,send\\n"
  },
  ...
}
```

# Feature Support

Requests is ready for today’s web.

* International Domains and URLs

* Keep-Alive & Connection Pooling

* Sessions with Cookie Persistence

* Browser-style SSL Verification

* Basic/Digest Authentication

* Elegant Key/Value Cookies

* Automatic Decompression

* Unicode Response Bodies

* Multipart File Uploads

* Connection Timeouts

* .netrc support

* Python 2.6—3.3

* Thread-safe.

# `Thanks for reading`