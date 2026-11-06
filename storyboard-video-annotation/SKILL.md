---
name: storyboard-video-annotation
description: Deeply interpret an existing storyboard or Storyboard Pro video, annotate its actual scene and performance design, create panel-level Feishu Base records led by shot screenshots, and deliver verified video and editable assets. Use for storyboard-video annotation, semantic corrections, source swaps, annotation-table updates, or re-exports; do not use to redesign storyboards or annotate camera language by default.
---

# Storyboard Video Annotation

Use this skill to supplement an already completed storyboard video without rebuilding or obscuring its original TBS information.

## Team guide image

A shareable Chinese overview is available at [storyboard-video-annotation-guide.png](assets/storyboard-video-annotation-guide.png). It explains the skill's purpose and required inputs. Use it for onboarding or handoff; it is not required for ordinary execution.

## Interpretation principle

A storyboard is an authored visual adaptation, not an illustrated transcript. The script establishes narrative objectives and context; the storyboard artist may improve, replace, compress, or invert actions, performance, rhythm, staging, and spatial presentation. Annotate what the moving storyboard actually designs.

Before making semantic annotation decisions, read [story-interpretation.md](references/story-interpretation.md). Use a visual-first pass to reconstruct the action and performance without borrowing the script's verbs, then use the script only to resolve identity, objectives, unseen context, and continuity. If script and picture differ, the picture controls the action and performance annotation.

## Start by fixing the scope

- Identify the exact target video named by the user. Do not silently switch clips or expand from a sample to a full episode.
- Treat source videos, scripts, export specifications, and reference documents as read-only.
- Read the current project instructions and the latest relevant script before analyzing story content. Do not convert script sentences directly into annotations; the moving image is the primary evidence and the script only resolves context.
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

## Premiere project delivery contract

When a Premiere project is part of the delivery, native editability is mandatory:

- Put the original unannotated storyboard video on V1. Do not use the burned-in review MP4 as the project picture.
- Put scene information and special action/performance annotations on separate, unmuted Premiere native text/graphics tracks.
- Create one independently selectable native text clip per annotation event. Its source text, position, and duration must be directly editable inside Premiere.
- Every user-visible addition must also exist inside the PR project as an independently editable native object on an appropriate unmuted track. This includes small scene-element labels, callouts, arrows, shapes, highlights, masks, and any other added visual—not only the main scene and performance text.
- The review MP4 may mirror those additions as burned-in overlays, but no added visible element may exist only in the rendered video, ASS/SRT, or another sidecar asset. If an addition cannot be represented and verified as editable in the PR project, report it as a blocker before delivery.
- Visible special-action text starts with the useful fields such as `动作：` and `表演：`. Do not add a visible category heading such as `故事板额外设计`.
- SRT, ASS, or other sidecar files are backups only. They do not substitute for native editable text in the PR project.
- If a native editable project cannot be created and verified, report the blocker. Do not deliver a composite-video reference project as the editable PR project, and do not infer editability from the `.prproj` extension.

## Required workflow

1. Inventory the target folder and references. Confirm the exact source filename and output locations.
2. Probe the source for duration, resolution, frame rate, frame count, codecs, and audio streams. Inspect the first frame to determine the visible TBS timecode origin.
3. Detect Scene/Panel boundaries from the actual video and build an inclusive frame map. Use `Scene ID + Panel ID` as the composite key because Panel IDs can repeat between scenes.
4. Perform a visual-first review of every Panel in sequence context. Reconstruct the actual action chain, spatial viewpoint, setup/turn/payoff rhythm, character performance, and continuity before reconciling it with the script. Attribute each visible change to its real cause—character, camera, reflection/display, foreground reveal, shadow/light, prop, or background business—before writing the annotation. Record only changed scene facts and genuinely necessary special action/performance notes.
5. Extract one representative original-frame screenshot for every Panel. Use a clear, stable frame inside the Panel, avoiding dissolves, black transition frames, and motion-blurred frames when a clearer frame exists. Keep original TBS information visible.
6. Run a semantic audit before publishing: every annotation must be demonstrable from its timed Panels or clearly marked as contextual inference; no script-only action may survive. Then create the panel-level CSV and Feishu Base. The Feishu user-facing record must lead with the shot screenshot, then identifiers and timecodes. Follow [feishu-base.md](references/feishu-base.md).
7. Build the PR project according to the Premiere project delivery contract: unannotated source on V1, separate unmuted native tracks, and one independently editable native object per visible addition. Use a controlled FFmpeg render for the review MP4 when needed, but never substitute that composite or sidecar subtitles for the native PR layers.
8. Verify metadata, timing, original TBS regions, Feishu records, screenshot alignment, and deliverables. Reconcile the review MP4 against the PR project so every added visible element has a corresponding editable native PR object and no PR-only or render-only addition is left unmatched. Follow [execution-and-qa.md](references/execution-and-qa.md).

## Corrections and iteration

Treat a user's correction of story, action, performance, or space as new semantic evidence, not as a wording-only patch.

For semantic corrections, repeated review rounds, source swaps, or camera/reflection/shadow-dependent beats, read [semantic-correction-playbook.md](references/semantic-correction-playbook.md) before editing.

- Rewatch the complete action beat and its neighboring shots; identify setup, reversal or payoff, recovery, viewpoint changes, and continuity effects.
- Update every affected scene event, special-performance event, timing range, placement, CSV/Base field, SRT/ASS asset, review screenshot, and summary. Search generated text for superseded interpretations.
- Render to a temporary output, visually inspect the corrected event at start/middle/end and adjacent transitions, then replace the final deliverable only after QA passes.
- If Feishu has already been written, update the existing keyed records and read them back; do not create duplicate rows or leave the video and Base semantically inconsistent.

## Source replacement and re-export

When the user supplies a corrected source and says timing is unchanged:

- compare old and new duration, frame rate, frame count, audio, and representative non-correction regions;
- inspect the corrected element directly instead of trusting the filename;
- reuse annotation event timing only after the comparison passes;
- rerun the visual-first semantic pass for every changed picture region rather than preserving old wording by default;
- recalculate displayed timecodes from the new TBS origin;
- update CSV and Feishu timecode fields without changing unrelated annotation content;
- re-export, regenerate review screenshots, refresh project media copies, and rerun QA.

If timing or picture content differs materially, stop treating it as a simple source swap and remap affected Panels.

## Delivery

Deliver only the files requested by the project, normally:

- annotated MP4;
- native editable PR project when PR delivery is in scope;
- required media and editable subtitle/graphics assets;
- Feishu Base link;
- panel CSV backup, with screenshot filename/path traceability;
- representative annotation screenshots;
- concise execution summary including technical limitations and items needing human review.

Do not claim GUI, Premiere, Feishu, or export success without an observable result and readback/inspection.
