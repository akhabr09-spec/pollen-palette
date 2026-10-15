# Pollen Palette

Turn a short text prompt into an image with [Pollinations](https://pollinations.ai). A single-file browser app — you connect your own Pollinations account, so generation is paid with **your own Pollen**.

[![Made with pollinations.ai](https://raw.githubusercontent.com/pollinations/pollinations/main/packages/ui/src/brand/badge-made-with.svg)](https://pollinations.ai/?ref=badge)

## What it does

- Describe a scene (or pick one of the built-in prompt ideas) and get an image back.
- Choose an image model and output size (square / 16:9 / portrait).
- Connect your Pollinations account with **Connect User Wallets** (BYOP) and spend your own balance — no shared key, no server.

## How it works

1. The app is served as static `index.html` (hosted on GitHub Pages).
2. Clicking **Connect Pollinations** sends you through the Pollinations BYOP authorization flow using the app's publishable `pk_` App Key as `client_id`.
3. After you approve, Pollinations returns a short-lived, user-authorized `sk_` key in the URL fragment (`#api_key=...`). The app keeps it in the tab session only.
4. Generation calls go to `https://gen.pollinations.ai/image/{prompt}` with that key as a Bearer token.

Nothing is sent anywhere except Pollinations. The key is never stored on a server.

## Run locally

```bash
# any static server works
python -m http.server 8080
# then open http://localhost:8080/
```

## Stack

Vanilla HTML/CSS/JS, no build step, no dependencies.

Made with ❤️ and the [Pollinations API](https://gen.pollinations.ai/docs).
