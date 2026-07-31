# PDF Validation Report

## Collection Result

- Source folder: `project`
- Source pattern: `*.md` (top-level files in `project`)
- Expected Markdown file count: 3
- Discovered Markdown file count: 3
- Count difference: 0
- Note PDFs generated: 3
- Index PDFs generated: 1
- Total PDFs generated: 4
- Successfully validated note PDFs: 3 of 3
- Index validation: PASS
- Unresolved rendering issues: None
- Note filename convention: zero-padded `day-01` through `day-03` prefixes with lowercase kebab-case; the mandated `Day-00-Notes-Index.pdf` name is retained

## Source Inventory Recorded Before Generation

| Source Markdown filename | Source lines | Initial SHA-256 | Mermaid block inventory |
|---|---:|---|---|
| `day-01-dpdk-final.md` | 355 | `45f8b2f96516ea6ceec3344fd7b21af38d1d7b658a58c6f333cc7ee0419e7cff` | 0 blocks |
| `day-02-final-dpdk-benchops-copilot.md` | 674 | `cdb0eebbb16335d6bee83ecc760bced30f97c7511c39d9bea091cc0b36b936b2` | 0 blocks |
| `day-03-okyc-final.md` | 198 | `4ddf4921a45dbc4cafb491f27d1ff1535696fcb3580933a510ec37fae547948d` | 0 blocks |

## Per-File Generation and Validation

| Source Markdown filename | Generated PDF filename | PDF pages | Generation status | Validation status | Formatting issue detected | Formatting adjustment applied | Mermaid rendering mode | Diagram page orientation | Visual reflow | Source unchanged |
|---|---|---:|---|---|---|---|---|---|---|---|
| `day-01-dpdk-final.md` | `day-01-dpdk-final.pdf` | 8 | SUCCESS | PASS | No final defect. The source contains deliberate multi-blank-line runs. | Preserved the extra blank-line runs as vertical source spacing; retained nested-list structure with CommonMark rendering. | Not applicable: 0 Mermaid blocks | Not applicable; all pages A4 portrait | None | YES |
| `day-02-final-dpdk-benchops-copilot.md` | `day-02-final-dpdk-benchops-copilot.pdf` | 13 | SUCCESS | PASS | None | No content-specific adjustment required; CommonMark nesting and source block order retained. | Not applicable: 0 Mermaid blocks | Not applicable; all pages A4 portrait | None | YES |
| `day-03-okyc-final.md` | `day-03-okyc-final.pdf` | 5 | SUCCESS | PASS | Initial visual QA found that the first parser restarted the second numbered captcha phase at `1.` and flattened its nested bullets. | Re-rendered with a CommonMark parser; the source `1.`/`2.` sequence and all nested bullet levels now render correctly. | Not applicable: 0 Mermaid blocks | Not applicable; all pages A4 portrait | None | YES |

## Per-File Validation Evidence

### `day-01-dpdk-final.pdf`

- Readability: PASS
- Nonempty PDF and nonempty pages: PASS
- Filename mapping: PASS (`day-01-dpdk-final.md` → `day-01-dpdk-final.pdf`)
- A4 portrait, 18 mm content bounds, and page-number-only footer: PASS on all 8 pages
- Visible-text token stream matches the source: PASS
- Source lines present in source order with no missing or duplicated content: PASS
- Headings: PASS (13 of 13 detected)
- Lists and nested lists: PASS
- Inline code and special characters: PASS (`–`, `’`, `“`, `”`, `→`)
- Tables, fenced code blocks, ASCII diagrams, links, and Mermaid blocks: not present in this source
- PDF SHA-256: `8e34fbe6f5f0a1621fb68c3dbc6b891dfa4637ab28619e4dc24dddcae74d2b62`

### `day-02-final-dpdk-benchops-copilot.pdf`

- Readability: PASS
- Nonempty PDF and nonempty pages: PASS
- Filename mapping: PASS (`day-02-final-dpdk-benchops-copilot.md` → `day-02-final-dpdk-benchops-copilot.pdf`)
- A4 portrait, 18 mm content bounds, and page-number-only footer: PASS on all 13 pages
- Visible-text token stream matches the source: PASS
- Source lines present in source order with no missing or duplicated content: PASS
- Headings: PASS (58 of 58 detected)
- Lists and nested lists: PASS
- Special characters: PASS (`–`, `’`, `“`, `”`)
- Tables, fenced code blocks, ASCII diagrams, links, and Mermaid blocks: not present in this source
- PDF SHA-256: `3d8a6ada83014fd60d310b8b0891eec827c52b7eaf1c719b07d724fbc9d7f0f7`

### `day-03-okyc-final.pdf`

- Readability: PASS
- Nonempty PDF and nonempty pages: PASS
- Filename mapping: PASS (`day-03-okyc-final.md` → `day-03-okyc-final.pdf`)
- A4 portrait, 18 mm content bounds, and page-number-only footer: PASS on all 5 pages
- Visible-text token stream matches the source: PASS
- Source lines present in source order with no missing or duplicated content: PASS
- Headings: PASS (20 of 20 detected)
- Ordered and nested lists: PASS, including captcha phases `1.` and `2.`
- Inline code and special characters: PASS (`×`, `–`, `—`, `’`, `“`, `”`, `➜`)
- Tables, fenced code blocks, ASCII diagrams, links, and Mermaid blocks: not present in this source
- PDF SHA-256: `3e8cd6e9a257fe91415ce19f8a0ecc96af3cebf2ad62db6280e2f9e5426ba9dc`

## Index PDF

- PDF filename: `Day-00-Notes-Index.pdf`
- Generation status: SUCCESS
- PDF pages: 4
- Validation status: PASS
- Reference followed: `output/pdf/Day-00-Notes-Index.pdf`
- Structure validated: cover summary, source-derived recommended path, topic grouping, note entries, quick locator, page counts, and collection summary
- Content provenance: project titles, domains, headings, filenames, source-line counts, and PDF page counts were derived from the generated collection; no note topic content was invented
- Collection totals: 3 Markdown files, 1,227 source lines, and 26 note-PDF pages
- Page geometry/readability: PASS; all pages are readable A4 portrait pages with no clipped or overlapping index content
- Required note entries and page counts: PASS
- PDF SHA-256: `c88da0fa857c80bcaa0c6a9606426d6fff27d3f21af9c456794e7f6f14736056`

## Source Integrity Check After Generation

| Source Markdown filename | Final SHA-256 | Matches initial checksum | Modified by generation |
|---|---|---|---|
| `day-01-dpdk-final.md` | `45f8b2f96516ea6ceec3344fd7b21af38d1d7b658a58c6f333cc7ee0419e7cff` | YES | NO |
| `day-02-final-dpdk-benchops-copilot.md` | `cdb0eebbb16335d6bee83ecc760bced30f97c7511c39d9bea091cc0b36b936b2` | YES | NO |
| `day-03-okyc-final.md` | `4ddf4921a45dbc4cafb491f27d1ff1535696fcb3580933a510ec37fae547948d` | YES | NO |

All original Markdown files remained unchanged.
