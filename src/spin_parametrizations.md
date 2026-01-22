# Spin degrees of freedom in the presence of SU(2) symmetry

:::{note}
This section concerns electronic systems with SU(2) spin symmetry. For systems without SU(2) symmetry (e.g., in the presence of spin-orbit coupling or magnetic fields), the spin structure of two-particle quantities is more complicated and not covered here.
:::

SU(2) symmetry entails spin conservation for every correlation function, meaning the total spin of the incoming electrons must equal the total spin of the outgoing electrons. Furthermore, all quantities must be invariant under a global spin flip. 

Two-point functions are, as a consequence of spin conservation, diagonal in their spin arguments, $G_{\sigma_2 \sigma_1} \sim \delta_{\sigma_2, \sigma_1}$, with $\sigma_i \in \{\uparrow, \downarrow\}$. Invariance under global spin flips then implies that there is only a single independent spin component for two-point functions. Therefore, we drop their spin dependence completely.

For four-point functions, in particular vertices, spin conservation implies $F_{\sigma_1\sigma_2\sigma_3\sigma_4} \sim \delta_{\sigma_1+\sigma_3, \sigma_2+\sigma_4}$. The non-zero spin components of the vertex are 
\begin{align}
    F_{\sigma \overline{\sigma} \overline{\sigma} \sigma} &\equiv F_{\uparrow \downarrow} \\
    F_{\sigma \sigma \overline{\sigma} \overline{\sigma}} &\equiv F_{\overline{\uparrow\downarrow}} \\
    F_{\sigma\sigma\sigma\sigma} &\equiv F_{\uparrow \uparrow}\, ,
\end{align}
where $\overline{\sigma}$ denotes the spin opposite to $\sigma$. 

:::{warning}
In some papers (especially from the Vienna community), the definitions of $F_{\uparrow \downarrow}$ and $F_{\overline{\uparrow\downarrow}}$ are interchanged. This assignment in particular changes the roles of the two particle-hole channels, $ph \leftrightarrow \overline{ph}$. See also the [note](two-particle-channels#note-on-possible-confusion-regarding-ph-leftrightarrow-overline-ph) about the ambiguity in the literature regarding the definition of the two particle-hole channels.
:::

The three spin components above are furthermore related by the additionally identity
\begin{align}
    F_{\uparrow \uparrow} = F_{\uparrow \downarrow} + F_{\overline{\uparrow\downarrow}}\, ,
\end{align}
reducing the number of independent spin components to two.

:::{danger} To do
Derive this identity from the SU(2) symmetry. Use G. Rohringer's PhD thesis as a reference.
:::

:::{note}
The number of independent spin components can be further reduced to just one by using crossing symmetry, relating $F_{\uparrow \downarrow}$ and $F_{\overline{\uparrow\downarrow}}$.
Doing that in practice is somewhat intricate, as the crossing relation also swaps all other dependencies of the vertex as well as the two particle-hole channels. We will not go into details here.
:::

Depending on the context, it is often useful to work with linear combinations of the spin components defined above. One common choice is the magnetic/density basis, defined as
\begin{align}
    F_m &\equiv F_{\uparrow \uparrow} - F_{\uparrow \downarrow} \\
    F_d &\equiv F_{\uparrow \uparrow} + F_{\uparrow \downarrow}\, .
\end{align}
Another common choice is the singlet/triplet basis, defined as
\begin{align}
    F_s &\equiv F_{\uparrow \downarrow} - F_{\overline{\uparrow \downarrow}} = 2F_{\uparrow \downarrow} - F_{\uparrow \uparrow} \\
    F_t &\equiv F_{\uparrow \downarrow} + F_{\overline{\uparrow \downarrow}} = F_{\uparrow \uparrow}\, .
\end{align}

The main reason for introducing these linear combinations is that connections of two four-point vertices via bubbles in the $ph$ or $pp$ channels, respectively, decouple in these bases. Explicitly, one has
\begin{align}
    [A \circ \chi_0^{ph} \circ B]_{m/d} &= A_{m/d} \bullet \chi_0^{ph} \bullet B_{m/d} \\
    [A \circ \chi_0^{pp} \circ B]_{s/t} &= A_{s/t} \bullet \chi_0^{pp} \bullet B_{s/t}\, ,
\end{align}
where $A$ and $B$ are arbitrary four-point vertices and $\chi_0^{ph/pp}$ are the bubbles in the respective channels (see the section on [two-particle channels](two-particle-channels.md)). In this context, the symbol $\bullet$ denotes the contraction over all remaining internal variables except for the spin indices.

:::{dropdown} Explicit calculation
In the $ph$ channel, we have $[\chi_0]^{ph}_{\sigma_4 \sigma_3 \sigma_2 \sigma_1} \sim \delta_{\sigma_2, \sigma_1} \delta_{\sigma_4, \sigma_3}$, due to the fact that $G_{\sigma_2 \sigma_1} \sim \delta_{\sigma_2, \sigma_1}$. Hence, the contraction over spin arguments simplifies to
\begin{align}
    [A \circ \chi_0^{ph} \circ B]_{\sigma_1 \sigma_2 \sigma_3 \sigma_4} &= \sum_{\substack{\sigma_5, \sigma_6 \\ \sigma_7, \sigma_8}} A_{\sigma_5 \sigma_2 \sigma_3 \sigma_6} \bullet [\chi_0]^{ph}_{\sigma_8 \sigma_5 \sigma_6 \sigma_7} \bullet B_{\sigma_1 \sigma_8 \sigma_7 \sigma_4} \\
    &= \sum_{\sigma_5, \sigma_6} A_{\sigma_5 \sigma_2 \sigma_3 \sigma_6} \bullet \chi_0^{ph} \bullet B_{\sigma_1 \sigma_5 \sigma_6 \sigma_4}\, .
\end{align}
For the $\uparrow \uparrow$ and $\uparrow\downarrow$ components, it follows that
\begin{align}
    [A \circ \chi_0^{ph} \circ B]_{\uparrow \uparrow} &= [A \circ \chi_0^{ph} \circ B]_{\sigma\sigma\sigma\sigma} = \sum_{\sigma_5, \sigma_6} A_{\sigma_5 \sigma \sigma \sigma_6} \bullet \chi_0^{ph} \bullet B_{\sigma \sigma_5 \sigma_6 \sigma} \\
    &= A_{\sigma\sigma\sigma\sigma} \bullet \chi_0^{ph} \bullet B_{\sigma\sigma\sigma\sigma} + A_{\overline{\sigma} \sigma \sigma \overline{\sigma}} \bullet \chi_0^{ph} \bullet B_{\sigma \overline{\sigma} \overline{\sigma} \sigma} \\
    &= A_{\uparrow \uparrow} \bullet \chi_0^{ph} \bullet B_{\uparrow \uparrow} + A_{\uparrow \downarrow} \bullet \chi_0^{ph} \bullet B_{\uparrow \downarrow} \\ & \\
    [A \circ \chi_0^{ph} \circ B]_{\uparrow \downarrow} &= [A \circ \chi_0^{ph} \circ B]_{\sigma \overline{\sigma} \overline{\sigma} \sigma} = \sum_{\sigma_5, \sigma_6} A_{\sigma_5 \overline{\sigma} \overline{\sigma} \sigma_6} \bullet \chi_0^{ph} \bullet B_{\sigma \sigma_5 \sigma_6 \sigma} \\
    &= A_{\sigma \overline{\sigma} \overline{\sigma} \sigma} \bullet \chi_0^{ph} \bullet B_{\sigma \sigma \sigma \sigma} + A_{\overline{\sigma} \overline{\sigma} \overline{\sigma} \overline{\sigma}} \bullet \chi_0^{ph} \bullet B_{\sigma \overline{\sigma} \overline{\sigma} \sigma} \\
    &= A_{\uparrow \downarrow} \bullet \chi_0^{ph} \bullet B_{\uparrow \uparrow} + A_{\uparrow \uparrow} \bullet \chi_0^{ph} \bullet B_{\uparrow \downarrow}\, .
\end{align}
We thus find for the magnetic and density components
\begin{align}
    [A \circ \chi_0^{ph} \circ B]_{m/d} &= [A \circ \chi_0^{ph} \circ B]_{\uparrow \uparrow} \mp [A \circ \chi_0^{ph} \circ B]_{\uparrow \downarrow} \\
    &= A_{\uparrow \uparrow} \bullet \chi_0^{ph} \bullet B_{\uparrow \uparrow} + A_{\uparrow \downarrow} \bullet \chi_0^{ph} \bullet B_{\uparrow \downarrow} \mp A_{\uparrow \downarrow} \bullet \chi_0^{ph} \bullet B_{\uparrow \uparrow} \mp A_{\uparrow \uparrow} \bullet \chi_0^{ph} \bullet B_{\uparrow \downarrow} \\
    &= (A_{\uparrow \uparrow} \mp A_{\uparrow \downarrow}) \bullet \chi_0^{ph} \bullet (B_{\uparrow \uparrow} \mp B_{\uparrow \downarrow}) \\
    &= A_{m/d} \bullet \chi_0^{ph} \bullet B_{m/d}\, . \ \checkmark
\end{align}

In the $pp$ channel, we have $[\chi_0]^{pp}_{\sigma_4 \sigma_3 \sigma_2 \sigma_1} \sim \delta_{\sigma_4, \sigma_1} \delta_{\sigma_2, \sigma_3}$, again due to the fact that $G_{\sigma_2 \sigma_1} \sim \delta_{\sigma_2, \sigma_1}$. Hence, the contraction over spin arguments simplifies to
\begin{align}
    [A \circ \chi_0^{ph} \circ B]_{\sigma_1 \sigma_2 \sigma_3 \sigma_4} &= \sum_{\substack{\sigma_5, \sigma_6 \\ \sigma_7, \sigma_8}} A_{\sigma_1 \sigma_5 \sigma_3 \sigma_6} \bullet [\chi_0]^{ph}_{\sigma_6 \sigma_8 \sigma_5 \sigma_7} \bullet B_{\sigma_7 \sigma_2 \sigma_8 \sigma_4} \\
    &= \sum_{\sigma_5, \sigma_6} A_{\sigma_1 \sigma_5 \sigma_3 \sigma_6} \bullet \chi_0^{ph} \bullet B_{\sigma_6 \sigma_2 \sigma_5 \sigma_4}\, .
\end{align}
For the $\uparrow \uparrow$ component, which is the same as the triplet component, this equation is already diagonal,
\begin{align}
    [A \circ \chi_0^{pp} \circ B]_{t} &= [A \circ \chi_0^{pp} \circ B]_{\uparrow \uparrow} = [A \circ \chi_0^{pp} \circ B]_{\sigma \sigma \sigma \sigma} = \sum_{\sigma_5, \sigma_6} A_{\sigma \sigma_5 \sigma \sigma_6} \bullet \chi_0^{pp} \bullet B_{\sigma_6 \sigma \sigma_5 \sigma} \\
    &= A_{\sigma \sigma \sigma \sigma} \bullet \chi_0^{pp} \bullet B_{\sigma \sigma \sigma \sigma} = A_{\uparrow \uparrow} \bullet \chi_0^{pp} \bullet B_{\uparrow \uparrow} = A_{t} \bullet \chi_0^{pp} \bullet B_{t}\, .\ \checkmark
\end{align}
For the $\uparrow \downarrow$ and $\overline{\uparrow \downarrow}$ components, we have,
\begin{align}
    [A \circ \chi_0^{pp} \circ B]_{\uparrow \downarrow} &= [A \circ \chi_0^{pp} \circ B]_{\sigma \overline{\sigma} \overline{\sigma} \sigma} = \sum_{\sigma_5, \sigma_6} A_{\sigma \sigma_5 \overline{\sigma} \sigma_6} \bullet \chi_0^{pp} \bullet B_{\sigma_6 \overline{\sigma} \sigma_5 \sigma} \\
    &= A_{\sigma \sigma \overline{\sigma} \overline{\sigma}} \bullet \chi_0^{pp} \bullet B_{\overline{\sigma} \overline{\sigma} \sigma \sigma} + A_{\sigma \overline{\sigma} \overline{\sigma} \sigma} \bullet \chi_0^{pp} \bullet B_{\sigma \overline{\sigma} \overline{\sigma} \sigma} \\
    &= A_{\overline{\uparrow \downarrow}} \bullet \chi_0^{pp} \bullet B_{\overline{\uparrow \downarrow}} + A_{\uparrow \downarrow} \bullet \chi_0^{pp} \bullet B_{\uparrow \downarrow} \\ & \\
    [A \circ \chi_0^{pp} \circ B]_{\overline{\uparrow \downarrow}} &= [A \circ \chi_0^{pp} \circ B]_{\sigma \sigma \overline{\sigma} \overline{\sigma}} = \sum_{\sigma_5, \sigma_6} A_{\sigma \sigma_5 \overline{\sigma} \sigma_6} \bullet \chi_0^{pp} \bullet B_{\sigma_6 \sigma \sigma_5 \overline{\sigma}} \\
    &= A_{\sigma \overline{\sigma} \overline{\sigma} \sigma} \bullet \chi_0^{pp} \bullet B_{\sigma \sigma \overline{\sigma} \overline{\sigma}} + A_{\sigma \sigma \overline{\sigma} \overline{\sigma}} \bullet \chi_0^{pp} \bullet B_{\overline{\sigma} \sigma \sigma \overline{\sigma}} \\
    &= A_{\uparrow \downarrow} \bullet \chi_0^{pp} \bullet B_{\overline{\uparrow \downarrow}} + A_{\overline{\uparrow \downarrow}} \bullet \chi_0^{pp} \bullet B_{\uparrow \downarrow}\, .
\end{align}
For the singlet component, we thus find
\begin{align}
    [A \circ \chi_0^{pp} \circ B]_{s} &= [A \circ \chi_0^{pp} \circ B]_{\uparrow \downarrow} - [A \circ \chi_0^{pp} \circ B]_{\overline{\uparrow \downarrow}} \\
    &= A_{\overline{\uparrow \downarrow}} \bullet \chi_0^{pp} \bullet B_{\overline{\uparrow \downarrow}} + A_{\uparrow \downarrow} \bullet \chi_0^{pp} \bullet B_{\uparrow \downarrow} - A_{\uparrow \downarrow} \bullet \chi_0^{pp} \bullet B_{\overline{\uparrow \downarrow}} - A_{\overline{\uparrow \downarrow}} \bullet \chi_0^{pp} \bullet B_{\uparrow \downarrow} \\
    &= (A_{\uparrow \downarrow} - A_{\overline{\uparrow \downarrow}}) \bullet \chi_0^{pp} \bullet (B_{\uparrow \downarrow} - B_{\overline{\uparrow \downarrow}}) \\
    &= A_{s} \bullet \chi_0^{pp} \bullet B_{s}\, . \ \checkmark
\end{align}
:::