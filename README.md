# nathancastillo.com

Static personal site. One HTML file, no build step, nothing to install.
Domain is registered — everything below is deployment.

## Files

| File | What it does |
|---|---|
| `index.html` | The entire site |
| `og.png` | Social preview card (shows when the link is shared) |
| `favicon.svg` | Browser tab icon |
| `CNAME` | Tells GitHub Pages to serve nathancastillo.com |
| `robots.txt` / `sitemap.xml` | Search engine basics |

All files already reference nathancastillo.com. No edits needed before deploying.

## Step 1 — Host it (free, ~10 min)

1. Create a **public** GitHub repo named exactly `nathancastillo.github.io`
2. Upload every file in this folder to the repo root (drag-and-drop works — "Add file" → "Upload files")
3. Settings → Pages → Source: `main` branch, `/ (root)` → Save
4. Settings → Pages → Custom domain: enter `nathancastillo.com` → Save
5. Leave "Enforce HTTPS" unchecked for now. Check it once DNS resolves (Step 2), usually within an hour.

## Step 2 — Point the domain at GitHub

In your registrar's DNS panel, add these records:

```
Type   Name   Value
A      @      185.199.108.153
A      @      185.199.109.153
A      @      185.199.110.153
A      @      185.199.111.153
CNAME  www    nathancastillo.github.io
```

Delete any parking/placeholder A record the registrar added at signup, or it will conflict.

**If you bought through Cloudflare:** set each record's proxy status to **DNS only** (grey cloud, not orange) until GitHub issues the certificate. Orange-cloud proxying during setup blocks the validation and the site will show a 522.

Propagation takes 10 minutes to a few hours. Check progress at dnschecker.org.

## Step 3 — Verify

- `https://nathancastillo.com` loads with a padlock
- `https://www.nathancastillo.com` redirects to the apex
- Paste the URL into LinkedIn's post composer — the `og.png` card should preview
- Open on your phone; the timeline collapses to a dated list below ~820px

If the social card doesn't appear, run the URL through LinkedIn Post Inspector to clear their cache.

## Step 4 — Email on the domain (optional, free)

`nathan@nathancastillo.com` reads better than Gmail on applications and networking emails.

**Cloudflare Email Routing** — free, forwards to your Gmail. Add the domain to Cloudflare (nameserver change), enable Email Routing, add the destination address. To *send* from it: Gmail → Settings → Accounts → "Add another email address," then authenticate through a free SMTP relay.

**Google Workspace** — ~$7/mo, sending and receiving both work with no setup gymnastics.

## Updating later

Edit `index.html`, commit, push. Live in about a minute.

To add a role to the timeline, copy an existing `.row` block. The `--s` (start) and `--w` (width) percentages map to a 2022–2029 span, so roughly 14.3% per year. Class `law` is amber, `lead` is rose, `edu` is the dashed slate bar.

To change the headline, edit the three `.line` spans in the `<header>` — keep them at three lines so the staggered load animation still reads.
