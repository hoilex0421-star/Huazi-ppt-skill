---
name: huawei-insight-deck
description: >-
  Build Huawei-style restrained-red 16:9 reading slides and one-pagers for
  executive research materials. Use when Codex needs the visual system,
  layout components, and render-QA mechanics for dense Chinese reading PPTs:
  red claim title, light-red insight/judgement bands, dashed route panels,
  comparison cards, case cards with images, tables, footers, and source notes.
  Trigger on requests such as 华为风格PPT、阅读型PPT、研究一页纸、技术路线图、
  案例卡、对比表、结论栏、版面优化、渲染检查. This is a visual/layout foundation
  skill; pair it with tech-research-deck or investment-recommendation-deck when
  the task requires deciding the research or investment narrative.
---

# Huawei-Style Reading Deck Foundation

Use this skill as the **visual and production layer** for Huawei-style reading
PPTs. It defines the restrained-red house style, reusable page components,
PowerPoint helper functions, and render-QA workflow.

It should not decide the business or technical argument by itself. For narrative
logic, use a task skill first:

- `$tech-research-deck` for technical architecture, route, and trend research.
- `$investment-recommendation-deck` for company investment recommendation logic.

Then use this skill to build or polish the slides.

## When This Skill Should Lead

Use this skill directly when the user already has the argument and needs:

- a Huawei-style reading slide or one-pager;
- a dense but clean technical or business layout;
- route diagrams, comparison tables, case cards, or chart-like evidence blocks;
- PPT polishing, alignment, image placement, or render QA;
- conversion of a Markdown outline into a visually consistent slide.

When the user is still asking **what to say**, do not lead with this skill:

- use `$tech-research-deck` for technology structure and trend judgement;
- use `$investment-recommendation-deck` for company recommendation logic.

## Core Visual System

- 16:9 white canvas, dense but ordered, with equal safe margins.
- 微软雅黑 everywhere.
- `C7000B` red is the primary accent for claim titles, key labels, judgement
  strips, and conclusions.
- Use muted gray cards, light-red bands, and dashed rounded panels.
- **Hard color budget:** each slide may use at most **three theme colors**.
  White, black, grayscale neutrals, and light tints derived from an active
  theme color do not count. Default to one dominant color plus one supporting
  color; use the third only for a stable semantic role.
- Follow consulting-deck color discipline: high-contrast white space,
  McKinsey-like deep-blue restraint, or BCG-like green restraint. Pick one
  palette logic for the slide/deck; do not casually mix palette families or
  assign a different hue to every card, stage, person, or category.
- One slide should carry one argument. If mechanism, evidence, and case detail
  compete for space, split the page.

## Page Components

Use `scripts/deck_helpers.py` for deterministic layout:

- Global chrome: `newdeck`, `blank`, `title_band`, `footer`, `note`.
- Reading-page bands: `insight_band`, `section_header`, `conclusion_band`.
- Comparison and evidence: `card`, `spec_table`, `image_case_card`, `image_ph`.
- Technical diagrams: `dashed_panel`, `route_node`, `stage_box`, `arrow`,
  `time_axis`, `event_card`, `tag_chip`, `legend`.
- Charts: `stacked_bar`, `seg`, `dot`, `hline`.

Detailed geometry and component rules live in:

- `references/layout-and-visual-spec.md` for exact coordinates and QA pitfalls.
- `references/template-archetypes.md` for reusable visual page silhouettes.
- `references/data-rigor-and-caveats.md` for source and evidence discipline.

Read only the reference file needed for the current slide type.

## Recommended Build Flow

1. Use the domain skill or user brief to decide the slide argument.
2. Pick a visual archetype from `references/template-archetypes.md`.
3. Build with `scripts/deck_helpers.py`; reuse helpers instead of manually
   redrawing common components.
4. Put detailed sources in speaker notes; keep on-page source/caliber notes short.
5. Run `assert_theme_color_budget(slide)` on every slide.
6. Render to PNG and inspect before delivery.

## Render-QA Requirements

Always render and inspect before final delivery:

```bash
python3 your_build.py
libreoffice --headless --convert-to pdf --outdir outputs your_deck.pptx
pdftoppm -png -r 200 outputs/your_deck.pdf outputs/preview
```

Check:

- `assert_theme_color_budget(slide)` passes with no more than three theme colors;
  pictures are excluded from this count.
- No text overlap or clipped labels.
- Title and judgement bands stay readable and do not wrap unintentionally.
- Arrows sit in gaps between boxes.
- Tables do not shrink body text below readable size.
- Images sit inside their owning card or frame; no floating screenshots.
- Footer/source notes stay within the footer area.

## Boundary

This skill is responsible for **how the page looks and validates**, not for
deciding whether a technology is promising or whether a company is investable.
When those decisions are required, invoke the relevant upper-layer skill first
and then use this skill for slide construction.
