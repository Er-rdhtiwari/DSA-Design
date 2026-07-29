# PDF Validation Report

## Batch summary

| Field | Result |
| --- | --- |
| Source folder | `Notes` |
| Source file pattern | `Day*.md` |
| Expected matching Markdown files | 11 |
| Discovered matching Markdown files | 11 |
| Difference from expected | 0 |
| Matching files processed | 11 |
| PDFs generated | 11 |
| PDFs successfully validated | 11 |
| Total PDF pages | 425 |
| Batch generation status | Success |
| Batch validation status | Passed |
| Original Markdown files unchanged | Yes |
| Unresolved rendering issues | None |

## Source discovery and checksum record

| Source Markdown filename | Initial SHA-256 | Final SHA-256 | Source unchanged |
| --- | --- | --- | --- |
| `Day 1 — Vanilla RAG End to End.md` | `685697815dc0c1309ecec14fb02b34290d1de6ac9c8d8cbc6dcd24710879e341` | `685697815dc0c1309ecec14fb02b34290d1de6ac9c8d8cbc6dcd24710879e341` | Yes |
| `Day 10 DSA Core II Patterns.md` | `f5eec8d2d49ea7d9225cf7e1d0be077a029fa2bc80553ed869ad9c20b2ca505e` | `f5eec8d2d49ea7d9225cf7e1d0be077a029fa2bc80553ed869ad9c20b2ca505e` | Yes |
| `Day 3 — LangChain End to End.md` | `1ec63f0f7a2872d19bd3956b5f85323551aa8e15573a4d19699fa8519e9e6343` | `1ec63f0f7a2872d19bd3956b5f85323551aa8e15573a4d19699fa8519e9e6343` | Yes |
| `Day 6 — Interrelationship of RAG.md` | `8eb1dc6bf536b18d876898049a39831112309776d9184ba62d6edef7651e8040` | `8eb1dc6bf536b18d876898049a39831112309776d9184ba62d6edef7651e8040` | Yes |
| `Day 7 Revision: The Complete Production AI Stack.md` | `9fbe1d500b5db8a2c1d9a34341a88e157afe06ba17de074446bf72b2e0fc7a97` | `9fbe1d500b5db8a2c1d9a34341a88e157afe06ba17de074446bf72b2e0fc7a97` | Yes |
| `Day 8 System Design Interview Prep.md` | `785fce3134257acf4331fe487932936ff4b9e2f08ced14a31429e3fb5b24bf22` | `785fce3134257acf4331fe487932936ff4b9e2f08ced14a31429e3fb5b24bf22` | Yes |
| `Day 9 DSA Core I Patterns.md` | `c757a71cfcdbd75c898f6eb8502063e5976807d4c15627ed76126b55be83a2db` | `c757a71cfcdbd75c898f6eb8502063e5976807d4c15627ed76126b55be83a2db` | Yes |
| `Day-11 GenAI System Architecture.md` | `1899c02e1572393791b05404294100b5066b24737712762215e4bc0ee4222d42` | `1899c02e1572393791b05404294100b5066b24737712762215e4bc0ee4222d42` | Yes |
| `Day:2 LlamaIndex Foundations and Workflows.md` | `9ece8bd1ec8daf7754d5c19757f087a3428a20506e2ae6d0aab5fe75780bbd38` | `9ece8bd1ec8daf7754d5c19757f087a3428a20506e2ae6d0aab5fe75780bbd38` | Yes |
| `Day:4 LangGraph AI Workflows.md` | `4d7a3f3007b39222fd13aa1540f1bb09ee6e4a64578dd412f57f7ba4994c53bb` | `4d7a3f3007b39222fd13aa1540f1bb09ee6e4a64578dd412f57f7ba4994c53bb` | Yes |
| `Day:5 MCP End-to-End Overview.md` | `abf7bd3a929fe26a76cda519bedf8a4f060bb2d89554dbb35102bc09e04a982c` | `abf7bd3a929fe26a76cda519bedf8a4f060bb2d89554dbb35102bc09e04a982c` | Yes |

## Per-file generation and validation

| Source Markdown filename | Generated PDF filename | Pages | Generation status | Validation status | Formatting issue detected | Formatting adjustment applied | Source content unchanged |
| --- | --- | ---: | --- | --- | --- | --- | --- |
| `Day 1 — Vanilla RAG End to End.md` | `Day 1 — Vanilla RAG End to End.pdf` | 51 | Success | Passed | 12 fenced blocks contained lines wider than the usable 10.5 pt code width; one fenced block was taller than one A4 content area; one table required width-constrained layout. | Wrapped only the affected long-line fenced blocks, paginated the overheight block with continued borders, and constrained the table to the content width. | Yes |
| `Day 10 DSA Core II Patterns.md` | `Day 10 DSA Core II Patterns.pdf` | 31 | Success | Passed | Four multi-column tables required margin-safe cell wrapping. | Constrained tables to the content width and wrapped cell content without changing text. | Yes |
| `Day 3 — LangChain End to End.md` | `Day 3 — LangChain End to End.pdf` | 27 | Success | Passed | Six fenced blocks contained long prose lines, including one 503-character line; one table required width-constrained layout. | Wrapped only affected fenced lines at the page margin and constrained the table to the content width. | Yes |
| `Day 6 — Interrelationship of RAG.md` | `Day 6 — Interrelationship of RAG.pdf` | 40 | Success | Passed | One fenced block was taller than one A4 content area; five tables required margin-safe wrapping. | Paginated the overheight fenced block with continued borders and constrained tables to the content width. | Yes |
| `Day 7 Revision: The Complete Production AI Stack.md` | `Day 7 Revision: The Complete Production AI Stack.pdf` | 51 | Success | Passed | One fenced JSON block contained an overwidth line; seven tables required width-constrained layout. | Wrapped only the affected JSON line at the page margin and constrained tables to the content width. | Yes |
| `Day 8 System Design Interview Prep.md` | `Day 8 System Design Interview Prep.pdf` | 40 | Success | Passed | One fenced block contained an overwidth line; two fenced blocks exceeded one-page height; six tables required margin-safe wrapping. | Wrapped the affected line, paginated the two overheight blocks with continued borders, and constrained tables to the content width. | Yes |
| `Day 9 DSA Core I Patterns.md` | `Day 9 DSA Core I Patterns.pdf` | 30 | Success | Passed | Three multi-column tables required margin-safe cell wrapping. | Constrained tables to the content width and wrapped cell content without changing text. | Yes |
| `Day-11 GenAI System Architecture.md` | `Day-11 GenAI System Architecture.pdf` | 50 | Success | Passed | Two fenced blocks were taller than one A4 content area; one table required width-constrained layout. | Paginated only the overheight fenced blocks with continued borders and constrained the table to the content width. | Yes |
| `Day:2 LlamaIndex Foundations and Workflows.md` | `Day:2 LlamaIndex Foundations and Workflows.pdf` | 34 | Success | Passed | Ten fenced blocks contained lines wider than the usable 10.5 pt code width, including one 365-character line. | Wrapped only affected fenced lines at the page margin while preserving every character and explicit newline. | Yes |
| `Day:4 LangGraph AI Workflows.md` | `Day:4 LangGraph AI Workflows.pdf` | 33 | Success | Passed | Five fenced blocks contained overwidth prose lines, including one 434-character line; one fenced block exceeded one-page height. | Wrapped only affected fenced lines and paginated the overheight block with continued borders. | Yes |
| `Day:5 MCP End-to-End Overview.md` | `Day:5 MCP End-to-End Overview.pdf` | 38 | Success | Passed | Three multi-column tables required margin-safe cell wrapping. | Constrained tables to the content width and wrapped cell content without changing text. | Yes |

## PDF checksums

| Generated PDF filename | SHA-256 |
| --- | --- |
| `Day 1 — Vanilla RAG End to End.pdf` | `de59a44b5eaa4ad9f492ea3007ac759d2c642bf8d341f52430bbf31fb22adfbc` |
| `Day 10 DSA Core II Patterns.pdf` | `1d6a20b29b0a589db0059ea410ecd196deaa092860a3227448698955a19c4db7` |
| `Day 3 — LangChain End to End.pdf` | `d185fac05ca9e0d4ebccd8073c0503a16499c0eecdeac1797774011cf5450903` |
| `Day 6 — Interrelationship of RAG.pdf` | `912babbaaf68a776a7feef2e40c6dd6603d451c89ed37912d2bf2e0e9cfd5eec` |
| `Day 7 Revision: The Complete Production AI Stack.pdf` | `baa49216d21e3f85ea2f224ce3951afd95076d7a220fc7e832c3cc529151b9b4` |
| `Day 8 System Design Interview Prep.pdf` | `ddbf2440275d6f4a5bf1aeb5f0895b5b73d53e69d8fbf128e81e6b63aa94078a` |
| `Day 9 DSA Core I Patterns.pdf` | `ec61d6f11b0cd5d28c1ddfd08010ac1c941c19d841b532271908edb1bebbea65` |
| `Day-11 GenAI System Architecture.pdf` | `65e5d6e3f44ea7a040ad141f6ddc98b83d810999943a6ed3aabdac596d0632e5` |
| `Day:2 LlamaIndex Foundations and Workflows.pdf` | `241da38b71962840dad63798edad976a37158b3163ce186aab4c3fc96010c030` |
| `Day:4 LangGraph AI Workflows.pdf` | `f6dfe844e1fb21121332d21fb2e39cd1a92c14db491456b39d6a86a6be61d582` |
| `Day:5 MCP End-to-End Overview.pdf` | `26a618496c3f18e5a7f7fb0b516bb3d81c9ccfab635b3496a914f0f17cab777d` |

## Validation details

| Validation check | Result |
| --- | --- |
| Exactly one PDF exists for every matching Markdown file | Passed: 11 matching sources and 11 correspondingly named PDFs |
| Generated filenames match source filenames with only the extension changed | Passed |
| PDF readability, encryption, and non-empty checks | Passed for all 11 PDFs |
| Page size and orientation | Passed: every page is A4 portrait, 595.276 × 841.890 pt, rotation 0 |
| Margins | Passed: no body text, table, code block, diagram, or border outside the 18 mm content boundary |
| Page numbering | Passed: sequential page numbers only; no other header or footer content |
| Required typography | Passed: body 11 pt; H1 16 pt bold; H2 14 pt bold; H3 12 pt bold; code blocks and tables 10.5 pt |
| Line spacing | Passed: 1.3 |
| Color and background | Passed: black text on white |
| Embedded fonts | Passed for all PDFs |
| Headings, paragraphs, lists, and section order | Passed |
| Code blocks and ASCII diagrams | Passed: all 1,247 fenced blocks rendered and visually reviewed |
| Tables | Passed: all 31 tables rendered without clipping or overflow |
| Links | Passed: all 96 rendered links have matching PDF URI annotations; wrapped links may use multiple annotation rectangles |
| Special characters | Passed: visible Unicode character counts matched independently for every file |
| Content presence and order | Passed: 14,912 semantic fragments found in source order |
| Missing or duplicated content | Passed: 5,017 long-fragment occurrence checks found no omission or duplication |
| Renderer warnings and layout issues | Passed: zero final warnings and zero layout-boundary violations |
| Raster readability | Passed: all 425 pages rendered to images; no blank pages or edge clipping |
| Visual review | Passed: all 17 contact sheets and representative full-size table, code, diagram, wrapped-line, multi-page-block, and final pages reviewed |
| Source modification check | Passed: every initial and final SHA-256 checksum is identical |

## Final status

Generation and validation completed successfully for all 11 Markdown files matching `Day*.md`. No unresolved rendering issues remain, and all original Markdown files remained unchanged.
