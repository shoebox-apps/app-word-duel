# Word Duel

An async two-player Wordle-style duel with **zero backend** and **zero notifications**.
All game state travels inside links; players check on open.

## How it works

1. **Player 1** picks a secret 5-letter word. The app builds a **challenge link** with the
   word encoded in the URL fragment (base64url — obfuscation, not cryptography). Send it
   over any messenger.
2. **Player 2** opens the link and plays Wordle-style: 6 guesses, standard
   green / yellow / gray coloring with correct duplicate-letter handling. Any 5-letter
   A–Z string is a legal guess — there's no dictionary, it's a duel, your opponent is
   the dictionary.
3. On win or loss the app builds a **result link** (secret + full guess history) for
   Player 2 to send back. Player 1 opens it and sees the whole board replayed.
4. **Rematch** button flips the table — pick a new word, send a new link, the loop continues.

No servers, no accounts, no fetches, no push. The URL fragment never even leaves the
device except inside the message you choose to send. In-progress games survive
app restarts via `localStorage`.

## Link scheme

```
#c=<b64url({v:1, m:"c", w:"CRANE"})>              challenge
#r=<b64url({v:1, m:"r", w:"CRANE", g:[...]})>     result
```

The word is trivially recoverable by decoding the link. That's fine — it's a party
game on the honor system.

## Files

- `index.html` — the entire app, inline CSS + JS
- `manifest.json` — Shoebox bundle manifest
- `TESTING.md` — the manual two-phone test loop

## License

MIT.

## Add to Shoebox
Have the [Shoebox host](https://github.com/shoebox-apps/shoebox) installed? Scan this with your **phone's camera or Google Lens** — Shoebox opens with this app pre-filled, ready to add. No typing, no app store. (Your phone's camera does the scanning; Shoebox never asks for a camera permission.)

![Add to Shoebox](add-qr.png)

Or paste the base URL into Shoebox's **+ → Add**: `https://rubberduckinspace.github.io/app-word-duel/`

Fork it. Change one thing. Push. Watch your phone.
