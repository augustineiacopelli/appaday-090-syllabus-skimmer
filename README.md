# AppADay 090 &middot; Syllabus Skimmer

**Upload a syllabus PDF or paste the text. Get back the parts you actually need.**

**Live:** https://augustineiacopelli.github.io/appaday-090-syllabus-skimmer/

**Category:** Educational (E) &middot; **Day:** 090 &middot; **Built:** 2026-08-05

---

## What it does

A syllabus is fifteen pages of prose hiding about eight facts that matter. Syllabus Skimmer takes the whole document, PDF or pasted text, hands it to Claude, and returns a structured summary card: the course at a glance, the grading breakdown drawn as a weighted bar, every key date on a filterable timeline, required versus optional materials, and the policies on attendance, late work, academic integrity, and generative AI quoted rather than paraphrased away.

It also flags the things that are easy to miss. A capstone that is never accepted late. An attendance rule that costs a full letter grade. A hard drop deadline in week three. Those go in their own card at the bottom.

Drop the PDF straight in and it goes to Claude intact, tables and multi-page schedules and all, with no text extraction step to mangle the layout first. Plain text and Markdown files load into the paste box. A photo or screenshot of a printed page works too. Or paste anything at all: broken line breaks, page headers, and copy artifacts are fine.

## Input

Drag a file onto the panel, or click the drop zone to choose one. PDFs and images are attached to the request as-is and are capped at 25 MB. Text and Markdown files are read into the paste box so you can edit before skimming. If you attach a file and also type in the box, the typed text is passed along as additional context rather than replacing the document.

## Why it exists

Built the week before starting an MSBA program, on the reasonable assumption that reading four syllabi carefully in August is less likely than skimming them badly in September.

## Features

The grading card sums the weights and tells you when they do not reach one hundred percent, which is more common than it should be and usually means a component was worded differently somewhere else in the document. If the syllabus uses raw points instead of percentages, the points are converted and the original totals are kept as a note.

The date timeline sorts chronologically, infers years from the stated term when the syllabus gives only a month and day, and keeps unresolvable entries like "Week 4" in place rather than dropping them. Filter chips narrow the view to exams, assignments, deadlines, or breaks.

The AI policy gets its own highlighted panel. If the syllabus says nothing about generative tools, the panel says so plainly instead of leaving a blank, because silence is not permission.

The last skim is kept in `localStorage`, so the summary is still there when you come back. Export as markdown, copy to the clipboard, or print to a clean page with the input panel stripped out.

## Using it

Open the gear in the top right and paste an Anthropic API key. The key and the optional session label live in your browser's `localStorage` and are never sent anywhere except to the Anthropic API. Your syllabus, whether pasted or uploaded, goes directly from your browser to Anthropic; nothing passes through a server of mine, and no file is ever stored.

Press **Load sample** to try it against a realistic graduate business analytics syllabus without pasting anything.

Keyboard: `Cmd`/`Ctrl` + `Enter` in the textarea runs the skim. `Esc` closes Settings.

## Technical

A single self-contained `index.html`. Vanilla HTML, CSS, and JavaScript with no framework, no build step, and no dependency beyond Google Fonts. Claude is called directly from the browser with `anthropic-dangerous-direct-browser-access`, using `claude-sonnet-5`, and is prompted to return a single JSON object matching a fixed schema, which is then parsed defensively and rendered. PDFs and images are base64 encoded in the browser with `FileReader` and sent as native document and image content blocks, so there is no client-side PDF parsing library and nothing to bundle. Pasted input is capped at 60,000 characters per pass and uploads at 25 MB.

Fraunces for display type, Inter for everything else. Paper and ink palette with a deep teal accent. Fully responsive from a 375px phone to a wide desktop, with a two-column split for grading and materials above 760px and a dedicated print stylesheet.

## Caveat

This is a reading aid, not the authority. Extraction is very good and occasionally wrong. Confirm anything that carries a grade against the original document.

---

Part of [AppADay](https://augustineiacopelli.github.io/appaday/) by Augustine Iacopelli. One complete, functional, mobile-friendly web app every single day.
