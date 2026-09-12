# Flashcards (Dropbox version)

This is the exact `index.html` currently live at `nngupta1.github.io/flashcards` —
fully static, no backend, Dropbox Chooser SDK loaded client-side. Moving it to
Cloudflare Pages is just a deploy, no code changes.

## Deploy

From this folder:
```bash
npx wrangler login          # skip if already logged in from the CRM project
npx wrangler pages project create flashcards
npx wrangler pages deploy public
```

## Custom domain
Cloudflare dashboard → Workers & Pages → `flashcards` project → **Custom domains**
→ add `flashcards.cricketmade.com`.

## Important: update the Dropbox App Console
The Dropbox Chooser SDK checks a domain whitelist before it'll open the picker.
Go to the [Dropbox App Console](https://www.dropbox.com/developers/apps) → your
app (key `qrd2zyn6n4hxt6g`) → **Chooser / Saver / Embedder domains** → add:
- `flashcards.cricketmade.com`
- the `*.pages.dev` URL wrangler gives you, if you want to keep testing there too

Without this step the picker will silently fail to open on the new domain —
this is the one gotcha likely to bite you here, everything else should just work.

## Note
The old GitHub Pages version can stay live or be taken down — your call, they're
now fully independent copies of the same file.
