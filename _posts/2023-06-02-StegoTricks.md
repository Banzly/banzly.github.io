---
title: STEGOTRICKS
date: 2023-06-02 20:56:40 +/-TTTT
categories: [ctf, STEGOTRICKS]
tags: [ctf]     # TAG names should always be lowercase
---

automate workflows powered by the world's most advanced community tools.

# General 
Usually when organizer gave us Image, Music, Video, Zip, EXE, File System, PDF and other files, it a steganography or forensics challenge. `Run` file command first.

# Foremost

`Foremost` is a program that recovers files based on their headers, footers, and internal data structures. I find it especially useful when dealing with png images. You can select the files that Foremost will extract by changing the config file in /etc/foremost.conf.
It can be installed with `apt`, and the source can be found on Github.
```
foremost -i file : extracts data from the given file.
```

# Pngcheck
Get details on a PNG file (or even find out it's actually something else!).

`apt-get install pngcheck` : Install the tool.

`pngcheck stego.png` : Obtain info about the PNG

# Exiftool

Sometimes, important stuff is hidden in the metadata of an image or file; exiftool can be very helpful to view file metadata.
You can get it from `exiftool.org`
```
exiftool <fileName> : shows the metadata of the given file
```

# Strings

Extract strings from the file.

commands :

* `strings -n 6 <file>` : Extract the strings with min length of 6

* `strings -n 6 <file> | head -n 20` : Extract first 20 strings with min length of 6

* `strings -n 6 <file> | tail -n 20` : Extract last 20 strings with min length of 6

* `strings -e s -n 6 <file>` : Extract 7bit strings

* `strings -e S -n 6 <file>` : Extract 8bit strings

* `strings -e l -n 6 <file>` : Extract 16bit strings (little-endian)

* `strings -e b -n 6 <file>` : Extract 16bit strings (big-endian)

* `strings -e L -n 6 <file>` : Extract 32bit strings (little-endian)

* `strings -e B -n 6 <file>` : Extract 32bit strings (big-endian)

# Extracting data from images

-> `Binwalk`

`Binwalk` is a tool for searching binary files, like images and audio files, for embedded hidden files and data.

It can be installed with `apt`, and the source can be found on Github.

Useful commands :

* `binwalk file` : Displays the embedded data in the given file

* `binwalk -eM file` : Displays and extracts the data from the given file

* `binwalk --dd ".*" file` : Displays and extracts the data from the given file


-> `Identify` GraphicMagick tool to check what kind of image a file is. Also checks if the image is corrupted.
```
./magick identify -verbose stego.jpg
```

If the image is damaged, you may be able to restore it by simply adding a metadata comment to it (if it's very badly damaged this won't work) :
```
./magick mogrify -set comment 'Extraneous bytes removed' stego.jpg
```

# Steghide [JPEG, BMP, WAV, AU]

`Steghide` is a steganography program that hides data in various kinds of image and audio files. It supports the following file formats : JPEG, BMP, WAV and AU. It’s also useful for extracting embedded and encrypted data from other files.
It can be installed with apt, and the source can be found on Github.

Useful commands :

* `steghide info file` : displays info about whether a file has embedded data or not.

* `steghide extract -sf file [--passphrase password]` : extracts embedded data from a file `[using a password]`

You can also extract content from steghide using the web

# Zsteg [PNG, BMP]

`zsteg` is a tool that can detect hidden data in png and bmp files.
To install it `gem install zsteg`. The source can also be found on Github.

Useful commands :

* `zsteg -a file` : Runs every detection method on the given file.
* `zsteg -E file` : Extracts data with the given payload (example : zsteg -E b4,bgr,msb,xy name.png)

# stegoVeritas JPG, PNG, GIF, TIFF, BMP

Capable of a wide variety of simple and advanced tricks, this tool can check file metadata, create transformed images, brute force LSB, and more. Check out `stegoveritas.py -h` to read about its full capabilities. 
Execute `stegoveritas.py stego.jpg` to run all checks.

# Stegpy [PNG, BMP, GIF, WebP, WAV]

A program for encoding information in image and audio files through steganography. It can store the data as either plaintext or encrypted Find it on Github.

# Extracting data from audios

-> `ffmpeg`

can be used to check the integrity of audio files, reporting various information about the file, as well as any errors it finds.
```
ffmpeg -v info -i stego.mp3 -f null -
```

-> `Wavsteg [WAV]`

WavSteg is a Python3 tool that can hide data, using least significant bit, in wav files. It can also search for, and extract, data from wav files You can get it from Github.

Useful commands:

`python3 WavSteg.py -r -b 1 -s soundfile -o outputfile` : Extracts to an output file (taking only 1 lsb)

`python3 WavSteg.py -r -b 2 -s soundfile -o outputfile` : Extracts to an output file (taking only 2 lsb)


# Music file

Use `binwalk first`. They may embedded something in the file.

Use `Audacity`.

Use `Sonic Visualizer`. Look at spectogram and other few Pane.

Use `Deepsound`.

Use `SilentEye`.

Some of online stegano decoder for music :

* https://steganosaur.us/dissertation/tools/audio

Scripting may then be required to extract specific areas. The following python code retrieves an image as a list of pixels

```python
# pip install Pillow
from PIL import Image
stegano_image = Image.open("file.png")
width, height = stegano_image.size
pxs = list(stegano_image.getdata())
print(pxs[:10])
```

Scripting If you have ever studied machine learning about image processing, you will definitely recognize arrays that start with the value 255.

```python
from numpy import genfromtxt
my_data = genfromtxt('namfile.csv', delimiter=',')
from PIL import Image
image = Image.fromarray(my_data)
if image.mode != 'RGB':
    image = image.convert('RGB')
    image.save('data.jpg')
```

# Some of online stegano decoder : ".*"

* https://futureboy.us/stegano/decinput.html
* http://stylesuxx.github.io/steganography/
* https://www.mobilefish.com/services/steganography/steganography.php
* https://manytools.org/hacker-tools/steganography-encode-text-into-image/
* https://steganosaur.us/dissertation/tools/image
* https://georgeom.net/StegOnline
* http://magiceye.ecksdee.co.uk/


# DISCLAIMER
```
This cheatsheet is intended to guide CTF players in their research. This cheatsheet is not representative of modern steganography/seganalysis techniques, and its content does match with the creation of an interesting challenges 😉.
```