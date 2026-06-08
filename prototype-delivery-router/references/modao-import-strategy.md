# Modao Import Strategy

Use this before importing HTML or prototypes into Modao.

## Key Lesson

Browser preview is not Modao acceptance. Modao converts HTML into its own layers and may recalculate text boxes, filter images, or distort layout.

## Import Modes

### Mode A: Visual Fidelity First

Use when the user needs the prototype to look exactly like the reference.

Recommended:
- Render phone screens to images.
- Host images on reachable HTTPS URLs.
- Put editable annotations and PRD text beside the image.

Do not use:
- local image paths
- `data:image/png;base64` images
- browser-only assumptions

### Mode B: Modao Editability First

Use when the user must edit phone components inside Modao.

Recommended:
- simple absolute-positioned HTML layers
- wide text boxes
- short text lines
- no flex/grid dependency
- no overflow hidden, text overflow, or nowrap for critical text

Tradeoff:
- visual fidelity will be lower and requires post-import cleanup.

### Mode C: PRD Review First

Use when alignment is more important than editing the prototype.

Recommended:
- phone screen as image
- PRD as editable text
- annotation markers editable
- flow labels and arrows editable

## Required Validation

Before full import:
1. Import one page only.
2. Check image visibility.
3. Check progress percent and critical symbols.
4. Check text completeness.
5. Check annotation-to-PRD numbering.
6. Check layout alignment and spacing.
7. Only then expand to a block or full batch.

## Known Risks

- Base64 images can disappear in Modao.
- Text can truncate even when browser preview is normal.
- Percent signs and short labels can be dropped if text boxes are recalculated.
- Long PRD text boxes can become unreadable after import.
- Public HTTPS image hosting may expire; for long-term work, use a stable company/GitHub/CDN asset URL.

## Failure Response

If import output differs from browser preview:
1. Do not keep patching randomly.
2. Identify whether the failure is text, image, layout, or missing element.
3. Switch import mode if the same failure repeats.
