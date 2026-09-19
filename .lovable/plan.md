# Correct scene scale, rerolls, and SFX

## Changes
- Make scale explicit in every generated scene: schools, halls, cities, ships, crowds, mountains, and other large subjects must occupy the frame at monumental real-world scale, with people and nearby objects used as clear size references. Preserve genuinely small objects when the script says they are small.
- Remove prompt language that currently freezes locations at an accidentally small first interpretation. Keep architecture and identity consistent while allowing Fix Scene to correct scale.
- Strengthen the single-image rule so every result is one full-bleed 16:9 scene, never a contact sheet, storyboard grid, split view, inset, interface mockup, or image containing stray labels.
- Narrow visible SFX to explicit combat impacts, weapon clashes, explosions, destructive power releases, and clearly described attack impacts. Running, jumping, flying, magic objects, glowing auras, crowds, scenery, and ordinary movement remain wordless.
- Make Fix Scene regenerate a deliberately corrective prompt that prioritizes the exact timestamp, intended scale, and one-scene composition. Make Reroll retain scene facts but add a fresh anti-collage composition instruction and use a genuinely independent seed.

## Technical details
- Update prompt writing, location locks, scale classification, action/SFX classification, and final image prompt composition in `src/lib/manga.server.ts`.
- Separate broad dynamic-action detection from strict combat-SFX eligibility instead of using one permissive regex for both.
- Update the single-panel redraw flow in `src/routes/index.tsx` so Fix Scene and Reroll send distinct correction intent while retaining character and location continuity.
- Preserve 1344×768 output, professional webtoon/manhwa direction, character continuity, and the ban on dialogue, captions, bubbles, and unrelated text.
