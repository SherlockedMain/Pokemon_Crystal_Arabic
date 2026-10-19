# v1.0.2 — a crash fix and three text fixes

### بوكيمون نسخة البلور بالعربية

A point release on top of v1.0.1. Same translation, one crash and three broken
texts fixed.

## What changed

**The game could reset itself and land on "this game is designed for the Game
Boy Color".** A tester hit it after the third badge, mid-walk, from Fisher
Ralph's phone call ("I've been spending more time with my Pokémon…"). Nothing
was wrong with the hardware, the emulator or the save.

The cause was in the text, not the engine. A line that prints a name — a
Pokémon's, a move's, a trainer's — is followed by more text, and the game must
be told that more text is coming. In 24 places the Arabic scripts skipped that
byte. The engine read the next character as an instruction it does not have,
jumped into memory that holds no code, and the console restarted into its
boot-up check — which, with the wrong value in a register, concludes it is not
running on a Game Boy Color. It shows up only when the call, battle message or
dialogue is actually reached, which is why it took hours of play to hit.

Affected: phone calls from Alan, Anthony, Beth, Bill, Derek, Jack, Jose, Ralph,
Tiffany, Todd and Tully; four battle messages ("move disabled", "was disabled",
and the two "won't rise / drop any more" lines); a trade partner's farewell; the
two Battle Tower rule lines about different species and held items; and a few
NPCs in Blue's House, the Goldenrod Game Corner and Pokémon Center, the Battle
Tower and the Trainer House. All 24 are fixed, and the source now has a checker
that fails if the same mistake comes back.

**Mom's daylight-saving question came out mirrored and half-height.** Answer
"No" to "is this about your money?" and she asks whether to put your clock on
daylight saving time. That question was drawn by a routine that skips the
right-to-left setup, so it showed as small mirrored fragments until you
answered. It now prints like every other dialogue.

**Battle Tower trainers' greetings, win and loss lines** went through the same
routine and were mirrored the same way. Fixed.

**The names of two pairs of twins were too long for the dialogue box.** In a
battle, a twin pair is announced as their class and then both names — التوأمتان
هدى وندى — and every battle line that starts with the trainer ("wants to
battle", "sent out", "withdrew", "was defeated" and the rest) puts that on a
single line. تالة وهالة was one letter too wide: the last letter fell off the
left edge of the box and a stray fragment of it showed in the top corner. جاد
وزينة fitted the box exactly, with no room left for the "!" that ends the
"you lost against…" and "tied against…" lines — and جاد is a boy's name for two
girls. The two pairs are now:

| Where | Before | Now |
|---|---|---|
| The Spinarak and Ledyba twins | تالة وهالة | **هدى وندى** |
| The Victreebel and Vileplume twins | جاد وزينة | **جنى وسنا** |

Both are eight tiles, so they fit with room to spare. The other three pairs —
آية ومي, مهى ومنى and ليا وريا — already fitted and are unchanged. Only the
names changed: a pair you have already beaten stays beaten, and their teams are
the same.

## Cheats

GameShark codes written for the original game point at the wrong memory in
this version, because the Arabic build added variables and moved the game's data
(money, for instance, lives at `D85D` instead of `D84E`). A code made for the
original can write over something else. Codes need converting to this
version's addresses before they are used; do not paste original ones in as
they are.

## Download

**`Pokemon_Crystal_Arabic_OS.bps`** — apply it to your own copy of the game.

| | |
|---|---|
| Base ROM | Pokémon Crystal (UE) **v1.0** |
| Base SHA-1 | `f4cd194bdee0d04ca4eac29e09b8e4e9d818c133` |
| Patched SHA-1 | `7abd57e60d20f71f243dc42afbe785c2b6e23168` |
| Patch SHA-1 | `74260f1e7ade62835dbf8ccef27b3314ecf7e612` |
| Patch size | 413,630 bytes |

No ROM is distributed here. BPS checksums the base, so the wrong revision —
v1.1, the Australian release, a debug build — is refused with an error rather
than producing a broken game.

Apply with [Flips][flips], or in your browser with [RomPatcher.js][rompatcher].

**Game Boy Color only.** The tall font needs CGB's second VRAM bank, so DMG
hardware and DMG-mode emulators will not render the Arabic.

## Upgrading

Patch your clean base ROM again and keep playing: **saves from v1.0 and v1.0.1
carry over**, nothing in the save format moved. Put the new ROM next to your
existing `.sav` with the same file name. Emulator *save states* belong to the
ROM they were made on — load from an in-game save once, then make new states.

## Everything else

Unchanged from [v1.0.1][v101].

Found something? [Open an issue][issues] — a screenshot and roughly where you
were is plenty.

[flips]: https://github.com/Alcaro/Flips
[rompatcher]: https://www.marcrobledo.com/RomPatcher.js/
[issues]: https://github.com/SherlockedMain/Pokemon_Crystal_Arabic/issues
[v101]: https://github.com/SherlockedMain/Pokemon_Crystal_Arabic/releases/tag/v1.0.1
