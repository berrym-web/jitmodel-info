# jitmodel-info

A static GitHub Pages site about how jitmodel was built with Claude. jitmodel is a model and web app for the
re-condensing cryogenic power cycle of US Patent 11,598,261 (Just In Time Energy Company).

The site has:

- `index.html`: an overview, with links to the claude.ai planning conversation, the Claude Code transcript and the
  project documents.
- `pages/transcript.html`: an edited transcript of the Claude Code (CLI) session that built jitmodel.
- `pages/*.html`: the jitmodel repository's README, PLAN, DECISIONS, VALIDATION and CLAUDE markdown files,
  converted to HTML.
- `assets/`: the shared stylesheet, the logo and the favicon.

It's served from the `main` branch root. `.nojekyll` turns off GitHub's Jekyll processing.

## Building

The pages in `pages/` are generated files. The build tooling is not in this repository, because it contains the
personal details it removes from the transcript. It is kept locally next to the site:

- `build.sh`: converts the jitmodel markdown files with pandoc and generates the edited transcript. It stops if
  any personal details are left in the output.
- `build/template.html`: the pandoc page template.
- `build/links.lua`: a pandoc filter. It links mentions of the other documents and renders the Mermaid diagram.
- `build/transcript.py` and `build/transcript_parse.py`: turn the exported transcript HTML into the edited
  transcript.

Requirements: pandoc 3, Python 3, and a local checkout of the jitmodel repository.

```sh
./build.sh [path-to-jitmodel] [path-to-exported-transcript.html]   # defaults: ~/jitmodel and the export here
git add -A && git commit -m "Update pages" && git push
```

`index.html` and `assets/style.css` are edited by hand.

Copyright 2026 Just In Time Energy Company.
