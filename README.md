# FOSS CTF Bootcamp — Challenges & Writeups Site

A GitHub Pages site listing CTF challenges with beginner-friendly writeups,
built with Jekyll and the **Cayman** theme.

## Structure

```
.
├── _config.yml              # Site config + list of challenges shown on home page
├── _layouts/
│   └── challenge.html       # Shared layout for every challenge page
├── assets/
│   ├── css/style.scss       # Cayman theme + custom card/badge/flag styling
│   └── files/               # Downloadable challenge files (pcaps, etc.)
├── challenges/
│   ├── wiki-backup-leak.md  # Challenge 1 (fully written)
│   ├── challenge-2.md       # Challenge 2 (placeholder — fill in)
│   └── challenge-3.md       # Challenge 3 (placeholder — fill in)
└── index.md                 # Home page — auto-lists every challenge as a card
```

## Adding a new challenge

1. Create `challenges/your-challenge-slug.md`.
2. Add front matter at the top:
   ```yaml
   ---
   layout: challenge
   title: "Your Challenge Title"
   category: "Category"
   difficulty: "Beginner"
   permalink: /challenges/your-challenge-slug/
   ---
   ```
3. Write the writeup in Markdown below the front matter.
4. Add an entry to the `challenges:` list in `_config.yml` so it shows up
   as a card on the home page:
   ```yaml
   - title: "Your Challenge Title"
     category: "Category"
     difficulty: "Beginner"
     summary: "One-line description."
     link: /challenges/your-challenge-slug/
   ```
5. Drop any downloadable file (pcap, zip, etc.) into `assets/files/` and
   link it from the challenge page:
   ```markdown
   [Download the pcap]({{ '/assets/files/yourfile.pcap' | relative_url }})
   ```

## Publishing on GitHub Pages

1. Create a new GitHub repository (e.g. `ctf-bootcamp-writeups`).
2. Push this folder's contents to the repo's default branch (`main`).
3. On GitHub: **Settings → Pages** → under "Build and deployment", set
   **Source** to "Deploy from a branch", branch `main`, folder `/ (root)`.
4. Save. GitHub will build the site automatically (takes 1–2 minutes) and
   give you a URL like `https://<username>.github.io/ctf-bootcamp-writeups/`.
5. Any time you push new commits, the site rebuilds automatically — no
   manual deploy step needed.

No local Ruby/Jekyll install is required — GitHub Pages builds the site for
you using its supported themes (Cayman is one of the built-in options).

## Previewing locally (optional)

If you want to preview before pushing:

```bash
gem install bundler jekyll
bundle init
echo 'gem "github-pages", group: :jekyll_plugins' >> Gemfile
bundle install
bundle exec jekyll serve
```

Then open `http://localhost:4000`.
