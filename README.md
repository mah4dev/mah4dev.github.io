# trishul.re

An interactive terminal-style personal site. Boots like a program, drops you at
a working shell, and lets you explore the filesystem to find out who I am.

**Live → [trishul.re](https://trishul.re)**

```
  ┌──(trishul@mahadev)-[~]
  └─$ whoami
```

## What it is

A single-page site that behaves like a terminal. On load it runs a short boot
sequence and prints an ASCII wordmark, then hands over a real prompt. Visitors
can type commands — or tap the command chips — to move through a virtual
filesystem and `cat` the contents.

Built handwritten in vanilla HTML/CSS/JS. No framework, no build step, no
dependencies — it's one file that a browser just runs.

## Features

- Skippable boot sequence (respects `prefers-reduced-motion`)
- Working shell: `ls`, `cd`, `cat`, `tree`, `pwd`, `clear`, `whoami`, and more
- `whoami` prints a neofetch-style card with an ASCII trident
- Command history (`↑`/`↓`) and Tab autocompletion
- Clickable command chips for discoverability and mobile
- Toggleable CRT / scanline effect
- Responsive, and crawlable by search engines via a plain-text fallback

## Stack

- Plain HTML, CSS, and JavaScript — zero dependencies
- [JetBrains Mono](https://www.jetbrains.com/lp/mono/) for the type
- Palette: `#0d0d0d` background · `#9e1d1d` blood red accent · grey foreground
- Hosted on GitHub Pages, fronted by Cloudflare

## Structure

```
.
├── index.html        the whole site — markup, styles, and the terminal engine
├── CNAME             custom domain (trishul.re)
└── assets/           optional: extracted stylesheet, images, etc.
```

## Editing the content

The site's "filesystem" is a JavaScript object named `FS` inside `index.html`.
Each entry is either a directory or a file with its text content. To add or
change what a visitor sees, edit that object — e.g. add a file under
`projects/` or update `about.txt`. Commands, chips, and the boot sequence are
defined in the same script, near the top.

## Run locally

If everything lives in a single `index.html`, opening the file directly works.
Once assets are referenced by absolute path (e.g. `/assets/style.css`), serve
it over HTTP instead:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Deploy

Served from GitHub Pages with a custom domain:

1. `CNAME` contains `trishul.re`.
2. GitHub Pages → custom domain set to `trishul.re`, Enforce HTTPS on.
3. Cloudflare DNS holds the four GitHub Pages `A` records for the apex, proxied,
   with SSL/TLS set to Full (strict).

## Related

- [writeups.trishul.re](https://writeups.trishul.re) — CTF writeups and lab notes

---

<sub>har har mahadev.</sub>
