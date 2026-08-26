# ffluxx divisions

Two static sites, one repo. No build step.

| Folder | Domain | Cloudflare Pages project |
| --- | --- | --- |
| `soft/` | soft.ffluxx.com | ffluxx-soft |
| `studio/` | studio.ffluxx.com | ffluxx-studio |
| `brand/` | *not deployed* | source assets only |

`ffluxx.com` lives in its own repo and is not affected by anything here.

## Pages settings

Each project must point at its own folder. If **Root directory** is left at `/`,
both projects serve whichever `index.html` sits at the repo root.

- **Root directory:** `soft` (or `studio`)
- **Build command:** *(none — use `exit 0` if a value is required)*
- **Output directory:** `/`
- **Build watch paths → Include:** `soft/*` (or `studio/*`)

## The header wordmark

The lockup is two sibling anchors, not one. `ffluxx` goes to the company site;
`Soft` / `Studio` goes to that division's root. They are set flush against each
other with no whitespace between the tags — adding a newline there inserts a
space and breaks the word in half visually. Hovering either half tracks its
letters out and reveals the destination beside the lockup.

## Open items

- Neither signup form has an endpoint. Set `ENDPOINT` near the bottom of each
  `index.html`. While it is empty the form tells visitors nothing was saved.
- Devlog and build-note entries are placeholder text.
- Key art and app screens are generated wave fields, not real artwork.
- `brand/ffluxx-og-syne.png` replaces the parent repo's `og.png`, with the
  wordmark set in Syne instead of DejaVu.
