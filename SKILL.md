---
name: isolated-soviet-block-collage
description: Transform an uploaded image into a strict layer-isolated collage where the outer area stays 100% identical to the source image and only several irregular inner blocks are replaced with source-color Soviet line-poster redraws of the covered regions. Use when Codex needs to create image-edit prompts or direct image edits for pasted-paper overlays, raised geometric inserts, inner-mask stylization, or any composition where style must stay confined to inner blocks and must never leak into the preserved main image.
---

# Isolated Soviet Block Collage

Produce a composite image with hard layer isolation:

- Preserve the full source image outside the inner blocks.
- Generate new Soviet line-art content only inside the inner blocks.
- Derive block colors from the source image only.
- Keep the output ratio identical to the source image.

Any result that stylizes the full canvas, alters the preserved outer area, or lets poster graphics escape the inner blocks is a failure.

## Default execution mode

When invoked for an image task, use this as the default protocol:

1. Inspect the uploaded source image and any reference images.
2. Produce one concise prompt proposal tied to the source image:
   - source diagnosis
   - extracted colors
   - block layout
   - inner redraw plan
   - final prompt
   - negative prompt
3. Treat that proposal as stage one of the same task, not as the final stopping point.
4. If an image editing or generation tool is available, continue to stage two by generating the edited result with the same prompt constraints in the same turn.
5. Stop after the proposal only when the user explicitly asks to review first, confirm first, or pause before generation.
6. If the first generated result violates isolation, source-color, block-boundary, or aspect-ratio rules, tighten the prompt and regenerate once with stricter wording.

Interpret common user intents this way:

- `Use this skill on my image` -> propose, then generate in the same turn if tooling is available.
- `Give me a prompt first` -> propose first, then wait.
- `Generate directly` or `apply this now` -> skip discussion and generate immediately.
- `Give options` -> provide prompt options and do not generate until the user chooses one.

## Non-negotiable rules

### 1. Preserve the outer area

- Treat every pixel outside the inner blocks as locked source content.
- Do not repaint, recolor, blur, filter, sharpen, crop, or reinterpret the outer area.
- Keep the original subject and background visible around the inner blocks so the collage reads as pasted on top of the source image.

### 2. Restrict stylization to inner blocks

- Place several irregular blocks near the center or slightly off-center.
- Use 2-5 blocks unless the user explicitly asks for denser fragmentation.
- Make the blocks feel pasted above the source image with visible shadow, thickness, or torn-paper edge depth.
- Do not let any linework, text, poster texture, or decorative mark extend beyond block boundaries.

### 3. Use source-derived color only

- Extract 3-5 dominant colors from the uploaded image first.
- Use those colors to drive the block background fills.
- Do not drop in a canned red-blue-yellow Soviet palette unless the source image already supports it.
- Do not add red circles, red circular badges, red round seals, or red disc motifs anywhere in the composition unless the user explicitly overrides this rule.

### 4. Redraw the covered image region

- Each block must contain a Soviet-style line poster redraw of the content that the block covers.
- Do not insert unrelated generic aircraft, symbols, slogans, or landmarks unless the user explicitly asks for them.
- Preserve the local scene logic of the covered area in simplified line form: silhouette, edges, depth cue, and major objects.

### 5. Keep boundaries explicit

- Use clear edges, bevels, torn paper, clipped polygon borders, or thick contour structure.
- Keep the block silhouette irregular rather than perfect rectangles.
- Use shadows or slight extrusion so the blocks visibly sit above the preserved source image.

### 6. Match the source canvas

- Preserve the source aspect ratio exactly.
- Do not add white poster margins, background extensions, or extra framing unless the user explicitly asks for them.

## Workflow

### 1. Inspect the source image

Identify:

- the main subject
- the local scene structure around the intended block area
- 3-5 dominant source colors
- the parts of the image that will remain untouched
- the parts that can be convincingly reinterpreted inside blocks

If the user provided reference images, follow them for block shape, density, and line quality, but not for fixed colors.

### 2. Design the block layout

Choose:

- block count
- approximate placement
- relative sizes
- irregular edge style
- shadow and depth treatment

Prefer layouts similar to pasted paper fragments or segmented globe/map pieces:

- asymmetrical
- separated by narrow gaps
- clustered in the middle field
- large enough to show meaningful redraws

Do not let the block cluster consume so much area that the preserved source image stops reading clearly.

### 3. Plan the inner redraw

For each block:

- note what source region it covers
- identify the dominant object or structure in that covered region
- simplify it into a Soviet line-poster rendering
- keep the redraw tied to the hidden content instead of inventing a new scene

Use:

- hard contour lines
- limited hatching
- poster-flat shadow planes
- geometric simplification
- selective depth cues

Avoid painterly rendering, glossy realism, and full-scene re-composition.

### 4. Construct the prompt

When writing the edit prompt:

- state that the outer area must remain exactly unchanged
- state that only the inner blocks may be regenerated
- repeat that all poster style elements are block-confined
- name the extracted source colors
- explicitly forbid red circles and red circular accents
- describe the block count, placement, and irregularity
- describe the line-poster redraw content inside each block
- require shadow and raised-paper depth
- require the original image ratio

Load [prompt-contract.md](./references/prompt-contract.md) when you need the reusable prompt scaffold, failure checklist, or response format.

### 5. Validate before finishing

Reject the result if any of these are true:

- the outer area no longer matches the source image
- the blocks use colors not supported by the source image
- any red circle or red circular badge appears without explicit user approval
- the block interiors show unrelated content
- linework or text leaks outside block borders
- the block edges are too soft to read as separate layers
- the output ratio changed

If you are editing with an image-generation tool and the first pass fails, regenerate with a stricter prompt that repeats the isolation rules more aggressively and reduces block count if needed.

## Output contract

When using this skill, return:

1. A one-sentence diagnosis of the source image and why it suits this collage mode.
2. The extracted source colors and warm/cool bias.
3. The planned block layout: count, placement, and edge style.
4. The inner redraw plan for each block.
5. One full edit prompt.
6. One negative prompt.
7. A short acceptance checklist.

Keep the response concrete. Do not give generic Soviet poster advice detached from the uploaded image.
