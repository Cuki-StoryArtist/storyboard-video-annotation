# Feishu Base Contract

Use the existing authenticated `lark-cli` and the `lark-base` command family. Do not build a replacement API client when the CLI supports the operation.

## Record grain and keys

- One row equals one Panel.
- The stable business key is `Scene ID + Panel ID`; never assume `Panel ID` alone is unique.
- Create text records first, retain returned `record_id` values, then upload each screenshot into the matching attachment cell.

## Required user-facing order

The first user-facing item must be the shot image, not only a number.

Preferred field order:

1. `镜头截图` — attachment/image field;
2. `Scene ID`;
3. `Panel ID`;
4. `开始时间码`;
5. `结束时间码`;
6. `镜头持续时间`;
7. `原有台词`;
8. `地点`;
9. `空间类型`;
10. `画面内容`;
11. `特殊人物动作`;
12. `特殊表演倾向`;
13. `其他备注`;
14. `AI 判断依据`;
15. `人工审核状态`.

Use an attachment field schema equivalent to:

```json
{"type":"attachment","name":"镜头截图"}
```

For a new table, try to make `镜头截图` the first/primary field so the grid starts with the image. Upload files with `base +record-upload-attachment` after record creation. If the platform rejects an attachment as the primary field or forcibly pins another primary field first, do not pretend the order succeeded: keep `镜头截图` immediately after the forced primary field, create or configure a gallery/card view with the screenshot as the visual cover when supported, and state the platform limitation in the summary.

Use `base +view-set-visible-fields` to set the final visible field list and order. Include every field that should remain visible.

## Data rules

- Timecodes must reflect the visible TBS timecode origin, not an assumed zero.
- Original timecode, Scene/Panel identifiers, and dialogue are correspondence data only and must not be editorially altered.
- Special action and performance fields may be blank.
- Use `待审核`, `已确认`, or `需要修改` for `人工审核状态`.
- The CSV backup should include `镜头截图路径` or `镜头截图文件名` before identifiers so image-to-record mapping can be audited locally.

## Write and readback

1. Create or resolve the Base/Table and inspect its field schema.
2. Batch-create text records in groups of at most 200.
3. Map returned `record_id` values to the composite key.
4. Upload the matching screenshot to `镜头截图` for every record.
5. Read back projected fields including `镜头截图`, `Scene ID`, `Panel ID`, start/end timecodes, and review status.
6. Verify record count, missing/extra composite keys, duplicates, timecode mismatches, missing attachment cells, and image-to-key alignment.

Do not report Feishu completion while any expected Panel lacks a screenshot attachment. If an upload fails, retry only the failed record after verifying its key and path; do not recreate the whole table or duplicate successful rows.
