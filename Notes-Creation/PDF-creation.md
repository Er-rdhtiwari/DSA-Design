SOURCE_FOLDER="Notes"
PDF_OUTPUT_FOLDER="${SOURCE_FOLDER}/pdfs"
SOURCE_FILE_PATTERN="Day*.md"
EXPECTED_FILE_COUNT=11
VALIDATION_REPORT="${PDF_OUTPUT_FOLDER}/pdf-validation-report.md"

Create one PDF for each Markdown note matching `${SOURCE_FILE_PATTERN}` inside `${SOURCE_FOLDER}`.

## Requirements

1. Treat the existing Markdown files as the only source of truth.
2. Copy the content exactly. Do not rewrite, summarize, correct, add, remove, or reorder anything.
3. Do not modify the original Markdown files.
4. Create `${PDF_OUTPUT_FOLDER}` if it does not exist.
5. Save all generated PDFs inside `${PDF_OUTPUT_FOLDER}`.
6. Preserve the source filename and change only the extension:

```text
day-01.md → day-01.pdf
```

7. Use A4 portrait formatting:

* Body font: 11 pt
* H1: 16 pt bold
* H2: 14 pt bold
* H3: 12 pt bold
* Code blocks and tables: 10.5 pt
* Line spacing: 1.3
* Margins: 18 mm on all sides
* Black text on a white background
* Page numbers only
* Do not add headers, footers, titles, watermarks, or extra content

8. Preserve all:

* headings
* paragraphs
* lists
* tables
* code blocks
* ASCII diagrams
* links
* special characters
* blank-line structure
* section order

9. Ensure no content is:

* clipped
* missing
* duplicated
* reordered
* rendered outside the page margins

10. Fix only PDF layout and rendering issues. Never change the Markdown source content.

11. Process and validate each Markdown file separately.

12. Create `${VALIDATION_REPORT}` containing:

* source Markdown filename
* generated PDF filename
* PDF page count
* generation status
* validation status
* formatting issue detected
* formatting adjustment applied
* confirmation that source content was unchanged

13. Validate that:

* every matching Markdown file has exactly one PDF
* every PDF is readable
* headings, tables, code blocks, diagrams, and special characters render correctly
* no source file was modified
* no generated PDF is empty
* generated filenames match their source filenames

14. If the number of matching Markdown files differs from `${EXPECTED_FILE_COUNT}`, record the difference in `${VALIDATION_REPORT}` and process all matching files without inventing or deleting files.

Follow this order:

1. Discover all matching Markdown files
2. Record their names and checksums
3. Create `${PDF_OUTPUT_FOLDER}`
4. Generate each PDF separately
5. Validate each generated PDF
6. Compare the source-file checksums to confirm they are unchanged
7. Create `${VALIDATION_REPORT}`
8. Report the final result

At the end, confirm:

* number of Markdown files discovered
* number of PDFs generated
* number of successfully validated PDFs
* validation report location
* whether all original Markdown files remained unchanged
* any unresolved rendering issues
