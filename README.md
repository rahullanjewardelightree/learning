# Learnings

Notes I write down so I can revise them later. Short, skimmable, heavy on examples —
written for my future self who has forgotten the details but remembers the shape of
the problem.

> Use the search box in the sidebar. It indexes headings and body text across every
> note, so searching the error message or the flag name usually gets you there faster
> than browsing.

## Topics

- [AWS](aws/README.md) — services, networking, the parts that bite.

## How this site works

Every page you're reading is a plain Markdown file in the
[repo](https://github.com/rahullanjewardelightree/learning). There's no build step:
[docsify](https://docsify.js.org) loads `index.html` once and fetches the Markdown at
runtime, so the files on GitHub and the pages here are the same thing. Reading a note
on GitHub directly works fine too — this site just makes it nicer.

## Adding a note

1. Create `<topic>/<note>.md`, starting with an `# H1` title.
2. Add a line for it in `_sidebar.md`.
3. Commit and push — GitHub Pages picks it up within a minute or so.

See [CLAUDE.md](CLAUDE.md) for the full conventions.
