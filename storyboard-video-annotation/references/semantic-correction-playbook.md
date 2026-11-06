# Semantic Correction and Iteration Playbook

Read this reference for user corrections, repeated review rounds, source replacements, or any annotation whose meaning depends on motion, viewpoint, reflection, shadow, foreground reveal, background business, or a multi-panel beat.

## Attribute the visible change before naming it

For every proposed annotation, identify what actually causes the change:

- character or prop movement;
- camera movement or reframing;
- reflection, monitor, projection, POV, or another mediated view;
- lighting, cast shadow, color treatment, or graphic effect;
- foreground occlusion or a reveal created by the camera;
- continuity in the background while the main dialogue continues.

Do not convert one cause into another. In particular:

- do not say a character `进入前景` when the character stays in place and a pull-back or pan reveals them;
- do not describe a gray frame as mood or color grading when the picture shows a cast shadow;
- do not call a reflection or screen image the physical position of the reflected subject;
- do not infer `混乱`, motivation, or emotion when the picture only establishes an action or spatial handoff;
- if the meaningful performance is a gesture such as扶额、干呕、停手、偷笑, name the gesture instead of filling the note with abstract transition language.

Camera language remains excluded by default. When the user explicitly asks to preserve a camera-led transition or when character-versus-camera causality would otherwise be wrong, describe only the exact operation and story function, such as `摄像机缓慢拉开，带出兰雪`.

## Reconstruct the beat as timed motion

Review the moving Panels in this order:

1. the shot immediately before the event;
2. the event start, middle, and end;
3. the shot immediately after the event;
4. the complete sequence for setup, payoff, and continuity.

Determine whether the beat is one uninterrupted action or several truth-changing phases. Split it when the subject, viewpoint, cause, or dramatic function changes. A reflection that first preserves the previous action and a later camera pull that reveals a new subject are separate editable clips even when together they form one transition.

Keep background performance separate from the main beat when it carries its own continuity or comedy. Examples include a character continuing to vomit after being shaken, a worker stopping a cleaning task, or a background character reacting while another character speaks.

## Use narrow, observable wording

- Prefer literal verbs and visible relationships.
- Write `动作` for what changes physically or spatially.
- Write `表演` for gesture, rhythm, contrast, or the designed comic/dramatic effect.
- Avoid repeating the same fact in both fields.
- Avoid stage-direction filler such as `进入画面` if the useful fact is a camera reveal, specific gesture, reflection handoff, or shadow effect.
- Keep prop and task labels short, for example `前景：古藏录` or `包子：擦沙发`.

Do not stretch a task label through unrelated Panels merely because the same task appeared earlier. Add a new short event when the task is shown again in a later close-up, and end it when the character stops, looks away, or the shot changes function.

## Respect source replacements

Never trust the new filename as proof that old timing still applies.

- Compare duration, frame rate, frame count, audio streams, and representative frames.
- If timing or picture content differs materially, rebuild the inclusive Scene/Panel map from the new source.
- Re-extract every representative screenshot from the new source.
- Do not reuse old frame numbers, screenshots, or annotation boundaries until comparison proves them valid.
- Detect short Panels as well as regular cadence; fixed-interval sampling can miss brief Panels near cuts or sequence endings.
- Re-evaluate every carried annotation against the new picture, even when the Scene ID appears unchanged.

## Treat one event source as authoritative

Maintain annotation events in one deterministic source, then regenerate all derivatives:

- review MP4;
- native editable Premiere text clips;
- SRT/ASS backups;
- panel JSON and CSV;
- Feishu Base records;
- QA manifests and summaries.

Do not patch only the visible MP4 or only the PR project. A semantic correction is incomplete while any derivative still contains the rejected wording or old timing.

After each correction:

1. search text assets, CSV/JSON, and summaries for the rejected phrase;
2. inspect or decompress the PR project and verify the old phrase is absent and the new native text is present;
3. render to a temporary file;
4. inspect the corrected event at start, middle, end, and adjacent shots;
5. verify placement does not cover faces, gestures, dialogue, timecode, Scene/Panel labels, or the object being identified;
6. replace the final deliverable only after structural and visual QA pass.

## Preserve editability and visual evidence

- Original unannotated video stays on V1.
- Every visible addition, including small task or prop labels, must be an independently editable native PR object.
- Reflections, foreground silhouettes, arrows already burned into the source, original dialogue, and red TBS labels remain immutable picture content.
- Representative Base screenshots come from the unannotated source, not the review MP4.
- Base records must still lead with the screenshot and use `Scene ID + Panel ID` as the key.

For Feishu destination and folder rules, follow [feishu-base.md](feishu-base.md).
