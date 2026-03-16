# 866alffind.com — Landing Page

Static lead-generation landing page for the **866-ALF-FIND** phone number brand (866-253-3463). Part of the Senior Placement Helpline LLC national marketing campaign, operated by [Higher Vision Health](https://highervisiohealth.com).

## What it is

- Single-page static site (`index.html`) — no build step, no dependencies
- Deep teal + orange design language; mobile-first, fully responsive
- Lead capture form that POSTs to `https://highervisiohealth.com/leads`
- All CSS self-contained in a `<style>` block; one external font (Google Fonts Inter)
- Google Maps embed showing nationwide service area

## Deploy to Cloudflare Pages

### Option A — GitHub integration (recommended)

1. Push this repo to GitHub (or it's already there).
2. In [Cloudflare Pages](https://pages.cloudflare.com/), click **Create a project → Connect to Git**.
3. Select the `866alffind` repository.
4. Set **Framework preset** to `None`.
5. Leave **Build command** and **Output directory** blank — Cloudflare will serve `index.html` directly.
6. Click **Save and Deploy**.
7. Under **Custom domains**, add `866alffind.com` and `www.866alffind.com`.

### Option B — Direct upload (Wrangler CLI)

```bash
npx wrangler pages deploy . --project-name 866alffind
```

### Custom Domain DNS

After connecting the domain in Cloudflare Pages, Cloudflare will prompt you to add CNAME records. Point:

| Type  | Name | Target                          |
|-------|------|---------------------------------|
| CNAME | @    | `<project>.pages.dev`           |
| CNAME | www  | `<project>.pages.dev`           |

Ensure the domain is on Cloudflare DNS (orange-cloud proxy enabled) for HTTPS to work automatically.

## Updating the lead endpoint

The form POSTs JSON to `https://highervisiohealth.com/leads`. To change the endpoint, find this line in `index.html`:

```js
fetch('https://highervisiohealth.com/leads', {
```

And replace the URL with your actual endpoint.

