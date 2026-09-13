# Learnings repo

Personal learning notes, rendered as a site by [docsify](https://docsify.js.org).

## How it works

`index.html` is the whole app. Docsify fetches the Markdown at runtime and renders
it in the browser — there is no build step, no generator, no dependencies to install.
`.nojekyll` stops GitHub Pages from touching the files. Published from the `main`
branch, root folder.

## Layout

```
index.html      docsify config (theme, search, sidebar, prism languages)
README.md       homepage
_sidebar.md     navigation — hand-maintained
aws/README.md   section landing page
aws/*.md        notes
```

## Adding a note

1. Create `<topic>/<note>.md` with an `# H1` title.
2. Add a line to `_sidebar.md` under the right section.

A new topic = new folder with a `README.md` plus a section in `_sidebar.md`.

## Preview locally

```bash
npx serve .     # or: python3 -m http.server
```

Opening `index.html` via `file://` does not work — docsify needs HTTP.

## Conventions

- Notes are for revision: short, skimmable, code examples over prose.
- Links between notes are relative paths to the `.md` file (`../aws/vpc.md`).
- Fenced code blocks get a language tag. Languages beyond the docsify defaults
  need a Prism component `<script>` added to `index.html`.
