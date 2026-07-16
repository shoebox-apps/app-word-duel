# Word Duel — manual two-phone test

A laptop browser counts as the second device.

## The loop

1. **Device A (Player 1):** open the app with no hash. Type a secret word
   (e.g. `CRANE`) and tap **Create challenge link**. Tap **Copy** — confirm the
   button flashes "Copied!".
2. **Send the link** to yourself via any messenger (or just paste it into the
   second device's browser bar).
3. **Device B (Player 2):** open the challenge link. Confirm:
   - The play board appears — the secret word is NOT visible anywhere on screen.
   - On-screen keyboard and (on laptop) physical keys both enter letters.
   - A short guess shakes the row; a full 5-letter guess colors green/yellow/gray.
   - Duplicate letters color correctly (secret `ALLAY`, guess `LLAMA` →
     yellow, green, yellow, gray, yellow).
   - Mid-game: close the tab / kill the app, reopen the SAME link — guesses are
     restored from localStorage.
4. **Finish the game** (win or run out of 6 guesses). Confirm the result panel
   shows win/loss, reveals the word on loss, and offers a **result link** with a
   working Copy button.
5. **Send the result link back** to Device A. Open it there. Confirm Player 1
   sees the full colored board replay, the outcome headline, and their word.
6. **Rematch:** tap the rematch button on either device — it returns to setup
   with a clean slate so a new word/link can be created. Repeat step 1 with
   roles swapped.

## Edge checks

- Open the app with a mangled hash (e.g. `#c=garbage`) → "That link didn't
  decode" screen, with a working **Start a new duel** button.
- Narrow the browser to **380px** width → no horizontal scroll, board and
  keyboard fully usable.
- Airplane mode on both devices → everything above still works (no fetches).
