# CLAUDE.md

The full contributor guide for this repository is **[`AGENTS.md`](AGENTS.md)** — read it before
any non-trivial change.

Highest-signal reminders when writing or editing a page:

- **The existing `src/*.md` pages are the source of truth for conventions and notation.** Match
  them; don't invent notation or silently switch conventions (e.g. no symmetric `ν ± ω/2`). New
  symbols go into [`src/symbols_and_notations.md`](src/symbols_and_notations.md) with their
  literature synonyms.
- **Fully parametrize every equation** — all frequency/momentum/spin/index arguments explicit,
  no ambiguity about which convention is in force.
- **Derive properly, but keep the body readable:** put long derivations in a
  `:::{dropdown} Explicit calculation` block; state the result in the main text.
- **Match the house MyST style:** one `# H1` per page, `\begin{align}` display math,
  `:::{note}` / `:::{important}` / `:::{warning}` admonitions, `:::{danger} To Do` for open
  items, relative `[text](page.md#anchor)` cross-links, diagrams under `src/diagrams/`.
- **Cross-reference other conventions** (Vienna vs Munich, channel labelings) wherever a reader
  from the literature would trip, and **disambiguate** symbols that clash across pages.
- **Preview locally** with `jupyter-book start` before opening a PR — there is no content CI on
  pull requests.
