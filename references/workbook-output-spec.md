# Storyboard Workbook Output Specification

Use this specification whenever the skill produces its default downloadable deliverable.

## Required Worksheets

### 1. 总览

Include:

- Project or script title.
- Compact full-script understanding summary.
- Visual style and AI-video assumptions.
- Estimated total duration.
- Full-screen B-roll duration.
- Full-screen B-roll coverage calculation and target.

Make the coverage calculation auditable. Full-screen B-roll must be at least 60%.

### 2. 分镜执行表

Use the 13 required columns defined in `SKILL.md`.

Formatting requirements:

- Freeze the header row and the first one or two useful columns.
- Enable filters.
- Use controlled column widths and wrapped text.
- Use readable row heights; do not rely on unconstrained autofit.
- Visually distinguish `强烈建议`, `一般建议`, and `不建议`.
- Visually distinguish rows whose `节奏建议` contains `全屏 B-roll`.
- Keep the complete production decision in each row.

### 3. AI提示词

Extract only rows with an AI-video prompt.

Use columns:

| 编号 | 对应原句 | 画面建议 | 即梦中文 Prompt | 建议源片时长 | 生成风险与备注 |
|---|---|---|---|---:|---|

Give the Prompt column enough width for easy reading and copying.

### 4. 制作清单

Include:

- 人物正面关键保留点
- 主人公重点演绎清单
- 优先生成清单
- 制作风险

## Visual Style

- Use a professional, restrained style suitable for production handoff.
- Prefer dark blue headers, light blue information areas, and restrained accent colors.
- Keep key labels bold and maintain strong contrast.
- Avoid decorative charts or styling that does not improve execution.

## Verification

Before delivery:

1. Inspect key ranges and values.
2. Render and visually check every worksheet.
3. Fix clipped headers, unreadable wrapped text, excessive row heights, and poor column widths.
4. Verify the coverage calculation.
5. Export one final `.xlsx` file.

Do not deliver preview images or builder files unless the user requests them.
