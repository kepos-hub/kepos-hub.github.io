# Kepos

## Purpose
A community-maintained repo + static site (MkDocs) sharing graduate program
experiences — syllabi, course notes, reading lists, application experiences —
aimed primarily at Iranian students considering or currently in Master's/PhD
programs abroad, across fields (not limited to Philosophy/History of Science).
Named for Epicurus's Kepos ("The Garden"), a school unusually open to
outsiders for its time — the spirit this project aims for: a space that grows
as contributors from different programs and universities add their own.
Started with the maintainer's own program (LUH Hannover, HPS) as the seed
content; structured to generalize to other universities and fields as
contributors add theirs.

## Stack
- Content: Markdown with YAML frontmatter
- Site: MkDocs + Material theme
- Nav: manually maintained in `mkdocs.yml` unless/until content volume
  justifies `mkdocs-awesome-pages` or literate-nav

## Commands
- `mkdocs serve` — local preview at localhost:8000
- `mkdocs build` — static build to `site/`
- `mkdocs build --strict` — fail on broken links/nav refs (run before PRs)

## Repository structure
```
content/
  universities/
    <university-slug>/
      program-overview.md
      semesters/
        <term-slug>/            # e.g. ws2025, ss2026
          courses/
            <course-slug>/
              overview.md
              sessions/
                <NN-topic-slug>.md
              resources/
                readings.md
  application-experiences/
  reading-lists/
```

## Content conventions
- **Folders = structurally universal** (university → semester → course).
  Do not add program-specific levels (e.g. "module") as folders — they don't
  generalize across universities.
- **Frontmatter = program-specific metadata.** Put things like module name,
  ECTS, track, instructor as tags, not folder levels.
- `overview.md` frontmatter schema (per course):
  ```yaml
  ---
  title: ""
  field: ""          # e.g. Philosophy, History of Science, Sociology
  module: ""        # institution-specific label, optional
  ects: 0
  semester: ""       # e.g. WS2025
  instructor: ""
  ---
  ```
- Session files: `NN-topic-slug.md`, zero-padded, one file per session.
- Do not upload official syllabus/catalog PDFs verbatim unless the
  contributor has confirmed redistribution is permitted — summarize and
  restructure instead (topics, readings, structure), don't scan-and-dump.
- Slugs: lowercase, hyphenated, no spaces or special characters.

## When adding new content
1. Check whether the university/semester/course folder already exists
   before creating a new one — search first, don't assume.
2. Create `overview.md` before any `sessions/` files.
3. Update `mkdocs.yml` nav to include new pages (until an auto-nav plugin
   is adopted).
4. Run `mkdocs build --strict` before committing.

## Tone
Practical and first-person where it's experience/application content;
neutral and factual for syllabus/course-catalog summaries. This is a
resource for prospective and current students, not marketing copy for
any program.

## Out of scope for automation
Do not auto-generate application-experience or personal-reflection content
on a contributor's behalf — that content should come from the actual
contributor. Claude Code's job here is scaffolding, structure, formatting,
and nav/build maintenance, not writing people's stories for them.
