# Sprite export check

A small, experimental preflight for **Aseprite PNG + JSON exports**. Check frame bounds, filenames, durations, trim geometry and animation tag ranges before investigating an import problem.

**[Open the demo](https://jsirocco.github.io/sprite-export-check/)**

Files are read locally in your browser. No account, uploads, analytics, runtime AI service or paid API. The checker does not modify your originals.

## Try it

1. Open the demo and compare **Broken example** with **Healthy example**. Both use original synthetic PNG/JSON files through the same decoding pipeline as selected files.
2. Choose your exported JSON and, optionally, its PNG; press **Check my export**.
3. Select a frame to inspect its rectangle. **View report** exposes copyable JSON and a download link.

## Supported checks

- JSON-array and JSON-hash exports, unrotated frames.
- Frame coordinates within the supplied PNG or declared size.
- Duplicate array filenames and case-only filename collisions.
- Positive frame durations, trim geometry, animation tag index ranges.
- PNG dimensions versus JSON metadata, and declared versus selected image filename.

Limits: JSON 5 MB; PNG 20 MB, 16 megapixels and 8,192 px per side; 20,000 frames. Preview buttons show the first 40 frames and outlines show up to 1,000; supported validation covers all frames. The visible list caps at 200 findings; the report includes all findings.

## Scope and limitations

This is a **structural prototype**, not an engine compatibility certificate. Rotated frames and nonempty slice metadata are marked unchecked. Duplicate keys inside JSON objects, animation direction semantics, overlapping rectangles, image bleed and actual engine rendering are not validated. Shared image regions are not automatically an error.

The logic passed 23 assertion-based tests with synthetic fixtures. Browser checks covered both synthetic examples and the visible report. No real customer exports or Aseprite/Phaser/Godot engine imports have been tested. Native file-picker automation and saved Blob downloads were not verified; the report can be selected and copied without a download.

## Feedback

Use a GitHub issue to describe a reproducible export problem and what the checker missed. **Do not attach confidential or third-party assets without permission.** A synthetic minimal example and the relevant metadata are enough to discuss most structural issues.

Format references: [Aseprite CLI](https://www.aseprite.org/docs/cli/), [sprite sheet documentation](https://www.aseprite.org/docs/sprite-sheet/).
