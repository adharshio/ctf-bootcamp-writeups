---
layout: challenge
title: "Wiki Backup Leak"
category: "Network Forensics"
difficulty: "Beginner"
permalink: /challenges/wiki-backup-leak/
---

## The Challenge

**Files:** [`traffic.pcap`]({{ '/assets/files/traffic.pcap' | relative_url }})

We're given a single file — a recording of network traffic. Our job is to
open it, read through the traffic, and find a hidden flag in the format
`foss{...}`.

The tool we'll use is **[Wireshark](https://www.wireshark.org/)**, the
standard tool for reading and analyzing packet captures. If you don't have
it installed yet, grab it from the link above — it's free for Windows,
macOS, and Linux.

## What a Flag Actually Is

A "flag" is a specific string of text that proves you solved the challenge.
It's wrapped in a recognizable format — here, `foss{...}` — so that when you
find it, you know for certain you've found *the* answer. You submit the
exact string, braces included, to score the challenge.

## Opening the File

Open Wireshark, then **File → Open**, and select the pcap. You'll land on
the main view, split into three panes:

| Pane | What it shows |
|---|---|
| **Packet list** (top) | One row per packet — time, source, destination, protocol, description |
| **Packet details** (middle) | The selected packet's layers, expandable — Ethernet, IP, TCP, and whatever's on top |
| **Hex/ASCII dump** (bottom) | The raw bytes of the selected packet |

## Step 1 — Survey Before You Search

Go to **Statistics → Protocol Hierarchy**. You should see a mix: ARP, DNS,
ICMP, TCP, HTTP, and FTP.

Most of these carry data in **plain text** — anyone capturing the traffic
can read it directly. HTTP and FTP are the protocols most likely to carry
readable, interesting content, so that's where we focus.

## Step 2 — Filter Down to What Matters

Type into the filter bar:

```
http
```

You should see two `GET` requests: one for `/index.html`, one for
`/uploads/notes_backup.txt`. The second one is unusual — a backup file
shouldn't normally be reachable over plain HTTP. That's our lead.

## Step 3 — Follow the Full Conversation

Right-click the `notes_backup.txt` request → **Follow → HTTP Stream**. This
reassembles both directions of the conversation into readable text.

Read the **request headers and the response body** carefully. You'll find:

- In the request: `X-Debug-Token: Zm9zc3twNGNrM3RfNW4=`
- In the response body: `chunk2=MWZmMW42XzE1X2Z1bn0=`

<div class="hint-box">
<strong>Hint:</strong> both strings end in <code>=</code> and use only
letters and digits — that's a strong sign of Base64 encoding.
</div>

## Step 4 — Decode and Combine

```bash
echo "Zm9zc3twNGNrM3RfNW4=" | base64 -d
# -> foss{p4ck3t_5n1

echo "MWZmMW42XzE1X2Z1bn0=" | base64 -d
# -> 1ff1n6_15_fun}
```

No terminal handy? Use **[CyberChef](https://gchq.github.io/CyberChef/)** —
drag in "From Base64", paste the string, read the output.

Concatenate both halves in order:

```
foss{p4ck3t_5n1  +  1ff1n6_15_fun}
```

## The Flag

<div class="flag-box">foss{p4ck3t_5n1ff1n6_15_fun}</div>

## What This Teaches

- **Cleartext protocols leak everything.** HTTP and FTP send headers,
  filenames, and sometimes credentials in plain, readable text — this is
  exactly why HTTPS exists.
- **Data isn't always in the obvious place.** Check headers *and* bodies,
  requests *and* responses.
- **Not everything in a capture matters.** The `index.html` request and the
  FTP login were decoys.
- **Recognizing encodings on sight is a skill** that transfers to almost
  every forensics challenge.

## The Method, Summarized

> **Survey → Filter → Follow → Decode**

1. Survey the capture (Statistics → Protocol Hierarchy)
2. Filter to the protocol most likely to carry readable data
3. Follow the full stream of anything that looks out of place
4. Decode anything unusual, and check if there's more than one piece
