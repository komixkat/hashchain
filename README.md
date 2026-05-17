# Hash Chain

**Prove you're the same anonymous person across posts, without revealing who you are.**

A single-file web app that generates a cryptographic hash chain. Drop a token into each post. Anyone can verify two consecutive tokens chain together. Nobody can forge the next one without your passphrase.

---

## How it works

1. **Enter a secret passphrase** — generates 100 unique tokens via SHA-256 chaining with 2000-round key stretching
2. **Post your anchor** — a public hash that establishes your identity in a first post
3. **Add a token to each post** — paste `sig: <token>` at the bottom
4. **Readers verify** — `hash(newer token) == older token` proves same author

The chain is one-way: seeing token #42 gives you nothing about token #41. Only the person who knows the passphrase can produce the correct next value.

---

## Deploy your own copy

### Option 1 — GitHub Pages (recommended)

1. Fork or clone this repo
2. Go to **Settings → Pages**
3. Under *Source*, select **GitHub Actions**
4. Push to `main` — the workflow deploys automatically

Your site will be live at `https://<your-username>.github.io/<repo-name>`

### Option 2 — Run locally

No build step needed. Just open `index.html` in a browser:

```bash
git clone https://github.com/your-username/hashchain.git
cd hashchain
open index.html        # macOS
xdg-open index.html   # Linux
start index.html       # Windows
```

### Option 3 — Any static host

Upload `index.html` to Netlify, Vercel, Cloudflare Pages, or any web server. It's a single self-contained file with no dependencies beyond Google Fonts.

---

## Security notes

- **Nothing leaves your browser.** The passphrase and chain live only in memory.
- **Key stretching.** Your passphrase is hashed 2000 times before chain generation, making brute-force attacks slow.
- **Deterministic.** Same passphrase → same 100 tokens, every time. Re-enter it after closing the tab to resume where you left off.
- **No storage.** Closing the tab loses your position in the chain (not the chain itself — just which token you're on). Keep a note of your current token number if needed.
- **Not a login system.** This proves consistency of authorship, not real-world identity. Don't use the same passphrase for anything else.

---

## Files

```
hashchain/
├── index.html               # The entire app (single file)
├── .github/
│   └── workflows/
│       └── deploy.yml       # GitHub Actions → GitHub Pages
└── README.md
```

---

## License

MIT — do whatever you want with it.
