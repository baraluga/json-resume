# JSON Resume Project

Resume data files live in `resumes/` and follow the **Reactive Resume v4** schema (NOT the JSON Resume standard).

## Schema Reference

The full JSON Schema is at `schemas/reactive-resume.schema.json`. Key field names that differ from JSON Resume:

| Section   | Reactive Resume field | NOT this (JSON Resume) |
|-----------|----------------------|------------------------|
| Education | `school`             | `institution`          |
| Education | `degree`             | `studyType`            |
| Education | `grade`              | `score`                |
| Education | `location`           | (missing in JSON Resume) |

## Rules for editing resume files

- Always use the Reactive Resume field names, not JSON Resume field names
- Every item needs `id` (UUID string) and `hidden` (boolean)
- `website` is always `{ "url": "", "label": "" }`, never a bare string
- `options` (`{ "showLinkInTitle": boolean }`) is optional on all items
- Each section item type has one required non-empty field: `company` (experience), `school` (education), `name` (projects/skills/interests), `title` (awards/certifications/publications), `organization` (volunteer), `language` (languages), `network` (profiles), `name` (references)
- Custom sections use `type` to determine which item schema applies (e.g. `"type": "experience"` means items follow the experience schema)
- `description` fields use HTML: `<p>`, `<ul><li>`, `<em>`, `<strong>`
- `0_master.json` is the master resume; role-specific resumes are derived from it
