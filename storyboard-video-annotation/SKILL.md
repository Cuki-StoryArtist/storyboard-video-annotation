---
name: storyboard-video-annotation
description: Analyze an existing storyboard or Storyboard Pro video, add only necessary scene and special-performance annotations, create panel-level Feishu Base records with a shot screenshot first, and deliver a verified annotated video plus editable project assets. Use for storyboard-video annotation, source swaps, annotation-table updates, or re-exports; do not use to redesign storyboards or annotate camera language by default.
---

# Storyboard Video Annotation

Use this skill to supplement an already completed storyboard video without rebuilding or obscuring its original TBS information.

## Start by fixing the scope

- Identify the exact target video named by the user. Do not silently switch clips or expand from a sample to a full episode.
- Treat source videos, scripts, export specifications, and reference documents as read-only.
- Read the current project instructions and the latest relevant script before analyzing story content. The video image is the primary evidence; the script only resolves context.
- If the target is a 3D storyboard, reread the complete latest script for the affected sequence before every modification and check the shot in full-sequence continuity. Stop if the script is missing, ambiguous, or conflicts with the requested change.
- Work in the background. Do not open Premiere Pro, Blender, or any other desktop application window unless the current user request explicitly asks for it.

## Non-negotiable preservation rules

Preserve the original video exactly except for new annotation layers:

- burned-in timecode;
- Scene/shot and Panel identifiers;
- dialogue and its position, font, size, and timing;
- frame composition, aspect ratio, shot order, duration, frame rate, and audio.

Never recreate, move, cover, or duplicate existing TBS information. When it is burned into the source, treat it as immutable picture content.

Do not add shot size, camera angle, or camera movement labels unless the user explicitly requests them.

Read [annotation-standard.md](references/annotation-standard.md) before deciding annotation text or placement.

## Required workflow

1. Inventory the target folder and references. Confirm the exact source filename and output locations.
2. Probe the source for duration, resolution, frame rate, frame count, codecs, and audio streams. Inspect the first frame to determine the visible TBS timecode origin.
3. Detect Scene/Panel boundaries from the actual video and build an inclusive frame map. Use `Scene ID + Panel ID` as the composite key because Panel IDs can repeat between scenes.
4. Review each shot in sequence context. Record only changed scene facts and genuinely necessary special action/performance notes.
5. Extract one representative original-frame screenshot for every Panel. Use a clear, stable frame inside the Panel, avoiding dissolves, black transition frames, and motion-blurred frames when a clearer frame exists. Keep original TBS information visible.
6. Create the panel-level CSV and Feishu Base. The Feishu user-facing record must lead with the shot screenshot, then identifiers and timecodes. Follow [feishu-base.md](references/feishu-base.md).
7. Add annotations as independently editable layers when the available editing path supports it. Prefer the user's existing Premiere installation only when reliable background automation is available. Otherwise create PR-compatible subtitle/graphics assets and use a controlled FFmpeg fallback for the review MP4; disclose the limitation and never call it a Premiere export.
8. Verify metadata, timing, original TBS regions, Feishu records, screenshot alignment, and deliverables. Follow [execution-and-qa.md](references/execution-and-qa.md).

## Source replacement and re-export

When the user supplies a corrected source and says timing is unchanged:

- compare old and new duration, frame rate, frame count, audio, and representative non-correction regions;
- inspect the corrected element directly instead of trusting the filename;
- reuse annotation event timing only after the comparison passes;
- recalculate displayed timecodes from the new TBS origin;
- update CSV and Feishu timecode fields without changing unrelated annotation content;
- re-export, regenerate review screenshots, refresh project media copies, and rerun QA.

If timing or picture content differs materially, stop treating it as a simple source swap and remap affected Panels.

## Delivery

Deliver only the files requested by the project, normally:

- annotated MP4;
- editable PR project or an explicitly described reference/fallback project;
- required media and editable subtitle/graphics assets;
- Feishu Base link;
- panel CSV backup, with screenshot filename/path traceability;
- representative annotation screenshots;
- concise execution summary including technical limitations and items needing human review.

Do not claim GUI, Premiere, Feishu, or export success without an observable result and readback/inspection.
