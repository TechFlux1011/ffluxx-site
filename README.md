# ffluxx divisions

Two static sites, one repo. No build step.

| Folder | Domain | Cloudflare Pages project |
| --- | --- | --- |
| `soft/` | soft.ffluxx.com | ffluxx-soft |
| `studio/` | studio.ffluxx.com | ffluxx-studio |
| `brand/` | *not deployed* | source assets only |

`ffluxx.com` lives in its own repo and is not affected by anything here.

## Pages settings — the part that matters

Each project must point at its own folder. If **Root directory** is left at `/`,
both projects serve whichever `index.html` sits at the repo root, and one
division's site appears on both subdomains.

For each project, in Settings → Builds & deployments:

- **Root directory:** `soft` (or `studio`)
- **Build command:** *(none — use `exit 0` if a value is required)*
- **Output directory:** `/`
- **Build watch paths → Include:** `soft/*` (or `studio/*`)

Without the watch paths every push rebuilds both sites. Harmless, just noisy.

## File naming

Every file inside `soft/` and `studio/` is named generically on purpose —
`index.html`, `favicon.svg`, `og.png`. The folder provides the namespace.
Do not rename them to `soft-favicon.svg` and place them at the root; the
`<head>` references root-relative paths like `/favicon.svg`, which resolve
against the deployed root, i.e. the folder.

## Open items

- Neither signup form has an endpoint. Set `ENDPOINT` near the bottom of each
  `index.html`. While it is empty the form tells visitors nothing was saved.
- Devlog and build-note entries are placeholder text.
- Key art and app screens are generated wave fields, not real artwork.
- `brand/ffluxx-og-syne.png` is a replacement for the parent repo's `og.png`,
  with the wordmark set in Syne instead of DejaVu. Copy it there when convenient.
