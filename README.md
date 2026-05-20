# Hash Chain

Prove you're the same anonymous person across posts without revealing who you are.

Live at **[komixkat.github.io/hashchain](https://komixkat.github.io/hashchain/)** — no install needed, just open it.

---

## What it does

You pick a secret passphrase. It generates 100 unique tokens tied to that passphrase. Drop one token at the bottom of each post. Anyone can verify two consecutive tokens actually chain together with a single SHA-256 call. Nobody can fake the next token without knowing your passphrase.

The chain is one-way. Seeing token #42 tells you nothing about token #41. The passphrase never leaves your browser.

---

## Use your own copy

**Fork on GitHub**

1. Fork this repo
2. Go to Settings > Pages
3. Set Source to GitHub Actions
4. Push to main and it deploys automatically

Your copy will be live at `https://your-username.github.io/hashchain`

**Or just open the file**

Download `index.html` and open it in any browser. No server needed, no build step, nothing to install.

---

## How the crypto works

Your passphrase is run through SHA-256 two thousand times before anything else happens, which makes brute-forcing it slow. Then the app builds a chain by hashing forward 100 times. You post in reverse order, so each new token you reveal is the preimage of the previous one.

Verification is just `sha256(newer token) == older token`. One call, no special tools.

---

## Files

```
index.html          the whole app
.github/workflows/  auto-deploy to GitHub Pages
```

---

MIT license. Do whatever you want with it.
