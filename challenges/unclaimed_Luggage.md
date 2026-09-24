---
layout: challenge
title: "Unclaimed Luggage"
category: "Forensics & OSINT"
difficulty: "Easy (Beginner)"
permalink: /challenges/unclaimed-luggage/
---

## The Challenge

A suspicious black suitcase was spotted abandoned near a tea shop. Naturally, instead of opening it like normal people, our intel team took a picture of it and ran away.

Word on the street is that a frantic operative scrambled a secret location payload into the image's hidden details before losing his mind somewhere in the hills of Ooty.


## Step-by-step Writeup

1.Extract EXIF Metadata:
Use terminal tools or CyberChef to inspect the image tags.
The first step in any image-based forensics challenge is checking for hidden data attached to the file. 
Run exiftool against the provided image in your terminal:

```
exiftool suitcase.png
```

Scanning through the output, two specific tags stand out as highly unusual for a standard photograph:
```
Comment: Kilukkam Kilukilukkam (2006)
Description: 01:53:07
```
We now have our OSINT targets: a specific Malayalam movie and an exact timestamp.

2.Open-Source Video Search:

Search the public internet for the source media.Switching into OSINT mode, open YouTube or Google Video.Search for "Kilukkam Kilukilukkam 2006 full movie". 

Because this is a well-known public release, you will easily find several full-length uploads of the film available to stream for free.

3.Analyze the Cinematic Moment:Navigate to the extracted metadata timestamp.

Scrub through the video timeline to exactly 01:53:07.

Watch the scene unfold at this precise moment. 

Jagathy Sreekumar delivers a very specific, memorable line of dialogue in English:"Welcome to Ooty, nice to meet you."


4.Format and Submit the Flag:

Convert the dialogue into the required CTF format.

CTF flags usually require spaces to be replaced by underscores (_) and everything to be in lowercase, wrapped inside the competition format.Translate the spoken dialogue into the flag structure


## The Flag

<div class="flag-box">foss{welcome_to_ooty_nice_to_meet_you}</div>

## What This Teaches

Forensics seamlessly blends into OSINT.

    1.Challenges don't always stay in one lane. 

    This challenge starts purely technical (extracting EXIF metadata from a file) but pivots entirely into open-source intelligence (using public video platforms to hunt down real-world media references).

    2.Always check the metadata first.
	
	Before running complex steganography tools to see if a secret file is embedded inside an image's pixels, always check the EXIF data. Authors love hiding hints, passwords, or entire flags in the Comment, Description, or Copyright tags.

    3.Follow the breadcrumbs.

    A random timestamp (01:53:07) means nothing on its own, but paired with a movie title, it acts as exact GPS coordinates for a video file. OSINT is about taking isolated pieces of public data and connecting them to find the hidden meaning.