# v1.0 — Pokémon Crystal in Arabic

### بوكيمون نسخة البلور بالعربية

The full game, in Arabic, right to left, with the letters joined.

Dialogue, menus, battle text, item and move names, Pokédex entries, the
trainer card and stats screens, phone calls, the naming screen, the Battle
Tower — all of it, including the 210 Battle Tower nicknames that the
disassembly still ships as romanised Japanese.

Underneath is a text engine written for this hack: the original game draws one
8×8 tile per character, left to right, which Arabic cannot use. This one is
right to left, shapes each letter from its neighbours, and blits glyphs into
VRAM a letter at a time from a ring borrowed out of the walking-sprite pool.

## Download

**`pokecrystal-arabic.bps`** — apply it to your own copy of the game.

| | |
|---|---|
| Base ROM | Pokémon Crystal (UE) **v1.0** |
| Base SHA-1 | `f4cd194bdee0d04ca4eac29e09b8e4e9d818c133` |
| Patched SHA-1 | `43e49a71959e6f3cc62b4a2dac73b9365bb6b358` |
| Patch SHA-1 | `78b356c74e93d3e7b082dee2fc3b736757c67c2c` |
| Patch size | 412,641 bytes |

No ROM is distributed here. BPS checksums the base, so the wrong revision —
v1.1, the Australian release, a debug build — is refused with an error rather
than producing a broken game.

Apply with [Flips][flips], or in your browser with [RomPatcher.js][rompatcher].

**Game Boy Color only.** The tall font needs CGB's second VRAM bank, so DMG
hardware and DMG-mode emulators will not render the Arabic.

## Fixed on the way to 1.0

- A wild Pokémon fleeing ran the text engine off the end of its command table
- Both HUDs kept the party menu's palettes after switching Pokémon in battle
- Menus and the battle move list flashed into 8×8 letters for a frame as they closed
- The status box drew a scrap of the player's sprite beside سم
- The egg summary screen drew the egg twice, with its hatching text on the wrong side
- Menu cursors pointed away from the item they were selecting on left-to-right lists
- Kurt's quantity box blinked once per frame; the mart's ¥ multiplied as the subtotal shrank
- 199 message boxes had lost their second row, costing a button press each
- ~90 lines overran the textbox once a Pokémon or route name was substituted in

## Known

Tested on mGBA and BGB.

Every line in the game was measured against the 18-cell textbox with the
longest name that can be substituted into it. Nothing overruns with a
full-length Pokémon name (10 cells), which is what the great majority of those
inserts hold. A handful of buffers can instead hold an item name (12 cells) or
a route name (16), and those were not audited one by one — so if you ever see a
line run past the edge, it will be one of those, and it is worth reporting.

Found something? [Open an issue][issues] — a screenshot and roughly where you
were is plenty.

[flips]: https://github.com/Alcaro/Flips
[rompatcher]: https://www.marcrobledo.com/RomPatcher.js/
[issues]: https://github.com/SherlockedMain/Pokemon_Crystal_Arabic/issues
