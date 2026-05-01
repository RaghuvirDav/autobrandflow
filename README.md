# AutoBrandFlow public explainer site

Static single-page site for [RAPA-19](/RAPA/issues/RAPA-19). Tells a stranger
what AutoBrandFlow does in 30 seconds and points them at the apply form.

- **Repo:** <https://github.com/RaghuvirDav/autobrandflow.git>
- **Hosting:** GitHub Pages, source `main` + `/docs/`
- **Domain:** `autobrandflow.com` (apex, board-purchased)

## Layout

```
.
├── README.md            # this file (repo-root README)
├── .gitignore           # ignores .queue/
├── docs/                # GitHub Pages source path
│   ├── index.html       # the entire site, embedded CSS, no JS
│   └── assets/          # CTO headshot drops here once board uploads
└── .queue/              # heartbeat artifacts, gitignored
```

## Placeholders to fill before launch

| Token / asset | Source | Status |
|---|---|---|
| `{{CTO_NAME}}` (×2) | Board confirms via [`ask_user_questions` interaction 43b180ff](/RAPA/issues/RAPA-19) | Pending |
| `docs/assets/cto-headshot.jpg` | Board uploads square ≥400×400 JPG/PNG | Pending |
| `{{TALLY_APPLY_URL}}` (×2) | [RAPA-21](/RAPA/issues/RAPA-21) ships the apply-form URL | Pending |
| `{{HELLO_EMAIL_ADDRESS}}` | Board confirms (default suggestion: `hello@autobrandflow.com`) | Pending |

The 90-second demo section is **removed** from source per RAPA-19 hard gate #1
(no "coming soon" placeholder allowed). An HTML comment marks the slot. Re-add
only when [RAPA-16](/RAPA/issues/RAPA-16) lands a real URL.

## Deploy

```bash
# one-time, from this directory
git init -b main
git remote add origin https://github.com/RaghuvirDav/autobrandflow.git

# after placeholders are filled and headshot is dropped at docs/assets/cto-headshot.jpg
git add README.md .gitignore docs/
git commit -m "v1 AutoBrandFlow explainer site"
git push -u origin main
```

After the first push, the board enables Pages on `main` + `/docs/` and points
`autobrandflow.com` DNS at GitHub Pages. CTO posts the live URL back on
[RAPA-19](/RAPA/issues/RAPA-19).

## Local preview

```bash
python3 -m http.server 8000 --directory docs
# open http://localhost:8000
```

## Performance budget

Single static HTML, ~10.5 KB raw / ~3 KB gzipped, embedded CSS, zero JS, zero
web fonts. First paint should be well under 2 s on mobile per the RAPA-19
acceptance bar.
