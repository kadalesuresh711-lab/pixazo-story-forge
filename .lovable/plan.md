# Automatic single-frame and multi-frame layouts

## Changes
- Keep one generated 16:9 image for every timestamp, but let that image contain either one cinematic frame or a deliberately designed multi-frame webtoon layout.
- Choose the layout automatically from the timestamp duration and story density:
  - up to 7 seconds: one full-bleed frame;
  - 8–14 seconds: two coordinated frames when the beat contains a clear progression, otherwise one frame;
  - 15 seconds or longer: two or three coordinated frames showing successive moments from that same timestamp.
- Keep all frames inside one 1344×768 image and preserve one location, cast, clothing, lighting, and story moment across the layout.
- Keep dialogue, captions, narration boxes, signs, and speech bubbles absent. Combat-only SFX remains the sole allowed lettering.
- Multi-frame pages will use clean professional webtoon gutters, varied cinematic framing, and readable chronological flow rather than accidental contact sheets or repeated copies.
- Fix Scene and Reroll will retain the automatically selected layout instead of always forcing a single frame.

## Technical details
- Pass and parse each timestamp range during final prompt composition so duration is available to the renderer.
- Add deterministic layout selection using duration plus narrative progression cues in the script line and written prompt.
- Replace the unconditional single-frame guard with a duration-aware single-frame or multi-frame composition guard.
- Bump saved prompt semantics so old single-frame prompts and images do not silently return for the same script.
- Preserve existing 16:9 output, 1344×768 dimensions, character/location continuity, scale direction, action choreography, and strict combat-only SFX detection.
