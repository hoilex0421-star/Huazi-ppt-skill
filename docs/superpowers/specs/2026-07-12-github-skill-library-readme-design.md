# GitHub AI Research Skills Library Design

## 1. Background

The current repository publishes two independently callable Codex skills:

- `huawei-insight-deck`: builds restrained-red executive research slides and one-pagers.
- `tech-research-deck`: turns source materials and web research into structured technology research decks.

The repository currently presents itself mainly as a single PPT skill. The next version should become a durable personal skill library that can host additional research, analysis, and communication skills over time.

## 2. Goals

1. Rename the repository from `Huazi-ppt-skill` to `lex-ai-research-skills`.
2. Position the repository as a personal, installable library of reusable AI research skills.
3. Publish a complete English `README.md` and Chinese `README.zh-CN.md`.
4. Explain the research philosophy, skill boundaries, workflow, installation, invocation, and outputs in enough detail for a new visitor to understand and use the repository.
5. Show real PPT output from the embodied-data industry research deck in a dedicated case gallery.
6. Preserve both existing skills as independently callable units.
7. Create a directory structure that can accept more skills without another repository-wide reorganization.

## 3. Non-Goals

- Do not merge the two skills into one.
- Do not change the operational behavior of either skill as part of the repository presentation upgrade.
- Do not turn the README into a tutorial for PowerPoint programming.
- Do not place case screenshots throughout explanatory README sections.
- Do not add claims about external inspiration or explicitly reference another creator's repository style.
- Do not publish the full source PPTX in this change unless separately requested.
- Do not introduce a website, documentation generator, package registry, or automated installer.

## 4. Product Positioning

The repository should lead with a clear point of view:

> Research is a system, not a document.

The supporting message is that industrial research, technical analysis, evidence organization, and executive communication can be encoded as reusable agent skills rather than recreated from scratch for every project.

The repository has two simultaneous identities:

- **Personal research operating system:** a growing collection of Lex's methods for producing rigorous research outputs.
- **Installable skill library:** a practical repository that Codex users can clone, install, and invoke directly.

The tone should be confident, specific, and useful. It should describe what the skills actually do, where they fit, and what output quality they enforce. It should avoid inflated branding language and generic AI claims.

## 5. Repository Information Architecture

The target structure is:

```text
lex-ai-research-skills/
├── README.md
├── README.zh-CN.md
├── assets/
│   └── cases/
│       └── embodied-data-industry/
│           ├── cover.png
│           ├── industry-chain.png
│           ├── data-factory-workflow.png
│           └── outlook-2026-2028.png
├── skills/
│   ├── huawei-insight-deck/
│   │   ├── SKILL.md
│   │   ├── agents/
│   │   ├── references/
│   │   └── scripts/
│   └── tech-research-deck/
│       ├── SKILL.md
│       └── references/
└── docs/
    └── superpowers/
        └── specs/
```

The existing root-level `SKILL.md`, `agents/`, `references/`, and `scripts/` belong to `huawei-insight-deck` and will move together into `skills/huawei-insight-deck/`.

The `tech-research-deck` directory remains under `skills/`. Its content and trigger name remain unchanged.

The local brainstorming workspace `.superpowers/` is not repository content and must not be committed. It should be excluded from future Git status noise.

## 6. Bilingual README Model

### 6.1 Language Navigation

Both README files begin with a compact language switch:

- English: `README.md`
- 简体中文: `README.zh-CN.md`

The two files should have equivalent information architecture and meaning. They do not need to be literal sentence-by-sentence translations; each should read naturally in its language.

### 6.2 README Section Order

Both READMEs use the following order:

1. Repository title and one-line positioning
2. Language switch
3. Core philosophy and short introduction
4. Skill matrix
5. Why this repository exists
6. How the skill system works
7. Quick start
8. Installation
9. Usage examples
10. Case gallery
11. Repository structure
12. Quality principles
13. Roadmap or extension direction
14. License/status note only if supported by repository files

The first viewport should quickly answer:

- What is this repository?
- Who is it for?
- What can I install today?
- What makes the outputs different from generic AI-generated slides?

## 7. Skill Presentation

### 7.1 Skill Matrix

The README should compare skills using stable fields:

| Skill | Purpose | Best for | Main output |
| --- | --- | --- | --- |
| `huawei-insight-deck` | Convert a clear argument into a rigorous executive slide | Market sizing, comparisons, technical routes, executive one-pagers | Editable restrained-red PowerPoint pages |
| `tech-research-deck` | Structure a technology domain from source material and web research | Architecture, route evolution, key modules, cases, trends, compute implications | Complete reading-style technology research deck |

Each skill then gets a richer description covering:

- Trigger conditions
- Inputs it can use
- Research or layout work it performs
- Output characteristics
- Relationship to the other skill
- A short invocation example

### 7.2 Skill Boundary

The README must make the division explicit:

- `tech-research-deck` organizes the research question, evidence, architecture, route comparison, cases, and trends.
- `huawei-insight-deck` converts a settled argument into a consistent, editable, executive-facing visual page.
- They can be used separately or sequentially.

This prevents visitors from assuming that one is merely a theme pack for the other.

## 8. How It Works

The workflow section should show a compact research pipeline:

```text
Source material
  -> research framing
  -> evidence and source verification
  -> architecture and route decomposition
  -> page-level claims
  -> slide construction
  -> render and visual QA
  -> editable PPT output
```

The explanation should emphasize four system properties:

1. **Claim-first structure:** each page communicates one defensible conclusion.
2. **Evidence traceability:** important numbers and factual claims retain sources and definitions.
3. **Comparable dimensions:** routes, companies, and scenarios are compared using consistent fields.
4. **Editable delivery:** outputs remain native PowerPoint content whenever practical.

## 9. Installation And Invocation

The target installation flow should support the new multi-skill structure:

```bash
git clone https://github.com/hoilex0421-star/lex-ai-research-skills.git
mkdir -p ~/.codex/skills
ln -s "$(pwd)/lex-ai-research-skills/skills/huawei-insight-deck" ~/.codex/skills/huawei-insight-deck
ln -s "$(pwd)/lex-ai-research-skills/skills/tech-research-deck" ~/.codex/skills/tech-research-deck
```

The README should also include a direct-copy installation option for users who do not want symbolic links.

Invocation examples:

```text
$tech-research-deck
基于这篇文章和互联网研究，梳理具身数据产业的架构、商业模式、代表玩家和未来趋势，并生成一份研究型 PPT。
```

```text
$huawei-insight-deck
把已有研究结论整理成一页市场空间与竞争格局洞察页，所有关键数字标注来源。
```

Commands and paths must be verified after the repository rename and directory migration.

## 10. Dedicated Case Gallery

### 10.1 Placement Rule

All real PPT screenshots appear only in the dedicated **Case Gallery / 案例展示** section.

The normal README body may describe capabilities and outputs in text, but it must not insert case screenshots into philosophy, workflow, skill descriptions, installation, or usage sections.

### 10.2 Case

The initial gallery features:

**Embodied Data Industry Research: From Data Factories to Physical AI Infrastructure**  
**具身数据产业研究：从数据工厂到物理 AI 基础设施**

The gallery uses four selected slides from:

`具身数据产业研究-从数据工厂到物理AI基础设施-v0.1.pptx`

Selected images:

1. Cover: establishes the report topic and visual identity.
2. Industry chain and data layer: demonstrates system-level industry mapping.
3. Data factory workflow: demonstrates process and operational decomposition.
4. 2026-2028 outlook: demonstrates forward-looking synthesis and timeline communication.

Images should be exported or copied as repository-friendly PNG files under:

`assets/cases/embodied-data-industry/`

The gallery should use a clean two-column layout where GitHub rendering allows it, with short captions explaining what each page demonstrates. It should not repeat the same image elsewhere in either README.

The gallery should identify the deck as a real output example, not as a downloadable source deck.

## 11. Copy Rules

README copy should follow these rules:

- Use direct statements rather than unnecessary quotation marks.
- Avoid wrapping ordinary emphasis phrases in Chinese or English quotation marks.
- Use `洞察` for the top conclusion label when describing `tech-research-deck` slide conventions.
- Keep `核心判断` out of screenshots captions and new explanatory copy when it refers to that top label.
- Use concrete descriptions such as architecture map, route comparison, evidence traceability, and editable PowerPoint.
- Avoid unverified superlatives, adoption claims, or performance claims.
- Do not mention or imply that the repository's expression style was copied from a named external project.

These copy rules apply to both language versions.

## 12. Compatibility And Migration

Repository rename:

- Old: `hoilex0421-star/Huazi-ppt-skill`
- New: `hoilex0421-star/lex-ai-research-skills`

GitHub normally redirects repository links after a rename, but all README commands and the local `origin` remote should be updated to the new canonical URL.

Skill names remain stable:

- `$huawei-insight-deck`
- `$tech-research-deck`

Users with the old repository cloned directly into `~/.codex/skills/huawei-insight-deck` can continue using that local copy, but the new documented installation should clone the library once and link each child skill independently.

No trigger names, YAML names, or internal skill references should be renamed as part of the repository rename.

## 13. Implementation Scope

The implementation phase will:

1. Move the root-level `huawei-insight-deck` files into `skills/huawei-insight-deck/`.
2. Preserve `skills/tech-research-deck/` and verify its referenced files remain valid.
3. Add the four selected case PNGs under `assets/cases/embodied-data-industry/`.
4. Rewrite `README.md` in English.
5. Add `README.zh-CN.md` in Chinese.
6. Exclude `.superpowers/` from repository tracking.
7. Rename the GitHub repository to `lex-ai-research-skills`.
8. Update the local Git remote to the new canonical URL.
9. Commit and push the repository changes.

## 14. Validation Checklist

### Repository

- The GitHub repository name is `lex-ai-research-skills`.
- The local `origin` points to the renamed repository.
- The default branch remains `main`.
- `.superpowers/` is not tracked.
- No existing user content is accidentally deleted.

### Skill Integrity

- `skills/huawei-insight-deck/SKILL.md` exists and declares `name: huawei-insight-deck`.
- `skills/tech-research-deck/SKILL.md` exists and declares `name: tech-research-deck`.
- Supporting references, scripts, and agent files resolve from their new locations.
- Both documented skill invocation names remain unchanged.
- The `tech-research-deck` copy rules still require direct body copy and the `洞察` label.

### README

- `README.md` is complete English.
- `README.zh-CN.md` is complete Chinese.
- Language links work in both directions.
- The skill matrix, philosophy, workflow, quick start, installation, examples, and structure sections are present.
- Installation commands use the renamed repository and correct child-skill paths.
- No explicit reference to a named external README or project style appears.

### Gallery

- All four PNG files exist and render on GitHub.
- Images appear only in the dedicated gallery section.
- Each image has a concise, meaningful caption.
- Image paths use repository-relative links and match file name case exactly.
- No local absolute paths appear in the published README.

### Final Verification

- Git status is clean after commit and push.
- The renamed remote repository loads successfully.
- The default GitHub README renders without broken images or broken language links.
- A fresh clone exposes both skill directories in the documented locations.

