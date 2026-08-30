# How it works: staying compatible with Visual Improvement

Visual Improvement V1.2.7 and this translation both touch a large, overlapping
region of the ROM (roughly `0x0000BE`–`0x7FFFFF`), because game text and
graphics data are interleaved there. Diffing the two patches directly against
each other shows 68,990 overlapping bytes, of which 32,542 are hard conflicts:
both patches write different values to the same offset. There is no
application order that avoids this. Stacking the two patches independently
corrupts the ROM.

## The approach

Instead of patching the clean ROM and hoping the two hacks coexist, the
Italian patch is generated as a diff against a ROM that already has Visual
Improvement applied:

```text
clean USA ROM -> [Visual Improvement variant] -> base -> [Italian text] -> output
                                                         |
                                          Italian patch = diff(base, output)
```

This makes compatibility a property of how the patch is built, not something
verified after the fact. Because there are four Visual Improvement variants
(stock whip/menu, C-Whip, RMenu, C-Whip RMenu), there are four matching
Italian patches. Applying the wrong one to the wrong base still fails, but
predictably: the resulting ROM hash won't match `release.json`.

The Localization Fix variants of Visual Improvement are intentionally not
supported. That patch corrects English item text (e.g. `Skeleton Blaze` →
`Skeleton Blades`), which the Italian translation replaces entirely. Keeping
it as a base would only add conflict surface with no effect on the final
text.

## Font

Two glyphs used by Italian accents, `ì` and `ò`, did not exist in the base
font and were added to unused glyph slots. Their pixel data is a first pass
and may look rough in some contexts; a redraw is planned for the next
release. The other accented letters (`à`, `è`, `é`, `ù`) reuse glyphs already
validated by prior fan translations of this game into other Latin-alphabet
languages, so their pixel data was already known good.

## Verification

- Byte-exact round-trip: `apply(base, patch) == output` for all four variants.
- Text codec round-trip: every string encodes and decodes back to itself,
  including all six Italian accented letters.
- Control-code parity: every in-game formatting/control code in the English
  source is preserved unchanged in the Italian text.
- Byte budget: every translated string fits in the space reserved for the
  original, in place, so no pointer relocation was needed.
- Runtime checks on real hardware/emulator covered menus, inventory, item
  descriptions, story dialogue rendering (including the three ending
  branches), and loading an existing save.

A full continuous playthrough has not been completed, so this first release
is still considered experimental.
