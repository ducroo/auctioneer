# Photo Staging

Photo staging makes Ricardo upload predictable while preserving originals.

## Rules

- Never modify originals in `photos/`.
- Create upload-ready copies in a direct child folder of the item folder, usually `photos_upload/`.
- Name files in final order: `01_main.jpg`, `02_detail.jpg`, `03_mark.jpg`, etc.
- Make the first image a clear, searchable thumbnail. For sets, prefer the full set; for furniture, prefer the complete object in a clean angle.
- Keep only images that should be uploaded; exclude duplicates, blurry photos, or private-background details when they do not help sell the item.
- Prefer JPEG for photos unless transparency or text screenshots require PNG.
- Keep dimensions and filesize reasonable for web upload. If resizing is needed, preserve visual detail and avoid over-compression.
- Do not crop out important defects; defect/detail images should remain visible and honest.

## Ricardo-Specific Lessons

- Ricardo previously rejected nested or non-inbound upload paths. Use simple direct-child upload copies when possible.
- Drag-reordering uploaded images has been unreliable. Upload in the intended order and prepare the main thumbnail before initial publication.
- If replacing/reordering photos after publication, expect extra friction; log the reliable recovery path in `posting-learning-log.md`.

## Suggested Output

For each item prepared for Ricardo, aim for:

- `photos_upload/01_main.jpg`
- `photos_upload/02_context.jpg`
- `photos_upload/03_detail.jpg`
- `photos_upload/04_condition.jpg`

The exact count depends on the item. Quality beats volume.
