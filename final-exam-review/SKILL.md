---
name: final-exam-review
description: Create high-yield final exam review packs from course materials, lecture slides, PDFs, Word documents, assignments, past exams, and practice questions. Use when a student wants Codex or another agent to convert study materials into a detailed exam-focused outline, chapter practice bank, and mock exams, with MarkItDown preferred but optional for source conversion.
---

# Final Exam Review

## Overview

Use this skill to turn messy course materials into an exam-focused review package that a student can study from directly. Optimize for final-exam preparation: high-frequency concepts, problem patterns, mistakes to avoid, and enough practice to self-test.

Default to Chinese output unless the user asks otherwise. Preserve important English technical terms beside Chinese explanations when the source materials use them.

For the final output structure, load `references/review-package-template.md`.

## Intake

Collect only the information needed to build the review package:

- Subject or course name.
- Exam scope, chapters, or excluded topics, if known.
- Course materials: PPT/PPTX, DOC/DOCX, PDF, Markdown, HTML, XLSX, ZIP, images, links, or folders.
- Past exam papers, quizzes, homework, worksheets, lab reports, or answer keys.
- Exam date, if useful for prioritizing review depth.
- Chapters or topics the user especially worries about.
- Preferred output language and file location.

Do not ask for a target score. Assume the goal is a self-contained review package that covers the main examinable content well enough for strong performance.

## Source Processing

Prefer Markdown as the working format, but do not make MarkItDown a hard dependency.

1. Check whether the `$markitdown-convert` skill is available or whether `markitdown --version` works.
2. If MarkItDown is available, convert supported files to Markdown before summarizing:

```bash
python3 /path/to/markitdown-convert/scripts/convert_with_markitdown.py INPUT --output OUTPUT.md
```

Direct CLI usage is also acceptable:

```bash
markitdown INPUT > OUTPUT.md
```

3. After each conversion, inspect the converted Markdown before trusting it:
   - Check the beginning, middle, and end.
   - Check file size and whether content is mostly empty.
   - Look for mojibake, broken Chinese text, repeated garbage characters, missing tables, missing formulas, missing slides, or obvious page-order problems.
4. If the Markdown is garbled or incomplete, read the original source directly. Use specialized tools or skills when appropriate:
   - PDF tools for text extraction or rendered page checks.
   - Documents tools for Word documents.
   - Presentations tools for slide decks.
   - Spreadsheet tools for workbook-style practice data.
5. If MarkItDown is not available, ask the user to choose between:
   - installing/downloading MarkItDown and then converting the materials;
   - skipping installation and reading source files directly.

Always create a processing log that records each source file, conversion status, fallback method, and any content that may be missing or unreliable.

## Build The Review Package

Create a source index first. Track each file name, chapter, section, page, slide number, question number, or worksheet label whenever available.

Then synthesize the material in this order:

1. Identify exam-relevant structure: chapters, themes, formulas, definitions, methods, diagrams, and recurring question patterns.
2. Rank likely importance from source evidence:
   - repeated across lectures, homework, and past exams;
   - emphasized in titles, summaries, bold text, learning objectives, or teacher notes;
   - required for multi-step problems;
   - frequently tested in past papers or assignments.
3. Write concise but complete explanations. Prefer study-ready phrasing over broad textbook prose.
4. Highlight key knowledge points using this exact pattern: `**<mark>重点内容</mark>**`.
5. After each knowledge module, add practice:
   - 2-4 true/false questions;
   - 1-2 classic examples, short-answer prompts, proof prompts, calculation problems, or application questions depending on the subject;
   - answers and explanations inside `<details>` blocks.
6. Mark uncertain inferred content as "推测考点" and explain why it is inferred.

For math, engineering, programming, statistics, physics, economics, accounting, or other calculation-heavy courses, include formulas, conditions of use, solved examples, common traps, and unit or notation checks.

For humanities, law, management, literature, language, politics, history, or theory-heavy courses, include definitions, comparison tables, argument structures, canonical examples, possible essay prompts, and answer frameworks.

## Mock Exams

Generate at least three mock exams:

- 基础巩固卷: checks definitions, basic methods, and core concepts.
- 高频考点卷: concentrates on repeated themes from materials, homework, and past questions.
- 综合冲刺卷: mixes chapters and uses more exam-like integrated problems.

Each mock exam must include answers, explanations, scoring points, and a short "复盘定位" telling the student which review sections to revisit after mistakes.

If the user requests web support or current/open resources may improve the paper, search the web and cite the sources used. If the web is unavailable or not requested, clearly state that mock questions are generated from the supplied materials and observed question style.

## Quality Bar

Before delivering, verify that:

- Every important chapter in scope appears in the outline or is explicitly marked as missing from the source set.
- Every knowledge module has highlighted key points and practice questions.
- Answers and explanations are present for practice questions and mock exams.
- The processing log explains any conversion failures, garbled Markdown, unreadable files, or fallback reads.
- The final package is usable without rereading the original PPT, Word, or PDF files, except where missing source quality prevents that.

If the material is too large for one pass, process it chapter by chapter and maintain a running source index so later synthesis stays consistent.
