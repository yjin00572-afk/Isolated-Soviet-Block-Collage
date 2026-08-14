# Prompt Contract

Load this file when writing the actual image-edit prompt or when the user wants a tighter reusable template.

## Mandatory prompt blocks

Every final prompt should explicitly include all of these ideas:

1. `Outer area lock`
   Preserve everything outside the inner blocks exactly as in the uploaded source image. No restyling, repainting, filtering, or content changes outside the blocks.

2. `Inner block isolation`
   Only the irregular inner blocks may contain generated content. All Soviet linework, lettering, texture, and graphic treatment must stay fully inside those block boundaries.

3. `Source-color routing`
   Extract the dominant colors from the uploaded image and use only those source-derived hues for the block background tones.

4. `No red circles`
   Do not introduce any red circles, red circular emblems, red round stickers, red seals, or red disc motifs unless the user explicitly asks for them.

5. `Covered-region redraw`
   Inside each block, redraw the source content that would have existed under that block as a Soviet line-poster illustration.

6. `Raised collage depth`
   Make the blocks feel pasted above the image with shadows, thickness, torn-paper edges, clipped geometry, or bevel-like depth.

7. `Aspect-ratio lock`
   Match the output image ratio to the uploaded source image exactly.

## Full prompt template

```text
Edit the uploaded image into a strict layer-isolated collage. Preserve the entire original image exactly outside a cluster of [count] irregular inner blocks placed [placement]. The outer area must remain 100% unchanged from the source image: no repainting, no restyling, no filtering, no blur, no recolor, no content edits.

Inside the inner blocks only, generate new Soviet-style line poster redraws of the source content covered by each block. The redraws must correspond to the hidden local image regions rather than unrelated symbols or generic poster content. Use source-derived block background colors only: [source colors]. Keep the style graphic, line-based, hand-drawn, and poster-flat, with simplified contours, selective hatching, and restrained shading.

Give each block an irregular shape inspired by pasted paper fragments or segmented geometric pieces, with crisp boundaries, visible shadow, and slight raised depth. Keep all linework, text, and poster texture fully contained inside the blocks. Do not allow any lines, letters, or graphics to spill into the preserved outer photo area.

Do not introduce any red circles, red circular badges, red round emblems, red seals, or red disc-like accents anywhere in the image unless the user explicitly asks for them.

Keep the main subject and background clearly visible outside the blocks so the collage reads as a layered intervention on top of the untouched original image. Match the original image aspect ratio exactly.
```

## Negative prompt template

```text
Avoid full-image stylization, avoid changing the outer area, avoid global repainting, avoid generic Soviet palettes unrelated to the source image, avoid unrelated landmarks or aircraft, avoid poster elements outside the inner blocks, avoid soft blurry block edges, avoid flat sticker-like blocks without shadow, avoid changing the canvas ratio, avoid replacing the original background, avoid text spilling outside the blocks, avoid uniform collage tiles, avoid modern glossy rendering, avoid photobashing inconsistencies, avoid red circles, avoid red circular emblems, avoid red round stickers, avoid red seals, avoid red disc motifs.
```

## Acceptance checklist

Use this checklist before you finalize:

- The preserved outer area still matches the source image.
- The block cluster stays central or near-central.
- The block colors are visibly source-derived.
- No red circle or red circular emblem appears unless explicitly requested.
- Each block redraw relates to the covered source region.
- The block edges are crisp and dimensional.
- No poster line escapes into the preserved area.
- The output ratio matches the source ratio.

## Response template

```text
Source diagnosis:
[one sentence]

Extracted colors:
- [color 1]
- [color 2]
- [color 3]

Block layout:
- [count and placement]
- [edge and shadow treatment]

Inner redraw plan:
- Block 1: [covered region -> Soviet line redraw]
- Block 2: [covered region -> Soviet line redraw]

Full prompt:
[prompt]

Negative prompt:
[negative prompt]

Acceptance checklist:
- outer area unchanged
- style confined to blocks
- source colors only
- block redraw matches covered region
- source ratio preserved
```
