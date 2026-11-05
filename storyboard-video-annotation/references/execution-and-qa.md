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

Use the video frame rate for frame/timecode conversion. For 24 fps, frame `f` converts to `HH:MM:SS:FF` using integer division and `FF = f mod 24`. Add a TBS offset only when verified from the burned-in first frame.

## Editing and rendering

- Keep annotations on independent editable tracks/layers whenever the available path supports it.
- Continuous scene information can span consecutive Panels when the content is unchanged.
- Special action/performance text appears only during the relevant shot or action interval.
- Preserve source audio. Inspect streams before choosing `-an`, stream copy, or audio re-encoding.
- When FFmpeg is the controlled fallback, use the source as V1/picture, apply only the new overlay layer, retain exact duration/frame rate/frame count, and use a compatible delivery codec and pixel format.
- Package editable SRT/ASS or graphics timing assets with the fallback project so the user can continue in Premiere.

Never launch a visible desktop window as part of automation unless the current request explicitly permits it.

## Required QA

Before delivery, verify:

1. Source and output resolution, frame rate, duration, frame count, video codec, and audio stream behavior.
2. First and last annotation event timing, plus representative scene transitions.
3. Original timecode, Scene/Panel labels, and dialogue remain visible and in the original positions.
4. New text does not cover important faces, actions, composition, or existing TBS text.
5. Every Panel has exactly one primary screenshot file and exactly one matching Feishu record.
6. Feishu readback has no missing, extra, duplicate, shifted, or attachment-empty records.
7. The CSV contains the same composite keys, timecodes, annotation content, and screenshot mapping.
8. Project media copies match their sources by hash when copies are part of delivery.
9. The project file opens structurally or has its limitation clearly stated; do not infer native editability from a file extension alone.

Use frame samples and region comparisons such as SSIM to distinguish ordinary re-encoding differences from accidental TBS changes. Visual inspection remains necessary for layout and screenshot suitability.

## Execution summary

Report:

- processed source name and duration;
- Scene/Panel counts;
- number of scene annotations and special-performance annotations;
- screenshot count and whether every Panel received one;
- Feishu write/readback results;
- editing/export method actually used;
- whether original TBS content was preserved;
- items requiring human review;
- technical limitations and recommended next step.
