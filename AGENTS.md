# AGENTS.md

This file applies to the entire `TwoParticleQFT` repository. Read it before making any
non-trivial change. It tells human and AI contributors **how to write pages that are
consistent with the ones already here.** When in doubt, imitate the existing pages: they are
the reference, and other projects (e.g. `ReFrequenTT`) already treat this repo as their
convention ground-truth, so drift here propagates.

## What this repository is

A [MyST Markdown](https://mystmd.org/) / [Jupyter Book 2](https://next.jupyterbook.org/)
documentation site on two-particle quantities in quantum field theory, deployed to GitHub
Pages. Pages live in `src/*.md`; the table of contents is `myst.yml`; the landing page is
`src/intro.md`. See `README.md` for the project overview and the live site.

The site's whole reason to exist is that different communities use mutually incompatible
conventions. So the primary job of every page is to **fix one convention clearly and
translate to the others**, not to re-derive physics in yet another private notation.

## Conventions are the point (not optional)

- **The existing pages are the source of truth for conventions and notation**, not a paper,
  not memory. Before introducing any symbol or equation, check how it is already defined here
  and match it. The load-bearing pages are:
  - [`src/symbols_and_notations.md`](src/symbols_and_notations.md): the symbol registry, each
    entry cross-listed against its common literature synonyms. **Any new symbol must be added
    here**, with its synonyms.
  - [`src/starting_point.md`](src/starting_point.md): action, bare propagator, Hugenholtz
    interaction, the Vienna/Munich index conventions.
  - [`src/basic_definitions.md`](src/basic_definitions.md): propagator, self-energy,
    four-point function and vertex; the index-ordering conventions.
  - [`src/two-particle-channels.md`](src/two-particle-channels.md),
    [`src/frequency_parametrizations.md`](src/frequency_parametrizations.md),
    [`src/spin_parametrizations.md`](src/spin_parametrizations.md): channels, frequency
    parametrizations, SU(2) spin structure.
  - [`src/gw_approximation.md`](src/gw_approximation.md) and
    [`src/second_order_perturbation_theory.md`](src/second_order_perturbation_theory.md):
    fully parametrized worked results that downstream projects rely on directly; keep them
    consistent with the pages above.
- **Do not silently switch conventions.** Keep the channel-native frequency parametrization and
  the Keldysh conventions of [`src/keldysh_formalism.md`](src/keldysh_formalism.md) (the
  retarded/advanced/Keldysh component structure after the Keldysh rotation, the causality
  zeros, and the fact that the self-energy's Keldysh indices are interchanged relative to the
  propagator's). Rewriting existing pages into a different parametrization is not a cleanup;
  it is a breaking change. If a page genuinely needs a different convention, say so explicitly,
  in a box, and relate it back to the house convention.
- **Documenting an alternative convention is welcome; silently adopting it is not.** Adding a
  page or section that presents another community's or another code's convention, and maps it
  onto the house one, is exactly what this site is for. The open to-do on symmetric frequency
  parametrizations in [`src/frequency_parametrizations.md`](src/frequency_parametrizations.md)
  is a standing invitation, not something to avoid; what must not happen is re-parametrizing
  the existing pages on the way.
- **Point out differences to other conventions** wherever a reader coming from the literature
  would trip, most importantly the **"Vienna" vs "Munich"** conventions and the differing
  **channel labelings**. This cross-referencing is a feature, not an aside.

### House conventions to preserve

- **Vienna convention** is the default (arabic multi-indices `1,2` / `1,2,3,4`; the same-sign
  Fourier transform, so `ν₁+ν₂+ν₃+ν₄ = 0` for the vertex). Contrast Munich where relevant.
- **Multi-index parity:** odd indices label creation operators (`c̄`), even indices label
  annihilation operators (`c`). The index order in correlation functions (`G`, `G⁽⁴⁾`) is
  reversed relative to vertex functions (`Σ`, `F`).
- **Statistics factor `ζ`** (`ζ = −1` fermions, `+1` bosons) is kept general rather than
  hard-coding fermions.
- **Channels** are `ph`, `ph̄` (transverse, overline-ph), and `pp`. Use the channel-native
  `(ν, ν′, ω)` parametrization.
- **Hugenholtz** (antisymmetrized) notation for the bare vertex.
- **Connectors:** `∘` for the channel-specific contraction, `•` for contraction over all
  dependencies except frequency; channel identity operators `1ʳ`.
- **Keldysh:** retarded/advanced/Keldysh (`R`/`A`/`K`) components after the Keldysh rotation,
  with the component structure, the causality zeros, and the index ordering of `Σ` relative to
  `G` as documented in [`src/keldysh_formalism.md`](src/keldysh_formalism.md).

## How to write a page

The style that the existing pages follow, and that new pages must match:

1. **Fully parametrize every equation.** All frequency, momentum, spin, and multi-index
   arguments explicit. A reader must never have to guess a convention: "there can be no
   question marks regarding any conventions regarding arguments, indices, and so on."
2. **Derive results properly, but keep the main text readable.** State the result in the body,
   and put the step-by-step derivation in a collapsible `:::{dropdown} Explicit calculation`
   block (see below). Build on what other pages already derive rather than repeating it;
   link to them.
3. **Disambiguate notation aggressively.** When a symbol could be confused with one used on
   another page (e.g. a tilde for a "decaying part" vs the SBE `Δʳ` vs a hybridization `Δ(ν)`),
   add a `:::{warning}` or `:::{note}` that says so and links to the other page.
4. **Write for a new graduate student**, not only for the expert who already knows the answer.
   Prefer explicit prose and explicit steps over terse allusions.
5. **Do not use em-dashes.** Use a comma, a colon, a semicolon, parentheses, or two sentences.
   Em-dash-heavy prose reads as machine-written, which undermines a reference whose value
   depends on being trusted. En-dashes in compound names (Bethe–Salpeter, Schwinger–Dyson) are
   correct and stay.
5. **Be honest about status.** Mark anything incomplete, stated-without-derivation, or
   unverified with a `:::{danger}` "to do" admonition, the site-wide marker for open items
   (existing pages write the title as both "To do" and "To Do"; either is fine). Do not present
   a conjecture or a quoted-but-unchecked result as settled.

## MyST mechanics and formatting

Match the concrete patterns already in `src/`:

- **One `# H1` per page** (the page title; math is allowed, e.g. `# The $GW$ approximation`).
  Sections are `##` / `###`; cross-references target their slugified anchors.
- **Display math uses `\begin{align} … \end{align}`** (the site has hundreds of these);
  inline math uses `$…$`. Equations are generally unnumbered: cross-reference **sections**,
  not equation numbers.
- **Admonition palette** (the ones in use, stick to them):
  - `:::{note}`, `:::{important}`, `:::{warning}`, `:::{hint}`: remarks and caveats.
  - `:::{danger} To do`: open items / unfinished derivations. This is the marker maintainers
    scan for; use it rather than leaving silent gaps.
  - `:::{dropdown} Explicit calculation`: collapsible long derivations (also "Explicit
    derivation", "Consistency check with …", "Note on signs and prefactors", etc.).
  - `:::{image} diagrams/…`: figures.
  - **Nesting:** use one extra colon for the outer block, e.g. a `::::{dropdown}` or
    `::::{note}` that contains a `:::{image}` or another `:::` admonition.
- **Cross-links** use relative Markdown paths: `[text](other_page.md)` or
  `[text](other_page.md#section-anchor)`. Link liberally between pages.
- **Same-page links need an explicit target.** MyST warns when you link to a heading's implicit
  HTML id, because that id changes whenever the title is reworded. Put a label above the target
  and link to it:
  ```markdown
  (stoner-criterion)=
  ### Stoner criterion
  ```
  then `[Stoner criterion](#stoner-criterion)`. Labels also work on admonitions, which is the
  way to link to a specific box. Note that **a heading containing math gets no usable implicit
  id** (`# The $GW$ approximation` does *not* yield `#the-gw-approximation`): such a target
  must have an explicit label. Where a label replaces an id that other pages already link to,
  keep the label string identical to the old anchor so those links keep working.
- **The build must be warning-free.** `jupyter-book build --html` should report no `⚠️` lines.
  Broken references and implicit-heading links are cheap to fix and expensive to leave.
- **Diagrams** live under `src/diagrams/`, grouped in a subfolder per topic
  (e.g. `src/diagrams/w2dynamics/`). Prefer vector (`.svg`) where practical; `.png` is fine.
- **Per-page frontmatter is optional.** Most pages start directly with the H1; a page may carry
  a `--- author: "Name" ---` block if a specific author wants attribution.

## Adding a new page

1. Create `src/<name>.md` starting with a single `# Title`.
2. Register it in `myst.yml` under the appropriate `toc` section (Definitions / Diagrammatic
   frameworks / Advanced topics).
3. Add a matching link in `src/intro.md` under the same section, and keep the link text and the
   page's H1 consistent with each other.
4. Put any figures in `src/diagrams/<name>/`.
5. Add every new symbol to `src/symbols_and_notations.md`, with its literature synonyms.
6. Consider updating `README.md`'s "What's inside" table if the page is a substantive new topic.

## Building and previewing

The site is a Jupyter Book 2 / MyST project (`jupyter-book` v2 CLI; a Node runtime is
bootstrapped for you either way):

```bash
pip install jupyter-book        # or: npm install -g jupyter-book
jupyter-book start              # live preview with hot reload
jupyter-book build --html       # static build into _build/html
```

Every push to `main` triggers `.github/workflows/deploy.yml`, which builds and publishes to
GitHub Pages. There is no content CI on pull requests, so **preview locally before opening a
PR**: a broken admonition or a bad cross-link will otherwise only surface after merge.

## Contributing workflow

- Anyone may contribute; open a pull request. `main` is protected and requires a code-owner
  review before merge.
- Good starting points: the **wishlist** at the end of `src/intro.md`, and the `:::{danger}
  To Do` admonitions scattered through the pages.
- **Keep changes surgical.** Touch only what the task needs; match the surrounding style even
  if you would personally do it differently; do not "improve" adjacent prose or reformat pages
  you are not editing.
- For a substantive **new section or page**, think about scope and structure first (the
  `superpowers:brainstorming` skill is a good fit) rather than writing straight into the file.
- Fix a real error wherever you find it, but if a page states a convention that contradicts the
  ground-truth pages, surface it rather than silently "correcting" one side, since the inconsistency
  itself may be the thing to document.
