# Trolley Mirror

Trolley Mirror is a blind framing experiment that compares a player's trolley-problem decisions with **Jev**, Pollinations' typed decision-intelligence model. Six decisions contain three hidden pairs: the facts stay the same while their order and emphasis change. The final mirror reveals whether the player, Jev, or both changed their answer.

![Trolley Mirror interface](./screenshot.png)

## Live app

**[Open Trolley Mirror](https://trolley-mirror.jm716111.chatgpt.site/)**

Built for [Pollinations Quest #17647](https://github.com/pollinations/pollinations/issues/17647).

## How it uses Pollinations

- Uses `typesafe/jev-1.13` through the Pollinations typed decision endpoint.
- Reads all three Jev primitives: `choice`, `noul`, and `score`.
- Uses Pollinations OAuth PKCE so every visitor signs in and pays with their own Pollen.
- Requests only the Jev model, a maximum budget of 1 Pollen, and a 7-day expiry.
- Keeps the temporary access token in `sessionStorage`; no secret key is shipped with the app.
- Includes clearly labelled demo readings so the experiment can be explored before connecting.

## Run locally

No build step or dependencies are required. Serve the repository root with any static server, for example:

```bash
python -m http.server 4173
```

Then open `http://127.0.0.1:4173/`.

The production OAuth app only accepts the deployed callback URL. To test OAuth from another origin, create your own Pollinations app key and register that origin as a redirect URL.

## Privacy

Trolley Mirror does not use analytics or a backend. OAuth state and the temporary Pollinations token stay in the current browser tab. Closing the tab clears the session token.

---

[![Made with pollinations.ai](https://raw.githubusercontent.com/pollinations/pollinations/main/packages/ui/src/brand/badge-made-with.svg)](https://pollinations.ai/?ref=badge)

