# Annotation Standard

## Decision rule

Add text only when the original storyboard does not make an important fact sufficiently clear and the added information helps an AI or production reader understand the scene. If the frame and adjacent shots already communicate it easily, leave it unlabelled.

## Scene information

Use short, concrete fields:

- `地点`: the specific place shown or securely established by the sequence;
- `空间类型`: corridor, stairwell, exhibition hall, street, room, rooftop, and similar spatial category;
- `画面内容`: the current principal character/environment/story content that is not already obvious enough.

Keep location and spatial relationship consistent across continuous shots. Update only when location, spatial relationship, or the main subject changes. Do not repeat the same paragraph on every Panel merely to fill cells.

Mark uncertain facts as `待确认`. Do not turn an inference into a fact.

## Special action and performance

These fields are optional. Add them only for:

- dramatic, intentionally exaggerated, comic, or stylized movement;
- a special facial or emotional reaction important to the story;
- unusual body language with a clear performance intention;
- temporal action that a single storyboard frame is likely to misrepresent;
- action whose meaning is easy for an AI or production reader to misunderstand.

Ordinary walking, turning, standing, lifting a hand, and routine dialogue gestures usually stay blank.

Use compact wording such as `连续腾跃；抽帧式逼近` or `多人扑抓集体落空；滑稽节奏`. Describe what the performance is doing, not a speculative motivation.

## Excluded camera-language labels

Do not add fields or video labels for shot size, camera angle, or camera movement by default. The storyboard already communicates these visually.

## Video placement

- Scene information: upper right by default, with short line breaks for location, space, and content.
- Special action/performance: lower area or another safe region only for its relevant time range.
- Do not reserve empty boxes when no special note is needed.
- Use a consistent font, size, color, margins, and hierarchy.
- Never cover faces, important actions, composition, original dialogue, timecode, or Scene/Panel labels.

When a single fixed placement conflicts with the composition, move only the affected annotation to a verified safe area and preserve the style.

## Screenshot selection

Create one screenshot for every Panel from the original unannotated source:

- choose the midpoint or the first clear stable frame after a cut;
- avoid transition frames and temporary black frames unless black is the actual Panel content;
- keep the original frame aspect ratio and TBS labels;
- do not burn the new annotations into this identification screenshot;
- name it with a stable composite key, for example `A04_P02_00-00-05-00.png`.

For a Panel whose meaning changes substantially over time, the Base still receives one representative screenshot; additional supporting frames may be attached after the representative image only when needed.
