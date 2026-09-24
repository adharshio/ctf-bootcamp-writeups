---
layout: challenge
title: " Picture Perfect Secret"
category: "Cryptography"
difficulty: "Beginner"
permalink: /challenges/picture-perfect-secret/
---

## The Challenge

We intercepted a scrambled transmission and an image file (challenge.png) from an unencrypted channel.
Decode the message, and retrieve the flag!

Ciphertext:

c2drdXRhM3l1MGUzX3YwX2owNTVfYTU1dTN9

Flag Format: foss{...}

## Step-by-step Writeup

1.Inspect EXIF Metadata:Extract the hidden payload from the image tags.Run exiftool on the provided JPEG image or load it into CyberChef using the Extract EXIF recipe:
```
exiftool nss_logo.jpg
```
Look for the Image Description or Description metadata attribute:

```
Image Description : Encrypted Payload: c2drdXthM3l1MGUzXzcwX2gwNTVfcjU1fQ==
```

2.Decode the Base64 Layer:Recognize the '==' padding signature and convert to raw text.

The double equal signs (==) at the end of c2drdXthM3l1MGUzXzcwX2gwNTVfcjU1fQ== indicate 2-byte Base64 padding. 

Decode it in terminal or via CyberChef's From Base64 recipe:

```
echo "c2drdXthM3l1MGUzXzcwX2gwNTVfcjU1fQ==" | base64 -d
```
Decoded String: sgku{a3yu0e3_70_h055_r55}


3.
Decrypt the Vigenère Cipher:Apply the key 'nssce' to reveal the leet-speak flag.

Pass sgku{a3yu0e3_70_h055_r55} into CyberChef using the Vigenère Decode recipe with key nssce:


Alphabetic Shifts: Standard letter positions are shifted backward according to key nssce.


Non-Alphabetic Characters: Digits (3, 0, 7, 5), underscores (_), and curly braces ({, }) remain unchanged and do not consume key letters.


To learn more about vignere cipher:https://www.geeksforgeeks.org/dsa/vigenere-cipher/

Decrypted Result: foss{w3lc0m3_70_f055_n55}


## The Flag

<div class="flag-box">foss{w3lc0m3_70_f055_n55}</div>

## What This Teaches

1.Images Contain Hidden Data Beyond Pixels
Metadata (EXIF tags) can store plain text, GPS coordinates, timestamps, or custom payloads without changing the visual appearance of the image.

2.Encoding and  Encryption are different . 

Base64 is encoding: It transforms binary or text into ASCII representation so computers can safely transmit it. 
There is no secret key, and anyone can instantly reverse it.Vigenère is encryption: It requires a secret keyword (nssce) to mathematically scramble the underlying letters.

3.Identifying Base64 Signatures 

Base64 strings consist of alphanumeric characters (A-Z, a-z, 0-9), +, /, and frequently end in = or == padding depending on payload length.
Handling Non-Alpha Symbols in Classical CiphersWhen solving classical ciphers containing leet-speak (w3lc0m3), numbers and special characters (_, {, }) are ignored by the cipher wheel—only alphabetic characters undergo letter shifts.