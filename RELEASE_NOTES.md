# v1.0.1 — three fixes

### بوكيمون نسخة البلور بالعربية

A point release on top of v1.0. Same translation, three bugs out.

## What changed

**The town banner redrew the ground underneath it.** Clearest when you come out
of Slowpoke Well into Azalea Town. Loading a tall glyph into VRAM means waiting
for the PPU to let go of it, with interrupts held off for the duration, and a
place name is ten to sixteen glyphs back to back. Entered late enough in a
frame, one of those waits swallowed the vblank interrupt — and the handler,
running after vblank had already ended, copied a third of the background map
into VRAM that the hardware had locked again. A glyph now waits out the end of
the frame before it starts. Visible only on an emulator that models the VRAM
lock, which is why it showed in BGB and not in mGBA.

**The rival came out nameless.** The routine that names him had lost the line
telling `InitName` which string to fill, so skipping past the naming screen
left the name blank and his battle text printed an empty line where it should
have read سيلفر. Note that his name lives in your save file and the game asks
for it exactly once, in Elm's Lab: a file that already went through that scene
on v1.0 keeps the blank. If that is yours, [open an issue][issues] — it is a
fixed field in the save and can be put right without starting over.

**The battle menu's cursor pointed away from the word it was selecting.**
معركة / حقيبة / فريق / هروب is laid out unlike any other menu in the game, and
the arrow's direction was being decided from the wrong edge of the box.

## Download

**`pokecrystal-arabic.bps`** — apply it to your own copy of the game.

| | |
|---|---|
| Base ROM | Pokémon Crystal (UE) **v1.0** |
| Base SHA-1 | `f4cd194bdee0d04ca4eac29e09b8e4e9d818c133` |
| Patched SHA-1 | `a6bd086c89361224a9dd45e0fa2a13510f11e148` |
| Patch SHA-1 | `15a61a6d6cc493db0c27cacdf5ba7baec58c34d8` |
| Patch size | 412,648 bytes |

No ROM is distributed here. BPS checksums the base, so the wrong revision —
v1.1, the Australian release, a debug build — is refused with an error rather
than producing a broken game.

Apply with [Flips][flips], or in your browser with [RomPatcher.js][rompatcher].

**Game Boy Color only.** The tall font needs CGB's second VRAM bank, so DMG
hardware and DMG-mode emulators will not render the Arabic.

## Everything else

Unchanged from [v1.0][v1]. Saves made on v1.0 carry over; nothing in the save
format moved.

Found something? [Open an issue][issues] — a screenshot and roughly where you
were is plenty.

[flips]: https://github.com/Alcaro/Flips
[rompatcher]: https://www.marcrobledo.com/RomPatcher.js/
[issues]: https://github.com/SherlockedMain/Pokemon_Crystal_Arabic/issues
[v1]: https://github.com/SherlockedMain/Pokemon_Crystal_Arabic/releases/tag/v1.0
