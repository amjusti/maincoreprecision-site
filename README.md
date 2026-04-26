# Maincore Precision LLC — Website

Static site for [maincoreprecision.com](https://maincoreprecision.com).  
Pure HTML/CSS/JS — no build tools, no frameworks.

---

## Local preview

Open `index.html` directly in your browser, or use any static server:

```bash
# Python (built-in)
python3 -m http.server 8080
# then open http://localhost:8080

# Node (npx, no install needed)
npx serve .
```

---

## Before going live

1. **favicon.ico** — The SVG favicon (`favicon.svg`) works in all modern browsers. For older browser fallback, generate a `favicon.ico`:
   ```bash
   # Option A — npx (no install)
   npx png-to-ico favicon-32.png --output favicon.ico

   # Option B — upload favicon.svg to https://favicon.io and download the .ico
   ```
   Place `favicon.ico` in the project root and push.

2. **Formspree** — Create a free account at [formspree.io](https://formspree.io), create a form, and replace `REPLACE_WITH_YOUR_FORMSPREE_ID` in `index.html` with your real form ID (the 8-character code in the endpoint URL).

3. **GitHub Pages** — Enable Pages in repo Settings → Pages → Source: **GitHub Actions**. The workflow in `.github/workflows/deploy.yml` runs on every push to `main`.

4. **Custom domain DNS** — In Cloudflare (or your DNS provider), add:

   | Type  | Name | Value             |
   |-------|------|-------------------|
   | A     | @    | 185.199.108.153   |
   | A     | @    | 185.199.109.153   |
   | A     | @    | 185.199.110.153   |
   | A     | @    | 185.199.111.153   |
   | CNAME | www  | amjusti.github.io |

5. **Custom domain in GitHub** — Repo Settings → Pages → Custom domain → enter `maincoreprecision.com` → Save. Check "Enforce HTTPS" once DNS propagates (usually < 1 hour).

---

## Deploy

```bash
git add -A
git commit -m "initial site"
git push origin main
```

The GitHub Actions workflow deploys automatically. Check the **Actions** tab for status.

---

## File structure

```
/
├── index.html                  # Entire site (CSS + JS inline)
├── favicon.svg                 # SVG favicon (all modern browsers)
├── favicon.ico                 # .ico fallback (generate manually — see above)
├── CNAME                       # Custom domain for GitHub Pages
├── sitemap.xml
├── robots.txt
├── .github/
│   └── workflows/
│       └── deploy.yml          # GitHub Pages deploy workflow
└── README.md
```
