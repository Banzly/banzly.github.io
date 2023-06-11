---
title: PYTHON REQUEST
date: 2023-06-11 00:29:40 +/-TTTT
categories: [learning, web]
tags: [ctf]     # TAG names should always be lowercase
---

# What's Python’s Requests Library ?

`Python's Requests library is a` popular and powerful tool for making HTTP requests in Python. It simplifies the process of interacting with `web services and APIs` by providing a user-friendly API.

With the Requests library, you can easily send `GET, POST, PUT, DELETE, and other types of HTTP requests`. It handles tasks such as setting headers, managing cookies, handling redirects, and working with response data.

The library is widely used for tasks like web scraping, accessing RESTful APIs, and building web applications. It offers a straightforward and intuitive syntax, making it easy to understand and use.

One of the main advantages of Requests is its extensive documentation and active community support. You can find a wealth of resources, tutorials, and examples online to help you learn and use the library effectively.

In summary, Python's Requests library is a valuable tool for performing HTTP requests in Python. It simplifies the process, provides a user-friendly API, and is widely adopted in the Python community.

`Why learn Python requests module?`

`The Python Requests` module is worth learning due to its numerous advantages and functionalities. Firstly, it provides a simplified and user-friendly interface for making HTTP requests compared to the built-in libraries. This means you can easily perform common HTTP operations like `GET, POST, PUT, and DELETE` with just a few lines of code.

The module offers flexibility and extensibility, allowing you to handle various aspects of HTTP requests and responses. It supports `authentication methods, cookies, sessions, SSL verification, and more`. Additionally, Requests has extensive documentation and a large community, making it easy to find resources and examples online.

Learning the Requests module is particularly useful when working with `web APIs`. It simplifies the process of interacting with APIs, making it easier to retrieve data and integrate it into your applications. Many web services provide documentation and examples using the Requests library, further facilitating the learning process.

Moreover, Requests is cross-platform compatible, allowing you to write code that works seamlessly on different operating systems. Its Pythonic and elegant design follows the principles of readability and simplicity, making it a joy to work with.

Overall, mastering the Python Requests module empowers you to handle `HTTP requests effectively`, interact with web services, and build robust applications. Its simplicity, versatility, and extensive community support make it a valuable tool for any Python developer.

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

When sending a POST request with form-encoded data, it is often important to specify the content-type header to indicate that the data is in the `application/x-www-form-urlencoded` format.

Here's an updated example code snippet that demonstrates how to include the content-type header in a POST request with form-encoded data :

```py
import requests

url = 'http://example.com/post'  # Specify the URL where you want to send the POST request

form_data = {
    'key1': 'value1',
    'key2': 'value2',
    'key3': 'value3'
}

headers = {
    'Content-Type': 'application/x-www-form-urlencoded',  # Specify the content-type header
    'Custom-Header': 'value'  # Include any other custom headers if needed
}

response = requests.post(url, data=form_data, headers=headers)

if response.status_code == 200:
    print('POST request successful.')
else:
    print('Error occurred while sending the POST request.')

```

# POST requests

When making a POST request with form-encoded data, you typically send the data in the body of the request using the "application/x-www-form-urlencoded" content type. The data is represented as key-value pairs, similar to how form data is sent in HTML forms.

Here's an explanation of the process and an example code snippet using the Requests library in Python:

For example:

```py
import requests

url = 'http://example.com/post'  # Specify the URL where you want to send the POST request

form_data = {
    'key1': 'value1',
    'key2': 'value2',
    'key3': 'value3'
}

response = requests.post(url, data=form_data)

if response.status_code == 200:
    print('POST request successful.')
else:
    print('Error occurred while sending the POST request.')
```

In some cases, you may need to send data in a format other than form-encoded, such as JSON. If you pass a string instead of a dictionary as the data parameter, the data will be posted directly without form encoding.

For example, the GitHub accepts JSON-Encoded POST/PATCH data :

```py
import requests
import json

data = {
    "name": "BanZ",
    "email": "BanZ@example.com",
    "message": "Hello, GitHub!"
}

# Convert the data to JSON string
json_data = json.dumps(data)

# Set the headers to specify the content type as JSON
headers = {'Content-Type': 'application/json'}

# Send the POST request with the JSON-encoded data
response = requests.post("https://api.github.com/endpoint", data=json_data, headers=headers)
print(response.text)
```

# POST a Multipart-Encoded File

To upload a Multipart-encoded file using the Requests library in Python, you can follow :

```py
import requests

file_path = 'path_to_your_file'  # Specify the path to your file
file_name = 'file_name.ext'  # Specify the desired name for the file on the server
url = 'http://example.com/upload'  # Specify the URL where you want to upload the file

with open(file_path, 'rb') as file:
    files = {'file': (file_name, file)}
    response = requests.post(url, files=files)

if response.status_code == 200:
    print('File uploaded successfully.')
else:
    print('Error occurred while uploading the file.')
```

