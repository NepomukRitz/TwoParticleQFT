# TwoParticleQFT

::::{grid} 1 2 2 2

Welcome to the TwoParticleQFT documentation site! This site aims to provide a comprehensive overview of two-particle quantities in quantum field theory, with a focus on their applications in strongly correlated electron systems. We cover the fundamental definitions, diagrammatic representations, and key concepts needed to understand and work with two-particle vertices, correlation functions, and related quantities.

:::{image} images/vertex.png
:::
::::

In addition, we include some technical derivations, complementing the main text, which are often omitted in papers for the sake of brevity.

:::{note} Note about conventions
There is a vast body of litature on two-particle quantities in quantum field theory, and different communities often use different conventions and notations, which sometimes even differ from paper to paper. This fact is often a source of major confusion and [the main motivation for putting together this site](https://xkcd.com/927). In this documentation, we strive to be as clear and consistent as possible regarding our conventions. Whenever relevant, we point out differences to other common conventions in the literature.
:::

:::{hint} How to contribute
This site is editable by anyone! If you find mistakes, have suggestions for improvements, or want to contribute new sections, feel free to open a pull request on the [GitHub repository](https://github.com/NepomukRitz/TwoParticleQFT). A good starting point are the open "to do"s listed throughout these pages or to check the [wishlist](intro.md#wishlist) at the end of this page.
:::

## Definitions

- [Starting point: Many-body Hamiltonian and action](starting_point.md)

- [Basic quantities: propagator, self-energy, four-point function, vertex](definitions.md)

- [Two-particle channels](two-particle-channels.md)

- [Frequency parametrizations](frequency_parametrizations.md)

- [Spin degrees of freedom in the presence of SU(2) symmetry](spin_parametrizations.md)

## Diagrammatic frameworks

- [Parquet theory: parquet decomposition, Bethe-Salpeter equations, Schwinger-Dyson equation, parquet approximation](parquet_theory.md)
- [Single boson exchange (SBE) decomposition and approximation](single_boson_exchange.md)


## Wishlist

This site is still under construction. Below is a wishlist of tasks to be completed and sections to be added, in decreasing order of priority:

- Add nice-looking vector graphics for all diagrams
- Add a section on the SBE decomposition and approximation
- Add a section on the Keldysh formalism in the steady state (including thermal equilibrium), highlighting the differences to the Matsubara formalism
- Add derivations of the BSEs and the SDE
- Add a section on asymptotic decomposition of the two-particle vertex
- Add a section on generalized susceptibilities, maybe even as part of the basic definitions
- Add a section physical susceptibilities and general response functions and how to compute them from two-particle vertices
- Add a bibliography, especially specifying which papers we mean when we talk about the "Vienna" or "Munich" conventions

Beyond that, we could think of adding sections on more methods, as desired. Suitable topics could be:
- Functional renormalization group (fRG) and its multiloop extension
- Spectral representation of two-particle quantities
- Section on numerical aspects: Frequency grids, asymptotics, algorithms (e.g. Anderson acceleration or Pulay mixing) for solving Bethe-Salpeter and parquet equations, I/O considerations for large data sets, ...
- Non-local extensions of DMFT, such as
    - GW+DMFT
    - Dynamical vertex approximation (D$Γ$A)
    - Dual fermion approach
    - Finite-difference parquet method
    - DMF$^2$RG
