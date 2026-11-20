---
name: character-reveal-trailer
description: Create high-energy 15-second, 12-cut, 60fps 2.5D character reveal trailers from any character image, avatar, turnaround sheet, or text concept, supporting 16:9 landscape, 9:16 vertical, and 1:1 square formats across multiple visual styles (streetwear, cyber, Guofeng, minimal studio). Guides an AI coding agent to create an interactive HTML preview and, when requested, an MP4. Use when the user asks to make a character reveal trailer, turn a character or turnaround sheet into a cool promo video, build a fast-cut motion graphics animation, or export a stylized character MP4.
---
# character-reveal-trailer

Turn any character image, avatar, turnaround sheet, or character concept into a 15-second, 12-cut, 60fps 2.5D motion-graphics reveal trailer. The defaults below are a starting point; honor the requested length, format, visual direction, deliverables, and available tools. This is a workflow, not a bundled renderer. Check asset generation, browser, font, and encoding tools before promising output; explain any missing capability and offer a workable alternative.

## When to Use

- The user uploads a character turnaround sheet, single illustration, or avatar and asks for a cool reveal trailer or promo video.
- The user wants a fast-cut motion-graphics video (kinetic typography, split-screens, strobe afterimages, impact frames, studio climax) tailored to their brand, handle, or domain.
- The user asks for landscape (16:9 for X, YouTube, Bilibili), vertical (9:16 for Douyin, TikTok, Reels, Shorts), or square (1:1) character promo videos exported as MP4.

## Steps

### 1. Scope Inputs, Format, and Style

Confirm or infer four key dimensions before generating assets:

- **Input asset type:**
  - *3-view turnaround sheet:* Slice `front`, `side`, and `back` cleanly from the uploaded sheet.
  - *Single character image or portrait:* Keep the original as `front` (or generate a matched full-body `front` if only a headshot), and if image generation is available, generate matched `side` and `back` views referencing the upload; otherwise use the supplied views and disclose the limitation. Generated unseen views are interpretations, not verified design references.
  - *Complex or dark background:* Instead of fragile color thresholding, generate clean `#FFFFFF`-background reference-locked poses so cutouts stay crisp without halos.
  - *No image provided:* Generate a reference character sheet first if an image-generation tool is available (or use a procedural 3D geometric mascot only if the user explicitly wants a zero-asset robotic/abstract look).
- **Aspect ratio and layout:** Default to `16:9` (`1920x1080`). For `9:16` (`1080x1920`) vertical video, reflow layouts automatically: stack the Cut 04 tri-view as 3 horizontal strips (top/middle/bottom) instead of narrow columns, and place Cut 01 and Cut 12 brand text above/below the character instead of left/right.
- **Visual and audio theme:** Match the palette, graphic motifs, and synthesized music to the character's style (extracting default accent colors from the character's outfit):
  - *Streetwear / Cyber / Tech:* High-contrast dark/light + cobalt/amber/ice accents, halftone dots, barcodes, HUD reticles, 132 BPM Future-Bass + synth arpeggio.
  - *Guofeng / Oriental Fantasy:* Ink-black, vermilion, gold-leaf, jade accents, seal stamps, ink-brush energy arcs, pentatonic pluck + deep drum impacts.
  - *Minimal Studio / Pastel:* Clean cyclorama backdrop, soft shadows, glass cards, crisp pop-electronic groove.
- **Branding:** Collect custom brand title, domain/handle, edition number, and kinetic buzzwords (supporting both English and CJK text).

### 2. Build the 9-Pose Transparent Sprite Kit

For a reference-led illustrated character, prefer preserving the supplied likeness over substituting basic 3D geometric primitives; likeness drops drastically compared to reference-locked 2D sprites composited in a 2.5D stage.

- Extract base turnaround views (`front`, `side`, `back`) using edge flood-fill background removal, enclosed inner-pocket cleanup, and 1px anti-aliased fringe feathering.
- Generate matching dynamic action poses referencing the user's original image on a pure flat `#FFFFFF` background with no cast shadow or text:
  - `cool` (signature stance, e.g. adjusting eyewear or hero pose)
  - `run` (full-stride high-speed sprint)
  - `slide` (low-angle braking skid)
  - `jump` (mid-air parkour vault)
  - `kick` (foreshortened flying kick or signature attack)
  - `land` (three-point superhero crouch landing)
- Normalize all 9 transparent cutouts to ~560px height and encode them as WebP (`quality=88`) when inlining into HTML to keep the single-file app fast and compact (under ~700 KB).

### 3. Build the Interactive Single-File HTML Preview

Create a self-contained HTML player first so the user can preview, scrub, and iterate on copy or colorways before spending time on MP4 encoding.

- Drive every animation from a deterministic pure function `renderAt(t)` for `t` in `[0.00, 15.00]` seconds, and expose `window.__setTrailerTime(sec)` for frame-exact stepping and optional local browser capture.
- Composite 3 synchronized layers:
  1. Background Canvas2D (halftone, kinetic typography, radial speed lines, split-screen panels, cyclorama).
  2. Transparent Three.js WebGL2 layer for 3D props (orbit rings, crystal shards, tilted wireframe grid, shattering glass shutters, landing shockwave rings).
  3. Foreground Canvas2D (character sprites, tinted strobe afterimages, RGB split echoes, anime star gleams, energy slash arcs, 2-frame B&W impact flashes, HUD overlays).
- Choreograph multi-pose sequences inside key cuts so motions feel complete:
  - Cut 01 (0.00-1.20s): Slam-open brand reveal (`front -> cool` with star gleam and shock ring).
  - Cut 02 (1.20-2.30s): Tight close-up lock-on with HUD reticle and scanline sweep.
  - Cut 03 (2.30-3.50s): High-speed `run` transitioning into braking `slide` with spark shower.
  - Cut 04 (3.50-4.60s): Tri-view kinetic split-screen (`front`, `side`, `back`).
  - Cut 05 (4.60-5.80s): Stylized multi-view spin (a discrete-pose approximation, not a true continuous 3D turn) (`front -> side -> back -> flipped side -> front`) inside 3D rings.
  - Cut 06 (5.80-6.90s): Editorial magazine parkour chain (`run -> jump -> land`) over elastic typography.
  - Cut 07 (6.90-8.00s): Mid-air somersault (`jump -> kick`) with 4 neon-tinted strobe afterimages.
  - Cut 08 (8.00-9.20s): 4-beat kinetic combo (`run -> slide -> kick -> cool`) with 2-frame B&W impact flashes.
  - Cut 09 (9.20-10.40s): Tilted 3D wireframe grid bullet-time scan on `kick`.
  - Cut 10 (10.40-11.50s): `jump -> kick` smashing 4 translucent 3D glass shutters with impact flash.
  - Cut 11 (11.50-12.50s): 4 rapid 0.25s lookbook poster hard-cuts.
  - Cut 12 (12.50-15.00s): Slow-mo `jump` drop into `land` superhero crouch (B&W impact frame + 3D shockwave rings), rising into `front -> cool` beside the final brand card.
- Synthesize the matching beat and cut-synced SFX via Web Audio API (unlocked on first click) with Play/Pause (`Space`), Restart (`R`), Mute (`M`), Frame step (`ArrowLeft`/`ArrowRight`), clickable 12-cut strip, draggable scrubber, and 3 live theme presets.

### 4. Export 1080p 60fps MP4 Video

When the user requests a downloadable video, prefer capturing the same deterministic HTML composition frame by frame so the MP4 matches the preview. Bundle required libraries locally for an offline deliverable. If using a separate renderer, reproduce and compare the actual visual and audio output; disclose any differences.

- Synthesize the 15.00-second 44.1kHz stereo WAV soundtrack and cut-synced SFX in Python (`numpy` + `wave`) with a soft limiter (`tanh`) to prevent clipping.
- At the default 15 seconds and 60 fps, render 900 frames at the requested aspect ratio; encode with FFmpeg, for example `libx264`, `yuv420p`, AAC and `+faststart`. Square output may use 1080x1080. Ensure audio and frames share the same timing.
- If the user wants to render the exact WebGL HTML version locally on their own machine (e.g. macOS), offer a companion Playwright + FFmpeg script that steps `window.__setTrailerTime(i / 60)`.

### 5. Visual and Technical Verification

Verify every deliverable before presenting it to the user:

- **HTML preview:** Run static validation and inspect a rendered desktop screenshot to confirm zero JS errors, clean sprite cutouts, and unobstructed controls.
- **MP4 video:** Run `ffprobe` to verify exact resolution, `60/1` fps, `h264` (`yuv420p`), `aac` audio, and `15.00s` duration, then extract and inspect a 2x2 keyframe contact sheet (Cut 01, Cut 03, Cut 08, Cut 12) to catch text clipping, dark overlay bugs, or character-text overlap.

## Attribution

Inspired by [ChetasLua’s AO Bot Reveal Trailer](https://github.com/ChetasLua/ao-bot-reveal-trailer), a procedural 3D project. This skill describes an adapted image-led workflow; it does not bundle that project’s source code. Respect the rights and licenses of all supplied assets and dependencies.

## Gotchas

- **Pose direction consistency:** Always check which way generated `run`, `slide`, and `jump` sprites face, and apply `flipX` so the character always faces their travel direction.
- **CJK font fallback in MP4 rendering:** Standard Latin bold fonts like `DejaVuSans-Bold.ttf` render Chinese characters as missing-glyph boxes. When brand copy contains CJK text, query `fc-list` and load an installed Noto Sans CJK or WenQuanYi bold font.
- **Pillow RGBA rectangle traps:** `ImageDraw.rectangle(..., fill=(0, 0, 0, alpha))` can overwrite pixel alpha and create solid dark bands on RGBA canvases, and `fill=(0, 0, 0, 0)` on outlined text punches transparent holes. Use interpolated opaque RGB strips for floor gradients and solid fill + stroke colors for kinetic typography.
- **Brand card breathing room:** Keep the character and final brand text well separated (for example character at `x = 0.24 * W` and brand card at `x = 0.66 * W` in 16:9, or stacked vertically in 9:16) so limbs never collide with letters.
