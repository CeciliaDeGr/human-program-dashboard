# Textbook Lesson Blueprint — Format Reference

Use this with **textbook-lesson-blueprint.html** when creating new lesson content. The HTML file shows the same content rendered with every format; this doc lists each format type and how to apply it.

**Rules:** No horizontal lines or dividers. Use spacing, boxes, and indentation only. Prefer left-aligned body text; use center only for chapter title and equations.

---

## Box themes and colors (by logic)

Colors are assigned **by role**: same role = same color. Use the CSS variables in the HTML file.

| Role | Theme | Variable | Hex | Used for |
|------|--------|----------|-----|----------|
| **Framing** | Light grey | `--box-framing` | #F3F7FC | Learning objectives, Key Points (summary) |
| **Core** | Warm orange | `--box-core` | #FFF6ED | Definition (key term box), Concept |
| **Application** | Light blue | `--box-application` | #F1FBFF | Examples (worked example + applied examples) |
| **Interest** | Lavender | `--box-interest` | #E9E5FF | Did you know |

**Logic:** Framing = intro and recap (grey). Core = definitions and concepts (warm). Application = examples (pink). Interest = aside / extra (blue).

---

## 1. Chapter number

- **Purpose:** Small label above the main chapter title.
- **HTML:** `<p class="chapter-number">Chapter 4</p>`
- **CSS:** Smaller font, bold, centered; margin below only.

## 2. Chapter title

- **Purpose:** Main chapter heading.
- **HTML:** `<h1 class="chapter-title">Energy and Efficiency in Cells</h1>`
- **CSS:** Large, bold, centered.

## 3. Learning objectives box

- **Purpose:** Bulleted list of objectives in a light box.
- **HTML:** Wrapper `div.learning-objectives`, optional `.box-title`, then `<ul>` with `<li>` items.
- **CSS:** Background, subtle border, padding; list left-aligned with disc bullets.

## 4. Section heading (e.g., 1., 2., 3.)

- **Purpose:** Numbered section title.
- **HTML:** `<h2 class="section-heading">1. What Is Energy?</h2>`
- **CSS:** Medium-large, bold; margin-top for separation from previous section.

## 5. Body paragraph

- **Purpose:** Normal running text.
- **HTML:** `<p class="body-text">...</p>`
- **Variants:** Add `text-justify` or `text-center` for alignment.
- **CSS:** Default left-aligned; optional justify/center.

## 6. Inline bold (key terms)

- **Purpose:** First use of a defined term.
- **HTML:** `<span class="term">Energy</span>`
- **CSS:** font-weight: 700.

## 7. Italic (emphasis, quotes)

- **Purpose:** Emphasis or quoted phrase.
- **HTML:** `<span class="emphasis">"Life depends on..."</span>`
- **CSS:** font-style: italic.

## 8. Bullet list

- **Purpose:** Unordered list, indented.
- **HTML:** `<ul class="bullet-list"><li>...</li></ul>`
- **CSS:** padding-left for indent, disc bullets, spacing between items.

## 9. Pull quote (blockquote)

- **Purpose:** Short quote, set off from body.
- **HTML:** `<blockquote class="pull-quote"><span class="emphasis">"..."</span></blockquote>`
- **CSS:** Italic, left margin/indent, optional left border (no full horizontal line).

## 10. Key term box

- **Purpose:** Term name + definition in a box.
- **HTML:** `div.key-term-box`, inside: `.term-name` (term), `.term-def` (definition with hanging indent).
- **CSS:** Same box style as other callouts; definition uses negative text-indent + margin-left for hang.

## 11. Callout boxes — colors by role

See **Box themes and colors (by logic)** above for the full table. Use `--box-framing`, `--box-core`, `--box-application`, `--box-interest` in CSS.

- **HTML:** `div.callout-box concept-box` (or `example-box` or `did-you-know-box`), plus `.box-type-label` (“Concept”, “Example”, “Did you know?”), then `.callout-title`, then `.callout-body` (or worked-example content).
- **CSS:** Use the variables above; no border; 12px radius.

## 12. Centered equation / formula

- **Purpose:** Single equation on its own line, centered.
- **HTML:** `<div class="equation-block"><code>ATP → ADP + P + energy</code></div>`
- **CSS:** text-align: center; code in serif to match body.

## 13. Worked example (inside a callout box)

- **Purpose:** Step-by-step solution in a single box; each step is a distinct block so it’s easy to parse.
- **HTML:** Use `div.callout-box example-box` with `.callout-title` “Worked Example”, then body text, then for each step: `div.step-block` containing `span.step-num` (“Step 1”, “Step 2”), `p.step-desc` (instruction, no em dash), and `p.equation-inline` for the formula.
- **CSS:** `.step-block` has left border and light background so steps are visually separate; `.step-num` is bold, smaller; `.step-desc` and `.equation-inline` follow.

## 14. Section summary (Key Points)

- **Purpose:** Bulleted summary at end of section.
- **HTML:** `div.section-summary`, `.summary-title` (“Section Summary” / “Key Points”), then `<ul>` with `<li>`.
- **CSS:** Same list style as learning objectives.

## 15. Vocabulary

- **Purpose:** Term (bold) + definition on next line, hanging indent.
- **HTML:** `div.vocabulary`, `.vocab-title`, then repeated `.vocab-item` with `.vocab-term` and `.vocab-def`.
- **CSS:** `.vocab-def` uses same hanging-indent pattern as key-term-box.

## 16. Tables — content scenarios

Use `.table-wrap` around each table. Optional: `.table-caption`, `.table-footnote`, `.textbook-table.zebra`, `.num` (right-align).

| Scenario | Use case | Columns | Example |
|----------|----------|---------|---------|
| **Comparison / reference** | Numbers + notes, multi-row | 3–4 (e.g. Process, Value, Notes) | Efficiency of processes; add `.zebra` for alternating rows |
| **Definition / key terms** | Term + definition in table form | 2 (Term, Role or Definition) | Key molecules, vocabulary in table |
| **Data with units** | Numeric data, right-align numbers | 2+ with `.num` on number column(s) | Measurements, ranges, percentages |
| **Simple list in table** | Two related columns | 2 | Before/after, input/output, cause/effect |
| **With caption and footnote** | Cited or numbered table | Use `.table-caption` above, `.table-footnote` below | Table 1. …; footnote for source or caveat |

- **HTML:** `div.table-wrap` → optional `p.table-caption`, `table.textbook-table` (add `.zebra` for striping), optional `p.table-footnote`. Use `th.num` / `td.num` for right-aligned numeric cells.
- **CSS:** Header background, row borders, optional zebra striping.

---

## Checklist for new lessons

- [ ] Chapter title at top
- [ ] Learning objectives box
- [ ] Section headings (1., 2., 3., …)
- [ ] Body text with **term** and *emphasis* where needed
- [ ] Bullet lists where appropriate
- [ ] Pull quote if needed (no horizontal rule)
- [ ] Key term boxes (term + definition only; no label above)
- [ ] Callout boxes with title inside (Concept, Example, Did You Know, Worked Example); content as normal paragraphs, no nested boxes
- [ ] Equations in equation-block (standalone) or equation-inline (inside callout)
- [ ] Section summary (Key Points)
- [ ] Tables if needed (caption, footnote, .zebra, .num)
- [ ] Vocabulary list at end

No horizontal lines or dividers in main layout; tables may use light row borders.
