# Learnings repo

Personal learning notes by Rahul, published as a searchable site with
[docsify](https://docsify.js.org).

Live: https://rahullanjewardelightree.github.io/learning/

## Purpose

These are revision notes, not documentation. The reader is the author, six months
later, trying to reload context fast. Optimise for skimming: short sections, concrete
examples, the gotcha stated plainly. Prefer a command or a code block over a paragraph
describing one. Do not pad notes to look complete — a three-line note that captures the
one thing worth remembering is a good note.

## How the site works

`index.html` is the entire application. It loads docsify from jsDelivr, and docsify
fetches the Markdown files over HTTP at runtime and renders them in the browser.

There is **no build step and no generator**. Consequences worth internalising:

- The `.md` files in git are exactly what gets served. Nothing transforms them.
- Nothing needs installing to work on this repo. Edit Markdown, push, done.
- The page source is a near-empty `<div id="app">`; content is injected by JS.
- Pages are addressed by hash route: `/#/aws/vpc` serves `aws/vpc.md`.

### Why docsify and not Jekyll

GitHub Pages runs Jekyll by default. Jekyll is a static site generator: it builds
Markdown into HTML ahead of time, which buys generated navigation, themes, and clean
SEO — at the cost of a `_config.yml`, a theme to learn, and YAML front matter on every
single file. For a pile of personal notes that tax isn't worth paying, so the repo opts
out. Do not reintroduce Jekyll config or front matter; docsify ignores it and it would
render as visible junk at the top of a page.

### .nojekyll

Jekyll skips files and folders whose names start with `_` or `.`. Without the empty
`.nojekyll` file at the repo root, GitHub Pages would refuse to publish `_sidebar.md`
and docsify's fetch for it would 404, silently killing the navigation. The same applies
to any future `_navbar.md` or `_coverpage.md`. **Never delete `.nojekyll`.**

## Layout

```
index.html      docsify config: theme, search, sidebar, Prism languages
.nojekyll       disables Jekyll on GitHub Pages (required — see above)
README.md       homepage, rendered at /
_sidebar.md     navigation, hand-maintained
CLAUDE.md       this file
aws/README.md   section landing page
aws/*.md        notes
```

## Adding a note

1. Create `<topic>/<note>.md` beginning with an `# H1` title. Docsify uses that H1 as
   the page title, and `subMaxLevel: 2` means `##` headings appear as sub-entries in
   the sidebar automatically.
2. Add a line to `_sidebar.md` under the right section. This is the only manual step —
   a note that isn't in the sidebar is reachable by URL but invisible to browsing.
3. Commit and push. GitHub Pages redeploys from `main` root within a minute.

A new topic is a new folder with a `README.md` landing page, a new section in
`_sidebar.md`, and a bullet under **Topics** in `README.md`.

## Conventions and gotchas

- **Links between notes are relative paths to the `.md` file**, extension included:
  `[VPC](../aws/vpc.md)`. Docsify rewrites these into hash routes. A link without the
  `.md` is treated as an external path and breaks.
- **`_sidebar.md` paths are relative to the repo root**, not to the file being viewed.
- **Fenced code blocks need a language tag.** Docsify bundles Prism for a handful of
  languages; bash, typescript, json and yaml are loaded explicitly in `index.html`. A
  language beyond those needs its own
  `<script src="https://cdn.jsdelivr.net/npm/prismjs@1/components/prism-<lang>.min.js">`
  added there, or the block renders unhighlighted.
- **CDN versions are pinned to majors** (`docsify@4`). Leave them; a floating latest
  would break the site without a commit to blame.
- **Images** go next to the note that uses them and are referenced relatively.

## Preview locally

```bash
npx serve .          # or: python3 -m http.server
```

Opening `index.html` over `file://` does not work — docsify fetches the Markdown with
XHR, which the browser blocks on the file protocol. It must be served over HTTP.

## Deployment

GitHub Pages, legacy build, `main` branch, root path. There is no CI and no workflow
file. Pushing to `main` is the deploy.
