# Make action panels visibly dynamic

## Changes
- Detect combat, attacks, chases, falls, transformations, powers, and other fast physical beats from both the script line and generated scene prompt.
- Add a short mandatory action-direction block near the beginning of action prompts so it cannot be lost when long prompts are shortened.
- Require a decisive mid-action pose, readable movement direction, strong foreshortening or dynamic angle, and multiple wordless effects tied to the motion and impact.
- Keep quieter scenes free from unnecessary action effects, while preserving 16:9 output, character/location continuity, and the no-text rules.

## Technical details
- Update only the image prompt composition in `src/lib/manga.server.ts`.
- Reserve the action-effects instruction outside the trimmable scene text so Pixazo always receives it for detected action scenes.
