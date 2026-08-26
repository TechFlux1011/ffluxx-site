# ffluxx.com

Parent-brand portfolio site. Static, single page, no build step.

## Domain structure

| Domain | Purpose |
| --- | --- |
| `ffluxx.com` | Portfolio hub — this repo |
| `soft.ffluxx.com` | ffluxxSoft — apps and tools |
| `studio.ffluxx.com` | ffluxxStudio — video games |

Project pages live as paths beneath each division, e.g. `soft.ffluxx.com/second-home`.
The homepage displays those deep paths as link text but the `href`s currently point
at the division roots, since the deeper pages don't exist yet.

## Files

| File | Notes |
| --- | --- |
| `index.html` | Entire site. Inline CSS + JS. One external call: Google Fonts (Syne, Archivo, JetBrains Mono). |
| `og.png` | 1200×630 social card. Referenced by absolute URL, so it only resolves once live. |
| `favicon.svg` | Primary favicon. What modern browsers actually use. |
| `favicon.ico` | Fallback, 16–256px. |
| `apple-touch-icon.png` | 180×180, iOS home screen. |
| `robots.txt` | Allows all, points at the sitemap. |
| `sitemap.xml` | Lists the apex only. Add subdomains when they resolve. |

## Deployment

Cloudflare Pages, connected to this repo. Push to `main` deploys.

Build settings:

- Build command: *(none)*
- Output directory: `/`

Do **not** enable GitHub Pages on this repo. Cloudflare Pages is the only
deploy target; running both produces two competing sites.

## DNS — read before editing

The domain was bought through iCloud+ Custom Email Domain, so Cloudflare is the
registrar and iCloud handles mail. These records are load-bearing and must not
be deleted:

- `MX @ → mx01.mail.icloud.com` (priority 10)
- `MX @ → mx02.mail.icloud.com` (priority 10)
- `CNAME sig1._domainkey → sig1.dkim.ffluxx.com.at.icloudmailadmin.com`
- `TXT @ → v=spf1 include:icloud.com ~all`
- `TXT @ → apple-domain=…` (several; only one is live and they are not
  distinguishable, so leave all of them)
- Both `NS` records

Cloudflare Pages adds the apex and `www` records itself. It does not touch mail.

Exactly one `_dmarc` TXT record should exist. Two contradictory records cause
receivers to apply no DMARC policy at all.

## Known gaps

- OG card wordmark is set in DejaVu Sans, not Syne. Regenerate when Syne is available.
- Project panels are generated wave fields, not real art. Key art still pending.
- `hello@ffluxx.com` is linked in the footer and must exist in iCloud settings.
