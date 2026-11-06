# Execution and QA

## Project layout

Respect the project folders supplied by the user. Keep source/reference areas read-only. Put generated scripts, extracted frames, temporary media, subtitle files, and project assets under the designated engineering folder; put final deliverables under the output folder.

Do not delete or overwrite source media. A final deliverable may be replaced when the user explicitly requests a re-export; render to a temporary output first, validate it, then replace the deliverable.

## Analysis artifacts

Maintain a deterministic Panel timing map containing at least:

- `Scene ID` and `Panel ID`;
- inclusive start and end frame;
- source-relative start/end time;
- visible TBS start/end timecode;
- screenshot frame and filename;
- scene and special-performance annotation events.
- concise visual evidence or reasoning for non-obvious annotations, especially where the storyboard departs from the script.

Use the video frame rate for frame/timecode conversion. For 24 fps, frame `f` converts to `HH:MM:SS:FF` using integer division and `FF = f mod 24`. Add a TBS offset only when verified from the burned-in first frame.

## Semantic review gate

Before creating overlays or publishing records:

1. Review each proposed event at its start, middle, and end, plus the shots immediately before and after it.
2. Confirm the visible action chain, character initiative, spatial viewpoint, performance contrast, and event boundary from the moving storyboard.
3. Compare against the script only after the visual reading. Remove any action that exists only in the script and preserve visual redesigns.
4. Check for setup/payoff structures such as anticipation followed by reversal, overshoot, rescue, escape, or comic recovery.
5. Split scene or performance events when action, space, viewpoint, or dramatic function changes.

Do not proceed to final rendering while an annotation could be true merely because it copies the script but is not demonstrated by the timed picture.

## Editing and rendering

- For every PR deliverable, use the original unannotated storyboard video as V1. Never use the burned-in review MP4 as the project picture.
- Put scene information and special action/performance on separate, unmuted Premiere native text/graphics tracks.
- Create one independently selectable native text clip per annotation event. Verify that source text, position, and duration remain editable inside Premiere.
- Do not add a visible category heading such as `故事板额外设计`; special annotation clips should show only the useful `动作：` and `表演：` content.
- Continuous scene information can span consecutive Panels when the content is unchanged.
- Special action/performance text appears only during the relevant shot or action interval.
- Preserve source audio. Inspect streams before choosing `-an`, stream copy, or audio re-encoding.
- When FFmpeg is the controlled fallback, use the source as V1/picture, apply only the new overlay layer, retain exact duration/frame rate/frame count, and use a compatible delivery codec and pixel format.
- Package SRT/ASS timing assets as backups only. They do not satisfy the native editable PR requirement.
- If native editable PR construction or verification is unavailable, report the blocker instead of presenting a composite-video reference project as an editable PR deliverable.

Never launch a visible desktop window as part of automation unless the current request explicitly permits it.

## Required QA

Before delivery, verify:

1. Source and output resolution, frame rate, duration, frame count, video codec, and audio stream behavior.
2. First and last annotation event timing, plus representative scene transitions.
3. Original timecode, Scene/Panel labels, and dialogue remain visible and in the original positions.
4. New text does not cover important faces, actions, composition, or existing TBS text.
5. Every Panel has exactly one primary screenshot file and exactly one matching Feishu record.
6. Feishu readback has no missing, extra, duplicate, shifted, or attachment-empty records, and confirms the Base is stored directly under `我的文档库/EPXX` with no scene-level subfolder.
7. The CSV contains the same composite keys, timecodes, annotation content, and screenshot mapping.
8. Project media copies match their sources by hash when copies are part of delivery.
9. The PR project references the unannotated source, contains the expected native text clip count on unmuted tracks, and preserves per-event source text and timing. Verify native text components structurally and, when permitted, by Premiere readback; do not infer editability from a file extension alone.
10. Every semantic annotation matches the actual timed storyboard; no superseded, script-only, or mechanically inherited action remains.
11. Viewpoint and spatial labels are correct at threshold changes, especially interior/exterior, overhead, POV, projection, and similar transitions.
12. A text search across CSV, SRT/ASS, generated records, and summaries finds no wording from rejected interpretations after a correction.
13. A text search across the PR project and timing assets confirms that no visible `故事板额外设计` category heading was added.

Use frame samples and region comparisons such as SSIM to distinguish ordinary re-encoding differences from accidental TBS changes. Visual inspection remains necessary for layout and screenshot suitability.

After a semantic correction, invalidate stale representative screenshots and review composites, regenerate every affected deliverable from the same event source, and re-run the full gate rather than patching only the visible MP4.

## Execution summary

Report:

- processed source name and duration;
- Scene/Panel counts;
- number of scene annotations and special-performance annotations;
- screenshot count and whether every Panel received one;
- Feishu write/readback results;
- editing/export method actually used;
- native PR text-track counts and how editability was verified;
- whether original TBS content was preserved;
- items requiring human review;
- technical limitations and recommended next step.
