---
layout: default
title: Home
---

# FOSS CTF Bootcamp — Challenges & Writeups

Welcome! This page lists every challenge from the bootcamp, along with a
beginner-friendly writeup for each one. New to CTFs? Start with the
**Beginner** difficulty challenges below.

<div class="challenge-grid">
{% for c in site.challenges %}
  <div class="challenge-card">
    <h3><a href="{{ c.link | relative_url }}">{{ c.title }}</a></h3>
    <p>
      <span class="badge">{{ c.category }}</span>
      <span class="badge badge-diff">{{ c.difficulty }}</span>
    </p>
    <p>{{ c.summary }}</p>
    <a class="btn-link" href="{{ c.link | relative_url }}">View Writeup →</a>
  </div>
{% endfor %}
</div>

---


### How to use this site

Each challenge page includes:
- The **problem statement** — what you're given and what you need to find
- A **step-by-step writeup** — written for beginners, explaining not just
  *what* to click but *why*
- The **flag**, revealed at the end, so you can verify your own solve

Pick a challenge above and get started.


## Resources

<div style="margin: 30px 0;">
  <a class="btn-link" href="{{ '/tools/' | relative_url }}">
    🛠️ Helpful Tools & Platforms →
  </a>
</div>
