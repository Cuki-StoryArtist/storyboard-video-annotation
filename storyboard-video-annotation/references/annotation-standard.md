# Annotation Standard

## Decision rule

Add text only when the original storyboard does not make an important fact sufficiently clear and the added information helps an AI or production reader understand the scene. If the frame and adjacent shots already communicate it easily, leave it unlabelled.

Annotations must describe the storyboard's actual visual solution, not paraphrase the script. Preserve meaningful visual inventions such as substituted actions, comic reversals, altered staging, performance contrast, and changed spatial presentation.

## Scene information

Use short, concrete fields:

- `地点`: the specific place shown or securely established by the sequence;
- `空间类型`: corridor, stairwell, exhibition hall, street, room, rooftop, and similar spatial category;
- `画面内容`: the current principal character/environment/story content that is not already obvious enough.

Keep location and spatial relationship consistent across continuous shots. Update only when location, spatial relationship, or the main subject changes. Do not repeat the same paragraph on every Panel merely to fill cells.

Re-evaluate `空间类型` when the view crosses a threshold or changes between interior, exterior, overhead, POV, projection, reflection, or imagined space. A continuous action can still require a new spatial label when the represented space changes.

Mark uncertain facts as `待确认`. Do not turn an inference into a fact.

## Special action and performance

These fields are optional. Add them only for:

- dramatic, intentionally exaggerated, comic, or stylized movement;
- a special facial or emotional reaction important to the story;
- unusual body language with a clear performance intention;
- temporal action that a single storyboard frame is likely to misrepresent;
- action whose meaning is easy for an AI or production reader to misunderstand.
- a multi-beat setup, reversal, payoff, or recovery whose rhythm carries the story or comedy.

Ordinary walking, turning, standing, lifting a hand, and routine dialogue gestures usually stay blank.

Use compact wording such as `连续腾跃；抽帧式逼近` or `多人扑抓集体落空；滑稽节奏`. Describe what the performance is doing, not a speculative motivation.

For a multi-beat action, name the observable chain and its designed contrast, for example `猛冲—侧闪—扑空—失衡；由强势转为狼狈`. Split the event when the action, performance intention, or spatial viewpoint changes; do not let an earlier description linger over a later payoff.

Treat one independently editable annotation clip as one shot or one uninterrupted performance beat. A cut, subject change, action-to-reaction transition, setup-to-payoff transition, or materially different performance intention requires a new clip, even when the separate clips together create one contrast. Never combine one character's action and another character's later reaction into a single label merely to summarize their emotional contrast. Adjacent Panels may share one clip only when they remain in the same shot/beat and the complete wording is true throughout the full timed range.

## Excluded camera-language labels

Do not add fields or video labels for shot size, camera angle, or camera movement by default. The storyboard already communicates these visually.

When the user explicitly asks to preserve a camera-led transition, or when omitting the camera would falsely imply that a character moved, name only the exact operation and its narrative handoff. Keep the character's simultaneous performance gesture separate and observable.

## Video placement

- Scene information: upper right by default, with short line breaks for location, space, and content.
- Special action/performance: lower area or another safe region only for its relevant time range.
- Do not reserve empty boxes when no special note is needed.
- Use a consistent font, size, color, margins, and hierarchy.
- Never cover faces, important actions, composition, original dialogue, timecode, or Scene/Panel labels.

When a single fixed placement conflicts with the composition, move only the affected annotation to a verified safe area and preserve the style.

Check placement at the start, middle, and end of every timed event. A safe position in one Panel may cover a face, limb, object, or payoff in the next Panel; split or reposition the event when necessary.

## Screenshot selection

Create one screenshot for every Panel from the original unannotated source:

- choose the midpoint or the first clear stable frame after a cut;
- avoid transition frames and temporary black frames unless black is the actual Panel content;
- keep the original frame aspect ratio and TBS labels;
- do not burn the new annotations into this identification screenshot;
- name it with a stable composite key, for example `A04_P02_00-00-05-00.png`.

For a Panel whose meaning changes substantially over time, the Base still receives one representative screenshot; additional supporting frames may be attached after the representative image only when needed.

The screenshot identifies the Panel; it does not replace motion review. Determine temporal action and performance from the video before selecting or describing the representative frame.
