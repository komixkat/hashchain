# Hash_Chain

Live at **[komixkat.github.io/hashchain](https://komixkat.github.io/hashchain/)**

---

## What it does

You pick a secret passphrase. It generates "X" unique tokens tied to that passphrase and time of generation. Drop one token at the bottom of each post. Anyone can verify two consecutive tokens actually chain together with a single SHA-512 call. Nobody can fake the next token without knowing your passphrase.

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

Download `index.html` and open it in any browser. No Oneko tho...

---

## How the 'magic' works

Your salted passphrase is run through SHA-512 "X" times before anything else happens, which makes brute-forcing it slow. Then the site builds a chain by hashing forward. You post in reverse order, so each new token you reveal is the preimage of the previous one.

Verification is just `sha512 (newer token) == older token`, simple and efficient.

---

## Files  

```
index.html                    the thing that does stuff
.github/workflows/deploy.yml  auto-deploy to GitHub Pages
oneko.js & oneko.gif          cat chase mouse 
```

Special thanks to [@ari](https://github.com/adryd325/oneko.js) for oneko

---

## License
MIT license. Do whatever you want with it.
