# The fluctuation exchange (FLEX) approximation

The *fluctuation exchange* (FLEX) approximation of Bickers, Scalapino and White resums density, magnetic and pairing fluctuations on an equal footing ([N. E. Bickers, D. J. Scalapino and S. R. White, Phys. Rev. Lett. 62, 961 (1989)](https://doi.org/10.1103/PhysRevLett.62.961); [N. E. Bickers and D. J. Scalapino, Ann. Phys. 193, 206 (1989)](https://doi.org/10.1016/0003-4916(89)90359-X)). In the language of the [single boson exchange](single_boson_exchange.md) (SBE) decomposition, it is defined by three choices:

1. The fully $U$-irreducible vertex is neglected, $\Lambda^{U} \simeq 0$, as in the [SBE approximation](single_boson_exchange.md#sbe-approximation).
2. The Hedin vertices of **all three** channels are replaced by their lowest-order contribution, $\gamma^r \simeq \mathbf{1}^r$ and $\overline{\gamma}^r \simeq \mathbf{1}^r$ for every $r \in \{\overline{ph}, pp, ph\}$.
3. The self-energy is obtained by inserting the resulting vertex *directly* into the [Schwinger-Dyson equation](parquet_theory.md#schwinger-dyson-equation) (SDE), not into its [SBE form](single_boson_exchange.md#schwinger-dyson-equation-in-sbe-form).

The first two choices are shared with the [$GW$ approximation](gw_approximation.md); the difference lies entirely in the third. Setting the Hedin vertex to unity in the SBE form of the SDE gives a self-energy that involves the screened interaction of a single channel only: $GW$ for the two particle-hole forms, and a $T$-matrix approximation for the $pp$ form, as discussed in the section on [which form of the SDE](gw_approximation.md#which-form-of-the-schwinger-dyson-equation) to start from. Inserting the vertex into the SDE directly keeps the screened interactions of all three channels. The main result of this page is that the FLEX self-energy is the sum of these three single-channel self-energies, with the second-order diagram, which each of them contains, counted only once:
\begin{align}
    \Sigma - \Sigma_\mathrm{H} = \frac{1}{2}\, G \cdot \widetilde{W}^{ph} + \frac{1}{2} \zeta\, \widetilde{W}^{\overline{ph}} \cdot G + \zeta\, \widetilde{W}^{pp} \cdot G - 2\, \Sigma^{(2)} \, .
\end{align}
Here $\Sigma_\mathrm{H}$ is the Hartree term, $\widetilde{W}^r$ is the dynamic part of the screened interaction in channel $r$, and $\Sigma^{(2)}$ is the second-order self-energy. The first two terms turn out to be equal, so that only the $ph$ and the $pp$ ladder have to be computed in practice.

As on the $GW$ page, we specialize to a system with SU(2) spin symmetry and a *local and instantaneous* bare interaction, i.e. the Hubbard interaction of the [Hubbard model example](starting_point.md#example-hubbard-model). We use the compact notation of the [SBE](single_boson_exchange.md) and [parquet](parquet_theory.md) pages. Several results are taken over from the [$GW$ page](gw_approximation.md), which treats the single-channel case in detail. The derivation works with abstract multi-indices and only uses the crossing symmetry of the bare vertex; spin components and frequency arguments are written out only at the end, where we recover the familiar form of the FLEX equations.

(flex-scope)=
:::{important} Scope of the closed-form expressions
The derivation up to and including the [result in compact notation](#flex-result) does not depend on what the multi-indices contain, so it holds unchanged in the presence of additional indices such as Keldysh indices. The section on the [spin structure and explicit form](#flex-explicit-form), in contrast, assumes, as in the [scope of the $GW$ page](gw_approximation.md#gw-scope), that all objects are scalars in every degree of freedom other than spin and the bosonic transfer variable (a single band, Matsubara formalism). Only under this assumption are the ladders summed by an ordinary division. With additional indices, the division becomes a pointwise matrix inversion, as worked out for the $ph$ channel in the section on [closed-form ladder resummation with additional indices](gw_approximation.md#closed-form-ladder-resummation-with-additional-indices).
:::

:::{note}
Everything below is written for frequencies only. As explained in the section on [frequency parametrizations](frequency_parametrizations.md), all statements carry over verbatim to the momentum dependence by replacing $\nu, \nu', \omega \rightarrow \mathbf{k}, \mathbf{k}', \mathbf{q}$.
:::

## The vertex

### Screened interactions as bare ladders

With unit Hedin vertices, the $U$-reducible diagrams in channel $r$ reduce to the screened interaction itself,
\begin{align}
    \Delta^r = \overline{\gamma}^r \bullet W^r \bullet \gamma^r \simeq \mathbf{1}^r \bullet W^r \bullet \mathbf{1}^r = W^r \, ,
\end{align}
since $\mathbf{1}^r$ is by definition the unit with respect to the $\bullet$ contraction. The [bosonic Dyson equation](single_boson_exchange.md#sbe-equations) becomes
\begin{align}
    W^r = F_0 + F_0 \circ \chi_0^r \circ W^r = F_0 + W^r \circ \chi_0^r \circ F_0 \, ,
\end{align}
i.e. $W^r$ is the ladder of bare vertices in channel $r$, built from the bubble $\chi_0^r$. Equivalently, $W^r = F_0 + F_0 \bullet P^r \bullet W^r$ with the polarization $P^r = \mathbf{1}^r \circ \chi_0^r \circ \mathbf{1}^r$, which is the bubble of channel $r$ with its fermionic argument integrated over.

As on the $GW$ page, we split off the bare interaction and work with the dynamic (decaying) part of the screened interaction,
\begin{align}
    \widetilde{W}^r \equiv W^r - F_0 = \sum_{\ell \geq 1} F_0 \left( \circ\, \chi_0^r \circ F_0 \right)^{\ell} \, ,
\end{align}
where the term with $\ell$ bubbles is of order $\ell + 1$ in the bare interaction. Its first term is the second-order contribution of channel $r$,
\begin{align}
    \Phi^r_{(2)} \equiv F_0 \circ \chi_0^r \circ F_0 \, .
\end{align}

:::{note}
The symbol $\Phi^r_{(2)}$ is the one used in the section on [second-order perturbation theory](second_order_perturbation_theory.md#second-order-vertex), where it is built from the bare bubble $[\chi_0^0]^r$. Here it is built from the same bubble $\chi_0^r$ as the ladders, whichever propagator that bubble contains (see the [variants](#flex-variants) at the end of this page). In the $ph$ channel, the same object is called $\Phi^{(1)}$ in the section on [closed-form ladder resummation](gw_approximation.md#closed-form-ladder-resummation-with-additional-indices), where the parenthesized superscript counts bubbles rather than orders.
:::

The two forms of the Dyson equation imply the *ladder identity*
\begin{align}
    F_0 \circ \chi_0^r \circ \widetilde{W}^r = \widetilde{W}^r \circ \chi_0^r \circ F_0 = \widetilde{W}^r - \Phi^r_{(2)} \, ,
\end{align}
which states that attaching one more bubble and bare vertex to the decaying ladder yields the ladder with at least two bubbles. It is used repeatedly below.

:::{dropdown} Explicit calculation
The Dyson equation can be written as $\widetilde{W}^r = W^r - F_0 = F_0 \circ \chi_0^r \circ W^r$. Inserting $W^r = F_0 + \widetilde{W}^r$ on the right-hand side gives
\begin{align}
    \widetilde{W}^r = F_0 \circ \chi_0^r \circ F_0 + F_0 \circ \chi_0^r \circ \widetilde{W}^r = \Phi^r_{(2)} + F_0 \circ \chi_0^r \circ \widetilde{W}^r \, .
\end{align}
The mirrored form $\widetilde{W}^r = W^r \circ \chi_0^r \circ F_0$ gives $\widetilde{W}^r = \Phi^r_{(2)} + \widetilde{W}^r \circ \chi_0^r \circ F_0$ in the same way. $\checkmark$
:::

### The full vertex

With $\Lambda^{U} \simeq 0$ and $\Delta^r \simeq W^r$, the [SBE decomposition](single_boson_exchange.md#sbe-decomposition) of the full vertex becomes
\begin{align}
    F \simeq \sum_{r \in \{\overline{ph}, pp, ph\}} W^{r} - 2F_0 = F_0 + \widetilde{W}^{\overline{ph}} + \widetilde{W}^{pp} + \widetilde{W}^{ph} \, .
\end{align}
This vertex

- contains the second-order contributions $\Phi^r_{(2)}$ of all three channels and is therefore exact through second order in the bare interaction, cf. the section on [two-particle channels](two-particle-channels.md#bare-and-dressed-bubbles);
- is crossing symmetric, since crossing maps the $ph$ ladder onto the $\overline{ph}$ ladder and the $pp$ ladder onto itself, as shown [below](#flex-crossing);
- first deviates from the exact vertex at third order, where the exact vertex additionally contains the terms $F_0 \circ \chi_0^r \circ \Phi^{r'}_{(2)}$ with $r' \neq r$, in which a bubble of one channel is attached to the second-order contribution of another. These are the lowest-order corrections to the Hedin vertices, which enter through $T^r \supset \Phi^{r'}_{(2)}$ in $\gamma^r = \mathbf{1}^r + \mathbf{1}^r \circ \chi_0^r \circ T^r$.

:::{note} Relation to the parquet approximation
The decaying ladder $\widetilde{W}^r$ is two-particle reducible in channel $r$, so the FLEX vertex corresponds to the parquet decomposition with $\Phi^r \simeq \widetilde{W}^r$. By the ladder identity, $\widetilde{W}^r = F_0 \circ \chi_0^r \circ (F_0 + \widetilde{W}^r)$, which is the [Bethe-Salpeter equation](parquet_theory.md#bethe-salpeter-equations) of channel $r$ with the irreducible vertex $\Gamma^r$ replaced by $F_0$ and the full vertex replaced by $F_0 + \Phi^r$. Each channel is therefore resummed in isolation. The [parquet approximation](parquet_theory.md#parquet-approximation) instead keeps $\Gamma^r = F_0 + \sum_{r' \neq r} \Phi^{r'}$, i.e. the feedback between the channels whose absence is referred to as "ladder bias" on that page. In SBE language, this feedback enters through $T^r$ in the Hedin vertices, which FLEX discards.
:::

(flex-crossing)=
### Crossing symmetry of the ladders

Define the two crossing operations, which exchange the two odd (creation) legs and the two even (annihilation) legs of a four-point object, respectively,
\begin{align}
    (\mathcal{C}_{13} X)_{1234} = \zeta X_{3214} \, , \qquad\qquad (\mathcal{C}_{24} X)_{1234} = \zeta X_{1432} \, .
\end{align}
Both are involutions, and the bare vertex is invariant under both, $\mathcal{C}_{13} F_0 = \mathcal{C}_{24} F_0 = F_0$, by the crossing symmetry stated in the section on the [starting point](starting_point.md). The channel contractions transform as
\begin{align}
    \mathcal{C}_{13}\left( A \circ \chi_0^{ph} \circ B \right) &= (\mathcal{C}_{13} A) \circ \chi_0^{\overline{ph}} \circ (\mathcal{C}_{13} B) \, , \\
    \mathcal{C}_{24}\left( A \circ \chi_0^{ph} \circ B \right) &= (\mathcal{C}_{24} B) \circ \chi_0^{\overline{ph}} \circ (\mathcal{C}_{24} A) \, , \\
    \mathcal{C}_{24}\left( A \circ \chi_0^{pp} \circ B \right) &= A \circ \chi_0^{pp} \circ (\mathcal{C}_{24} B) \, ,
\end{align}
for arbitrary four-point objects $A$ and $B$ and an arbitrary propagator in the bubbles. Applied to the Dyson equations of the ladders, they give
\begin{align}
    W^{\overline{ph}} = \mathcal{C}_{13} W^{ph} = \mathcal{C}_{24} W^{ph} \, , \qquad\qquad W^{pp} = \mathcal{C}_{24} W^{pp} \, ,
\end{align}
and the same relations hold for $\widetilde{W}^r$ and $\Phi^r_{(2)}$, order by order in the number of bubbles. The two particle-hole ladders are crossing images of each other, while the $pp$ ladder is its own crossing image. This is the ladder version of the statement made for the second-order contributions in the section on [two-particle channels](two-particle-channels.md#second-order-perturbation-theory).

:::{dropdown} Explicit calculation
We use the channel contractions with the bubbles written out, as derived in the section on [two-particle channels](two-particle-channels.md#bare-and-dressed-bubbles),
\begin{align}
    [A \circ \chi_0^{\overline{ph}} \circ B]_{1234} &= A_{1256}\, G_{67} G_{85}\, B_{7834} \, , \\
    [A \circ \chi_0^{pp} \circ B]_{1234} &= \frac{1}{2} A_{1536}\, G_{67} G_{58}\, B_{7284} \, , \\
    [A \circ \chi_0^{ph} \circ B]_{1234} &= \zeta A_{5236}\, G_{67} G_{85}\, B_{1874} \, .
\end{align}

**First identity.** On the left-hand side, $\zeta [A \circ \chi_0^{ph} \circ B]_{3214} = \zeta^2 A_{5216}\, G_{67} G_{85}\, B_{3874}$. On the right-hand side, $(\mathcal{C}_{13} A)_{1256}\, G_{67} G_{85}\, (\mathcal{C}_{13} B)_{7834} = \zeta A_{5216}\, G_{67} G_{85}\, \zeta B_{3874}$. Both are equal. $\checkmark$

**Second identity.** On the left-hand side, $\zeta [A \circ \chi_0^{ph} \circ B]_{1432} = \zeta^2 A_{5436}\, G_{67} G_{85}\, B_{1872}$. On the right-hand side, $(\mathcal{C}_{24} B)_{1256}\, G_{67} G_{85}\, (\mathcal{C}_{24} A)_{7834} = \zeta^2 B_{1652}\, G_{67} G_{85}\, A_{7438}$, which turns into the left-hand side upon renaming the summation indices $5 \leftrightarrow 7$ and $6 \leftrightarrow 8$. $\checkmark$

**Third identity.** On the left-hand side, $\zeta [A \circ \chi_0^{pp} \circ B]_{1432} = \frac{1}{2} \zeta A_{1536}\, G_{67} G_{58}\, B_{7482}$. On the right-hand side, $\frac{1}{2} A_{1536}\, G_{67} G_{58}\, (\mathcal{C}_{24} B)_{7284} = \frac{1}{2} A_{1536}\, G_{67} G_{58}\, \zeta B_{7482}$. Both are equal. $\checkmark$

**Ladders.** Applying $\mathcal{C}_{13}$ to $W^{ph} = F_0 + F_0 \circ \chi_0^{ph} \circ W^{ph}$ and using the first identity together with $\mathcal{C}_{13} F_0 = F_0$ gives
\begin{align}
    \mathcal{C}_{13} W^{ph} = F_0 + F_0 \circ \chi_0^{\overline{ph}} \circ \mathcal{C}_{13} W^{ph} \, ,
\end{align}
which is the Dyson equation of the $\overline{ph}$ channel. Its solution is unique order by order in $F_0$, hence $\mathcal{C}_{13} W^{ph} = W^{\overline{ph}}$. Applying $\mathcal{C}_{24}$ to the mirrored form $W^{ph} = F_0 + W^{ph} \circ \chi_0^{ph} \circ F_0$ and using the second identity gives $\mathcal{C}_{24} W^{ph} = F_0 + F_0 \circ \chi_0^{\overline{ph}} \circ \mathcal{C}_{24} W^{ph}$, hence $\mathcal{C}_{24} W^{ph} = W^{\overline{ph}}$ as well. Finally, applying $\mathcal{C}_{24}$ to $W^{pp} = F_0 + F_0 \circ \chi_0^{pp} \circ W^{pp}$ and using the third identity gives $\mathcal{C}_{24} W^{pp} = F_0 + F_0 \circ \chi_0^{pp} \circ \mathcal{C}_{24} W^{pp}$, hence $\mathcal{C}_{24} W^{pp} = W^{pp}$. Since $\mathcal{C}_{13}$ and $\mathcal{C}_{24}$ are linear and leave $F_0$ invariant, the same relations hold for $\widetilde{W}^r = W^r - F_0$, and, term by term in the number of bubbles, for $\Phi^r_{(2)}$. $\checkmark$
:::

(flex-self-energy)=
## The self-energy

### Inserting the vertex into the SDE

We start from the $ph$ form of the [SDE](parquet_theory.md#schwinger-dyson-equation),
\begin{align}
    \Sigma = G \cdot F_0 + \frac{1}{2} G \cdot \left( F \circ \chi_0^{ph} \circ F_0 \right) \, , \qquad\qquad F = F_0 + \widetilde{W}^{\overline{ph}} + \widetilde{W}^{pp} + \widetilde{W}^{ph} \, ,
\end{align}
whose first term is the Hartree term $\Sigma_\mathrm{H}$. The difference to $GW$ becomes explicit at this point. Using the ladder identity for the $ph$ part of $F$,
\begin{align}
    F \circ \chi_0^{ph} \circ F_0 = W^{ph} - F_0 + \left( \widetilde{W}^{\overline{ph}} + \widetilde{W}^{pp} \right) \circ \chi_0^{ph} \circ F_0 \, .
\end{align}
The [SBE identity](single_boson_exchange.md#schwinger-dyson-equation-in-sbe-form) $F \circ \chi_0^{ph} \circ F_0 = \overline{\gamma}^{ph} \bullet W^{ph} - F_0$ with $\overline{\gamma}^{ph} \simeq \mathbf{1}^{ph}$ keeps only the first two terms, which yields $GW$. Inserting the vertex directly keeps the last term as well, through which the other two channels enter the self-energy.

:::{note}
Unlike for $GW$, the choice of the form of the SDE does not matter here: since the FLEX vertex is crossing symmetric, the three forms of the SDE give the same self-energy. This follows from the identities collected in the next subsection and is shown in the dropdown there.
:::

### Splitting into cross terms

Since the SDE is linear in $F$, it is convenient to define, for an arbitrary four-point object $A$, the linear functional
\begin{align}
    \Sigma_\times[A] \equiv \frac{1}{2}\, G \cdot \left( A \circ \chi_0^{ph} \circ F_0 \right) \, .
\end{align}
Inserting the FLEX vertex splits the dynamic part of the self-energy into four terms,
\begin{align}
    \Sigma - \Sigma_\mathrm{H} = \underbrace{\Sigma_\times[F_0]}_{\Sigma^{(2)}} + \underbrace{\Sigma_\times[\widetilde{W}^{\overline{ph}}]}_{\Sigma^{\overline{ph}}_\times} + \underbrace{\Sigma_\times[\widetilde{W}^{pp}]}_{\Sigma^{pp}_\times} + \underbrace{\Sigma_\times[\widetilde{W}^{ph}]}_{\Sigma^{ph}_\times} \, .
\end{align}
The first term, $\Sigma^{(2)} = \frac{1}{2} G \cdot \Phi^{ph}_{(2)}$, is the [second-order self-energy](second_order_perturbation_theory.md#second-order-self-energy), evaluated with the same propagator as everything else. We call the other three the *cross terms* of the three channels. Each $\widetilde{W}^r$ starts at second order, and $\Sigma_\times$ adds one bare vertex, so every cross term starts at third order.

The cross terms are evaluated with three identities, valid for arbitrary four-point objects $X$ and $A$, an arbitrary propagator, and a crossing-symmetric $F_0$:
\begin{align}
    G \cdot X &= \zeta\, (\mathcal{C}_{24} X) \cdot G \, , \\
    \Sigma_\times[\mathcal{C}_{13} A] &= \Sigma_\times[A] \, , \\
    \Sigma_\times[A] &= \zeta \left( F_0 \circ \chi_0^{pp} \circ \mathcal{C}_{24} A \right) \cdot G \, .
\end{align}
The first relates the two [loop products](parquet_theory.md#schwinger-dyson-equation). For a crossing-symmetric $X$ it reduces to the identity $X \cdot G = \zeta\, G \cdot X$ quoted there, but for a single-channel object it does not, which is why the orientation of the loop matters below. The second states that the cross functional does not see whether its argument is crossed in its odd legs. The third states that the cross functional of $A$ equals the $pp$ form of the SDE applied to the crossed argument $\mathcal{C}_{24} A$.

:::{dropdown} Explicit calculation
**Loop orientation.** With the definitions of the [loop products](parquet_theory.md#schwinger-dyson-equation),
\begin{align}
    [(\mathcal{C}_{24} X) \cdot G]_{12} = (\mathcal{C}_{24} X)_{1 \tilde{2} \tilde{1} 2}\, G_{\tilde{2} \tilde{1}} = \zeta X_{1 2 \tilde{1} \tilde{2}}\, G_{\tilde{2} \tilde{1}} = \zeta [G \cdot X]_{12} \, . \ \checkmark
\end{align}

**The cross functional written out.** With the $ph$ contraction of the previous dropdown,
\begin{align}
    \Sigma_\times[A]_{12} = \frac{1}{2} [A \circ \chi_0^{ph} \circ F_0]_{1 2 \tilde{1} \tilde{2}}\, G_{\tilde{2} \tilde{1}} = \frac{1}{2} \zeta\, A_{5 2 \tilde{1} 6}\, G_{67} G_{85} G_{\tilde{2} \tilde{1}}\, F_{0, 1 8 7 \tilde{2}} \, .
\end{align}

**Invariance under $\mathcal{C}_{13}$.** Inserting $(\mathcal{C}_{13} A)_{5 2 \tilde{1} 6} = \zeta A_{\tilde{1} 2 5 6}$ and using the crossing symmetry of the bare vertex in its even legs, $F_{0, 1 8 7 \tilde{2}} = \zeta F_{0, 1 \tilde{2} 7 8}$,
\begin{align}
    \Sigma_\times[\mathcal{C}_{13} A]_{12} = \frac{1}{2} \zeta\, A_{\tilde{1} 2 5 6}\, G_{67} G_{85} G_{\tilde{2} \tilde{1}}\, F_{0, 1 \tilde{2} 7 8} \, .
\end{align}
Renaming the summation indices $5 \leftrightarrow \tilde{1}$ and $8 \leftrightarrow \tilde{2}$ maps $A_{\tilde{1} 2 5 6} \rightarrow A_{5 2 \tilde{1} 6}$, $G_{85} G_{\tilde{2}\tilde{1}} \rightarrow G_{\tilde{2}\tilde{1}} G_{85}$ and $F_{0, 1 \tilde{2} 7 8} \rightarrow F_{0, 1 8 7 \tilde{2}}$, which is $\Sigma_\times[A]_{12}$. $\checkmark$

**Relation to the $pp$ form.** With the $pp$ contraction, $(\mathcal{C}_{24} A)_{7 \tilde{2} 8 2} = \zeta A_{7 2 8 \tilde{2}}$, and $F_{0, 1 5 \tilde{1} 6} = \zeta F_{0, 1 6 \tilde{1} 5}$,
\begin{align}
    \zeta \left[ \left( F_0 \circ \chi_0^{pp} \circ \mathcal{C}_{24} A \right) \cdot G \right]_{12}
    &= \zeta\, \frac{1}{2} F_{0, 1 5 \tilde{1} 6}\, G_{67} G_{58}\, (\mathcal{C}_{24} A)_{7 \tilde{2} 8 2}\, G_{\tilde{2} \tilde{1}} \\
    &= \frac{1}{2} \zeta\, F_{0, 1 6 \tilde{1} 5}\, G_{67} G_{58} G_{\tilde{2} \tilde{1}}\, A_{7 2 8 \tilde{2}} \, .
\end{align}
Renaming the summation indices $5 \rightarrow \tilde{2}$, $6 \rightarrow 8$, $7 \rightarrow 5$, $8 \rightarrow \tilde{1}$, $\tilde{1} \rightarrow 7$, $\tilde{2} \rightarrow 6$ maps $F_{0, 1 6 \tilde{1} 5} \rightarrow F_{0, 1 8 7 \tilde{2}}$, $A_{7 2 8 \tilde{2}} \rightarrow A_{5 2 \tilde{1} 6}$ and $G_{67} G_{58} G_{\tilde{2}\tilde{1}} \rightarrow G_{85} G_{\tilde{2}\tilde{1}} G_{67}$, which is $\Sigma_\times[A]_{12}$. $\checkmark$

**The three forms of the SDE agree for the FLEX vertex.** For a crossing-symmetric vertex, $\mathcal{C}_{24} F = F$, so the third identity gives $\Sigma_\times[F] = \zeta (F_0 \circ \chi_0^{pp} \circ F) \cdot G$, which is the dynamic part of the $pp$ form of the SDE. For the $\overline{ph}$ form, the loop orientation in the form $\zeta\, Y \cdot G = G \cdot (\mathcal{C}_{24} Y)$, together with the second contraction identity of the [crossing section](#flex-crossing) in the form $\mathcal{C}_{24}(A \circ \chi_0^{\overline{ph}} \circ B) = (\mathcal{C}_{24} B) \circ \chi_0^{ph} \circ (\mathcal{C}_{24} A)$, gives
\begin{align}
    \frac{1}{2} \zeta \left( F_0 \circ \chi_0^{\overline{ph}} \circ F \right) \cdot G = \frac{1}{2} G \cdot \mathcal{C}_{24}\left( F_0 \circ \chi_0^{\overline{ph}} \circ F \right) = \frac{1}{2} G \cdot \left( F \circ \chi_0^{ph} \circ F_0 \right) = \Sigma_\times[F] \, .
\end{align}
The Hartree terms agree as well, $\zeta F_0 \cdot G = G \cdot F_0$, by the loop orientation and $\mathcal{C}_{24} F_0 = F_0$. $\checkmark$
:::

(flex-ph-cross-term)=
### The $ph$ cross term

By the ladder identity, $\widetilde{W}^{ph} \circ \chi_0^{ph} \circ F_0 = \widetilde{W}^{ph} - \Phi^{ph}_{(2)}$, and therefore
\begin{align}
    \Sigma^{ph}_\times = \frac{1}{2}\, G \cdot \left( \widetilde{W}^{ph} - \Phi^{ph}_{(2)} \right) \, .
\end{align}

### The $\overline{ph}$ cross term equals the $ph$ cross term

Since $\widetilde{W}^{\overline{ph}} = \mathcal{C}_{13} \widetilde{W}^{ph}$ and the cross functional is invariant under $\mathcal{C}_{13}$,
\begin{align}
    \Sigma^{\overline{ph}}_\times = \Sigma_\times[\mathcal{C}_{13} \widetilde{W}^{ph}] = \Sigma_\times[\widetilde{W}^{ph}] = \Sigma^{ph}_\times \, .
\end{align}
The two cross terms consist of distinct diagrams, but they are equal: closing the transverse ladder with one more $ph$ bubble produces the same ring diagrams as closing the $ph$ ladder, opened at a different internal line. In practice, no object of the $\overline{ph}$ channel has to be computed at all.

:::{note}
This statement uses nothing but the crossing symmetry of $F_0$ and a relabeling of summation indices. It therefore holds for any propagator in the bubbles and with any additional indices on the multi-indices, in particular in the Keldysh formalism.
:::

### The $pp$ cross term

Since $\widetilde{W}^{pp} = \mathcal{C}_{24} \widetilde{W}^{pp}$, the relation of the cross functional to the $pp$ form of the SDE, followed by the ladder identity, gives
\begin{align}
    \Sigma^{pp}_\times = \zeta \left( F_0 \circ \chi_0^{pp} \circ \widetilde{W}^{pp} \right) \cdot G = \zeta \left( \widetilde{W}^{pp} - \Phi^{pp}_{(2)} \right) \cdot G \, .
\end{align}
For $A = F_0$ the same identity yields $\Sigma^{(2)} = \zeta\, \Phi^{pp}_{(2)} \cdot G$: the $pp$ loop of the second-order $pp$ contribution is the same second-order self-energy, as it must be, since this is the $pp$ form of the SDE at lowest order.

:::{warning}
The $ph$ cross term comes with the loop product $G \cdot X$ and the $pp$ cross term with $X \cdot G$. For single-channel objects these two loop products are *not* interchangeable: they project onto different [spin combinations](gw_approximation.md#spin-projection-of-the-loop-products) and close different legs of $X$. The orientation is therefore part of the result. The $pp$ bracket is special in that it is $\mathcal{C}_{24}$ symmetric, so that by the loop orientation identity $\zeta\, X \cdot G = G \cdot X$ holds for it. Either form may then be used, provided its own spin projection and its own frequency arguments are used along with it.
:::

(flex-result)=
### Result

Collecting the three cross terms, and using $\Sigma^{\overline{ph}}_\times + \Sigma^{ph}_\times = 2 \Sigma^{ph}_\times$, the FLEX self-energy reads
\begin{align}
    \boxed{\ \Sigma - \Sigma_\mathrm{H} = \Sigma^{(2)} + G \cdot \left( \widetilde{W}^{ph} - \Phi^{ph}_{(2)} \right) + \zeta \left( \widetilde{W}^{pp} - \Phi^{pp}_{(2)} \right) \cdot G \ } \, .
\end{align}
In words: the second-order self-energy appears exactly once, and on top of it the particle-hole ladders and the particle-particle ladder contribute with at least two bubbles each.

The same result reads differently if each cross term is grouped with a copy of the second-order term. Define the *$GW$-type self-energy of channel $r$* as
\begin{align}
    \Sigma^{r}_{GW} \equiv \Sigma^{(2)} + \Sigma^{r}_{\times} \, .
\end{align}
It is the dynamic part of the self-energy that the SDE in the form native to channel $r$ yields with a unit Hedin vertex, i.e. of the three expressions discussed in the section on [which form of the SDE](gw_approximation.md#which-form-of-the-schwinger-dyson-equation):
\begin{align}
    \Sigma^{ph}_{GW} = \frac{1}{2}\, G \cdot \widetilde{W}^{ph} \, , \qquad
    \Sigma^{\overline{ph}}_{GW} = \frac{1}{2} \zeta\, \widetilde{W}^{\overline{ph}} \cdot G \, , \qquad
    \Sigma^{pp}_{GW} = \zeta\, \widetilde{W}^{pp} \cdot G \, .
\end{align}
The FLEX self-energy is then
\begin{align}
    \Sigma - \Sigma_\mathrm{H} = \Sigma^{ph}_{GW} + \Sigma^{\overline{ph}}_{GW} + \Sigma^{pp}_{GW} - 2\, \Sigma^{(2)} \, ,
\end{align}
which is the form quoted at the top of this page. Each of the three $\Sigma^{r}_{GW}$ contains the second-order diagram as its lowest term, and two of the three copies are subtracted. $\Sigma^{ph}_{GW}$ is the dynamic part of the $GW$ self-energy, and $\Sigma^{pp}_{GW}$ that of the $T$-matrix approximation.

:::{dropdown} Explicit calculation
For the $ph$ channel, $\Sigma^{(2)} + \Sigma^{ph}_\times = \frac{1}{2} G \cdot \Phi^{ph}_{(2)} + \frac{1}{2} G \cdot (\widetilde{W}^{ph} - \Phi^{ph}_{(2)}) = \frac{1}{2} G \cdot \widetilde{W}^{ph}$. For the $pp$ channel, using $\Sigma^{(2)} = \zeta\, \Phi^{pp}_{(2)} \cdot G$, $\Sigma^{(2)} + \Sigma^{pp}_\times = \zeta\, \widetilde{W}^{pp} \cdot G$. For the $\overline{ph}$ channel, the loop orientation identity and $\mathcal{C}_{24} \widetilde{W}^{\overline{ph}} = \widetilde{W}^{ph}$ give $\frac{1}{2} \zeta\, \widetilde{W}^{\overline{ph}} \cdot G = \frac{1}{2} G \cdot \widetilde{W}^{ph} = \Sigma^{(2)} + \Sigma^{ph}_\times = \Sigma^{(2)} + \Sigma^{\overline{ph}}_\times$. This reproduces the result of the $GW$ page that the two particle-hole forms of $GW$ agree.

That these are the dynamic parts of the three expressions on the $GW$ page follows from $W^r = F_0 + \widetilde{W}^r$: for instance $\frac{1}{2} G \cdot (F_0 + W^{ph}) = G \cdot F_0 + \frac{1}{2} G \cdot \widetilde{W}^{ph}$ and $\zeta\, W^{pp} \cdot G = \zeta F_0 \cdot G + \zeta\, \widetilde{W}^{pp} \cdot G$, where the first terms are the Hartree term in its $ph$ and $pp$ forms. $\checkmark$
:::

(flex-explicit-form)=
## Spin structure and explicit form

From here on, we work within the [scope](#flex-scope) of scalar objects, i.e. in the Matsubara formalism and for a single band.

(flex-screened-interactions)=
### Screened interactions

The polarization $P^r$ carries the spin structure of the unit vertex $\mathbf{1}^r$, so the ladder of each channel decouples in the same spin basis as the corresponding bubble contraction, see the section on [spin parametrizations](spin_parametrizations.md) and the spin table in the section on [second-order perturbation theory](second_order_perturbation_theory.md#spin-structure). With the bare interaction of the Hubbard model,

- the $ph$ ladder decouples in the density/magnetic basis, with $F_{0,d} = -U$ and $F_{0,m} = +U$;
- the $\overline{ph}$ ladder decouples in the combinations $X_\pm = X_{\uparrow\uparrow} \pm X_{\overline{\uparrow\downarrow}}$, with $F_{0,\pm} = \pm U$;
- the $pp$ ladder decouples in the singlet/triplet basis, with $F_{0,s} = -2U$ and $F_{0,t} = 0$.

The $ph$ ladders are those of the [$GW$ approximation](gw_approximation.md#polarization-and-screened-interaction-in-the-ph-channel),
\begin{align}
    \widetilde{W}_{d}(\omega) = \frac{U^2 P^{ph}(\omega)}{1 + U P^{ph}(\omega)} = U^2 \chi_d(\omega) \, , \qquad
    \widetilde{W}_{m}(\omega) = \frac{U^2 P^{ph}(\omega)}{1 - U P^{ph}(\omega)} = U^2 \chi_m(\omega) \, , \qquad
    P^{ph}(\omega) = \zeta \int_\nu G(\nu) G(\nu + \omega) \, ,
\end{align}
where a spin label $d$ or $m$ unambiguously refers to the $ph$ channel. The $\overline{ph}$ ladders follow from them by crossing, $\widetilde{W}^{\overline{ph}}_{\pm} = -\widetilde{W}_{d/m}$, which is the decaying part of the relation $W^{\overline{ph}}_{\pm} = -W^{ph}_{d/m}$ found on the [$GW$ page](gw_approximation.md#which-form-of-the-schwinger-dyson-equation), but they are not needed. In the $pp$ channel, the singlet ladder is
\begin{align}
    \boxed{\ \widetilde{W}_{s}(\omega) = \frac{F_{0,s}^2\, P^{pp}(\omega)}{1 - F_{0,s} P^{pp}(\omega)} = \frac{4 U^2 P^{pp}(\omega)}{1 + 2 U P^{pp}(\omega)} \, , \qquad P^{pp}(\omega) = \frac{1}{2} \int_\nu G(\nu) G(-\nu - \omega) \ } \, ,
\end{align}
and its one-bubble term is $\Phi^{pp}_{(2),s} = 4U^2 P^{pp}$, in agreement with the section on [second-order perturbation theory](second_order_perturbation_theory.md#spin-structure). The triplet ladder vanishes identically,
\begin{align}
    W^{pp}_{t} = 0 \, ,
\end{align}
since its Dyson equation $W^{pp}_{t} = F_{0,t} + F_{0,t} \bullet P^{pp} \bullet W^{pp}_{t}$ has both a vanishing inhomogeneity and a vanishing kernel. This is the ladder version of the statement that a local interaction does not act in the triplet $pp$ channel, since two electrons of equal spin cannot occupy the same site.

:::{dropdown} Explicit calculation
The unit vertex of the $pp$ channel has the spin part of the [identity operator](two-particle-channels.md#connectors-and-identity-operators) $\mathbb{1}^{pp}_{1234} = \delta_{14}\delta_{23}$, i.e. $\delta_{\sigma_1, \sigma_4}\delta_{\sigma_2, \sigma_3}$. Its components are $\mathbf{1}^{pp}_{\uparrow\uparrow} = 1$, $\mathbf{1}^{pp}_{\uparrow\downarrow} = 1$ and $\mathbf{1}^{pp}_{\overline{\uparrow\downarrow}} = 0$, so that $\mathbf{1}^{pp}_{s} = \mathbf{1}^{pp}_{\uparrow\downarrow} - \mathbf{1}^{pp}_{\overline{\uparrow\downarrow}} = 1$ and $\mathbf{1}^{pp}_{t} = \mathbf{1}^{pp}_{\uparrow\uparrow} = 1$. The polarization therefore has the same, spin-independent value $P^{pp}$ in the singlet and the triplet channel.

For its frequency dependence, we insert the frequency-independent unit vertices into the $pp$ bubble contraction of the section on [frequency parametrizations](frequency_parametrizations.md),
\begin{align}
    [A \circ \chi_0^{pp} \circ B](\nu, \nu', \omega) = \frac{1}{2} \int_{\nu''} A(\nu, \nu'', \omega)\, G(\nu'') G(-\nu'' - \omega)\, B(\nu'', \nu', \omega) \, ,
\end{align}
which leaves $P^{pp}(\omega) = \frac{1}{2} \int_\nu G(\nu) G(-\nu - \omega)$. With the [decoupling](spin_parametrizations.md) $[A \circ \chi_0^{pp} \circ B]_{s/t} = A_{s/t} \bullet \chi_0^{pp} \bullet B_{s/t}$, the bosonic Dyson equation reduces to the two scalar equations
\begin{align}
    W^{pp}_{s/t}(\omega) = F_{0,s/t} + F_{0,s/t}\, P^{pp}(\omega)\, W^{pp}_{s/t}(\omega) \, ,
\end{align}
with the solutions $W^{pp}_{s} = F_{0,s} / (1 - F_{0,s} P^{pp}) = -2U / (1 + 2U P^{pp})$ and $W^{pp}_{t} = 0$. Subtracting $F_{0,s}$ gives
\begin{align}
    \widetilde{W}_{s} = \frac{F_{0,s}}{1 - F_{0,s} P^{pp}} - F_{0,s} = \frac{F_{0,s}^2\, P^{pp}}{1 - F_{0,s} P^{pp}} \, ,
\end{align}
whose expansion starts with $F_{0,s}^2 P^{pp} = 4U^2 P^{pp} = \Phi^{pp}_{(2),s}$. $\checkmark$
:::

:::{important} Cooper instability
The singlet ladder becomes singular where $1 + 2U P^{pp}(\omega) = 0$. In the static limit and in the Matsubara formalism, $G(-\nu) = G(\nu)^*$ gives
\begin{align}
    P^{pp}(0) = \frac{1}{2} \int_\nu G(\nu) G(-\nu) = \frac{1}{2} \int_\nu \left| G(\nu) \right|^2 > 0 \, ,
\end{align}
so the static singlet ladder can become singular only for an attractive interaction, $U < 0$. This is the ($s$-wave) Cooper instability of the attractive Hubbard model, the $pp$ counterpart of the [Stoner criterion](gw_approximation.md#stoner-criterion) in the magnetic channel. For repulsive $U$ the static $pp$ ladder is regular, and its geometric series alternates in sign. Pairing instabilities with a nontrivial momentum structure, for which FLEX is often used, are not signaled by $W^{pp}$ itself; they are studied with a separate linearized gap equation, which is not covered on this page.
:::

:::{note}
With additional indices (see the [scope](#flex-scope)), the $pp$ ladder is summed by a pointwise matrix inversion in the same way as the $ph$ ladder. The two rungs contract different legs, however: in $F_0 \circ \chi_0^{ph} \circ X$ the legs 1 and 4 of the result are those of $X$, whereas in $F_0 \circ \chi_0^{pp} \circ X$ the legs 2 and 4 are, as can be read off from the channel connectors. The block structure of the rung described in the section on [closed-form ladder resummation](gw_approximation.md#closed-form-ladder-resummation-with-additional-indices) therefore involves a different pair of spectator indices for $pp$. The vanishing of the triplet ladder carries over as long as the additional indices do not open a triplet component of the bare interaction. This is the case for Keldysh indices, but not in general for orbital indices, where an interorbital interaction can act between electrons of equal spin.
:::

### Self-energy

The two loop products project onto different spin combinations, as derived in the section on the [spin projection of the loop products](gw_approximation.md#spin-projection-of-the-loop-products). For the $ph$ term,
\begin{align}
    [G \cdot X] \ \longrightarrow \ X_{\uparrow\uparrow} + X_{\overline{\uparrow\downarrow}} = \frac{1}{2}\left( X_d + 3 X_m \right) \, ,
\end{align}
and for the $pp$ term, expressing the same projection as on that page in the singlet/triplet basis, $X_{\uparrow\uparrow} = X_t$ and $X_{\uparrow\downarrow} = \frac{1}{2}(X_s + X_t)$,
\begin{align}
    [X \cdot G] \ \longrightarrow \ X_{\uparrow\uparrow} + X_{\uparrow\downarrow} = \frac{1}{2} X_s + \frac{3}{2} X_t \, .
\end{align}
The $ph$ loop closes the two legs of a $ph$ object that carry its transfer frequency, which then takes the value $\nu - \nu'$, as shown in the section on the [frequency parametrization of the closing loop](second_order_perturbation_theory.md#frequency-parametrization-of-the-closing-loop). The $pp$ loop evaluates a $pp$ object at the $pp$ transfer frequency $-\nu - \nu'$ (derived below). With $W^{pp}_t = 0$ and $\Phi^{ph}_{(2),d} = \Phi^{ph}_{(2),m}$, the FLEX self-energy becomes
\begin{align}
    \boxed{\ \Sigma(\nu) - \Sigma_\mathrm{H} = \int_{\nu'} G(\nu') \left\{ \left[ \frac{1}{2}\widetilde{W}_{d} + \frac{3}{2}\widetilde{W}_{m} - \Phi^{ph}_{(2),d} \right](\nu - \nu') + \frac{1}{2} \zeta \left[ \widetilde{W}_{s} - \Phi^{pp}_{(2),s} \right](-\nu - \nu') \right\} \ } \, ,
\end{align}
where the spin sums have been carried out.

:::{dropdown} Explicit calculation
**Spin.** The $ph$ terms of the boxed result in compact notation are $\Sigma^{(2)} + G \cdot (\widetilde{W}^{ph} - \Phi^{ph}_{(2)})$. With $\Sigma^{(2)} = \frac{1}{2} G \cdot \Phi^{ph}_{(2)}$, the spin projection gives
\begin{align}
    \frac{1}{4}\left( \Phi^{ph}_{(2),d} + 3 \Phi^{ph}_{(2),m} \right) + \frac{1}{2}\left( \widetilde{W}_{d} - \Phi^{ph}_{(2),d} \right) + \frac{3}{2}\left( \widetilde{W}_{m} - \Phi^{ph}_{(2),m} \right)
    = \frac{1}{2}\widetilde{W}_{d} + \frac{3}{2}\widetilde{W}_{m} - \Phi^{ph}_{(2),d} \, ,
\end{align}
where we used $\Phi^{ph}_{(2),d} = \Phi^{ph}_{(2),m}$. The $pp$ term $\zeta (\widetilde{W}^{pp} - \Phi^{pp}_{(2)}) \cdot G$ gives $\frac{1}{2} \zeta (\widetilde{W}_{s} - \Phi^{pp}_{(2),s})$, since its triplet component vanishes.

**Frequency of the $pp$ loop.** Write the loop product with explicit frequency arguments, $[X \cdot G]_{12} = X_{1 \tilde{2} \tilde{1} 2}\, G_{\tilde{2} \tilde{1}}$, with $\Sigma_{12} = \Sigma(\nu_2)\, \delta(\nu_1 + \nu_2)$ and $G_{\tilde{2} \tilde{1}} = G(\nu_{\tilde{2}})\, \delta(\nu_{\tilde{2}} + \nu_{\tilde{1}})$, as in the section on the [frequency parametrization of the closing loop](second_order_perturbation_theory.md#frequency-parametrization-of-the-closing-loop). The external frequency is $\nu = \nu_2 = -\nu_1$ and the loop frequency is $\nu' = \nu_{\tilde{2}} = -\nu_{\tilde{1}}$. The four legs of $X_{1 \tilde{2} \tilde{1} 2}$ carry the frequencies $(-\nu, \nu', -\nu', \nu)$. In the $pp$-native parametrization of the section on [frequency parametrizations](frequency_parametrizations.md), $\nu_{pp} = -\nu_1$, $\nu'_{pp} = \nu_4$ and $\omega_{pp} = \nu_1 + \nu_3$, read off from the legs of $X$, this is
\begin{align}
    \nu_{pp} = \nu \, , \qquad \nu'_{pp} = \nu \, , \qquad \omega_{pp} = -\nu - \nu' \, ,
\end{align}
and therefore
\begin{align}
    [X \cdot G](\nu) = \int_{\nu'} X^{pp}(\nu, \nu, -\nu - \nu')\, G(\nu') \, .
\end{align}
Since the screened interaction depends on the bosonic frequency only, $X^{pp}(\nu, \nu, \omega) = \widetilde{W}^{pp}(\omega)$ with $\omega = -\nu - \nu'$. $\checkmark$
:::

:::{note}
The bosonic argument $-\nu - \nu'$ of the $pp$ term is the $pp$ transfer frequency $\omega_{pp} = \nu_1 + \nu_3$ of the house convention. Written with $\Omega = -\omega$, the polarization reads $P^{pp}(-\Omega) = \frac{1}{2} \int_\nu G(\nu) G(\Omega - \nu)$, the propagator of a particle pair with total frequency $\Omega$. In terms of this total frequency, the $pp$ term is evaluated at $\Omega = \nu + \nu'$, which is how the $T$-matrix contribution usually appears in the literature.
:::

Inserting the scalar ladders of the [previous subsection](#flex-screened-interactions), $\widetilde{W}_{d/m} = U^2 \chi_{d/m}$, $\Phi^{ph}_{(2),d} = U^2 P^{ph}$ and $\widetilde{W}_{s} - \Phi^{pp}_{(2),s} = -8U^3 (P^{pp})^2 / (1 + 2U P^{pp})$, and setting $\zeta = -1$, gives the form in which the FLEX self-energy is most easily recognized,
\begin{align}
    \Sigma(\nu) = U n + U^2 \int_{\nu'} G(\nu') \left[ \frac{1}{2} \chi_d + \frac{3}{2} \chi_m - P^{ph} \right]\!(\nu - \nu') + 4 U^3 \int_{\nu'} G(\nu') \left[ \frac{\left(P^{pp}\right)^2}{1 + 2U P^{pp}} \right]\!(-\nu - \nu') \, ,
\end{align}
with the Hartree term $\Sigma_\mathrm{H} = U n$ and the density per spin $n$, as on the [$GW$ page](gw_approximation.md#frequency-parametrization). For comparison, the $GW$ self-energy derived there is $\Sigma(\nu) = U n + U^2 \int_{\nu'} G(\nu') \left[ \frac{1}{4} \chi_d + \frac{3}{4} \chi_m \right](\nu - \nu')$.

## Order counting

Expanding the two kernels in powers of $U$, with $\chi_{d/m} = P^{ph} \mp U (P^{ph})^2 + \mathcal{O}(U^2)$,
\begin{align}
    U^2 \left[ \frac{1}{2} \chi_d + \frac{3}{2} \chi_m - P^{ph} \right] &= U^2 P^{ph} + U^3 \left(P^{ph}\right)^2 + \mathcal{O}(U^4) \, , \\
    4 U^3 \frac{\left(P^{pp}\right)^2}{1 + 2U P^{pp}} &= 4 U^3 \left(P^{pp}\right)^2 + \mathcal{O}(U^4) \, .
\end{align}
At second order, only the $ph$ kernel contributes, with weight $\frac{1}{2} + \frac{3}{2} - 1 = 1$, and yields $\Sigma^{(2)}$. At third order, both kernels contribute. As a functional of the propagator in its bubbles and loops, the FLEX self-energy is **exact through third order**: the vertex is exact through second order, and the SDE requires the vertex to one order less than the self-energy. $GW$ is not: its kernel $\frac{1}{4}\widetilde{W}_d + \frac{3}{4}\widetilde{W}_m = U^2 P^{ph} + \frac{1}{2} U^3 (P^{ph})^2 + \mathcal{O}(U^4)$, given in the section on [reduction to second-order perturbation theory](gw_approximation.md#reduction-to-second-order-perturbation-theory), contains half of the third-order $ph$ term and none of the third-order $pp$ term. In the compact notation, $GW$ keeps $\Sigma^{(2)} + \Sigma^{ph}_\times$ and misses $\Sigma^{\overline{ph}}_\times$ and $\Sigma^{pp}_\times$, which both start at third order.

A useful check follows at particle-hole symmetry, where the two third-order contributions of FLEX cancel exactly. Since FLEX contains the complete third-order term, this is the statement that the third-order term of the dynamic self-energy vanishes at particle-hole symmetry. $GW$, which keeps only half of the third-order $ph$ term and none of the $pp$ term, does not reproduce this zero.

:::{dropdown} Explicit calculation
Consider a purely frequency-dependent propagator with particle-hole symmetry, $G(-\nu) = -G(\nu)$, e.g. that of an impurity model at half filling. Then
\begin{align}
    P^{pp}(\omega) = \frac{1}{2} \int_\nu G(\nu) G(-\nu - \omega) = -\frac{1}{2} \int_\nu G(\nu) G(\nu + \omega) = \frac{1}{2} P^{ph}(\omega) \, ,
\end{align}
using $\zeta = -1$, so that $4 (P^{pp})^2 = (P^{ph})^2$. The third-order $pp$ contribution becomes, after substituting $\nu' \rightarrow -\nu'$ and using $G(-\nu') = -G(\nu')$,
\begin{align}
    U^3 \int_{\nu'} G(\nu')\, P^{ph}(-\nu - \nu')^2 = U^3 \int_{\nu'} G(-\nu')\, P^{ph}(\nu' - \nu)^2 = - U^3 \int_{\nu'} G(\nu')\, P^{ph}(\nu - \nu')^2 \, ,
\end{align}
where we used in the last step that $P^{ph}$ is even, $P^{ph}(-\omega) = P^{ph}(\omega)$, as follows from shifting the integration variable. This cancels the third-order $ph$ contribution $U^3 \int_{\nu'} G(\nu')\, P^{ph}(\nu - \nu')^2$ exactly. $\checkmark$
:::

(flex-literature)=
## Comparison with the literature

In the FLEX literature, the particle-hole part of the self-energy is usually written in terms of a fluctuation-exchange interaction of the form
\begin{align}
    U^2 \left[ \frac{3}{2} \chi_\mathrm{sp} + \frac{1}{2} \chi_\mathrm{ch} - \chi_0 \right] \, ,
\end{align}
which matches the $ph$ kernel above with $\chi_\mathrm{sp} = \chi_m$, $\chi_\mathrm{ch} = \chi_d$ and $\chi_0 = P^{ph}$. The term $-\chi_0$ is the subtraction of the double-counted second-order diagram. Variants of FLEX that keep only the particle-hole fluctuations are also in use; in the notation of this page, they correspond to dropping the $pp$ term, which removes the third-order $pp$ contribution.

:::{warning}
In the FLEX literature, the subscript $s$ (or "sp") usually denotes the *spin* susceptibility, i.e. the magnetic channel $m$ of this page, and $c$ (or "ch") the *charge* susceptibility, i.e. the density channel $d$. Here, the subscript $s$ denotes the *singlet* $pp$ channel. Furthermore, the $pp$ bubble is often defined without the factor $\frac{1}{2}$ that our [channel bubble](two-particle-channels.md#bare-and-dressed-bubbles) $\chi_0^{pp}$ carries. In terms of $\chi_\mathrm{pp}(\Omega) = \int_\nu G(\nu) G(\Omega - \nu) = 2 P^{pp}(-\Omega)$, the $pp$ term reads $U^3 \chi_\mathrm{pp}^2 / (1 + U \chi_\mathrm{pp})$, evaluated at $\Omega = \nu + \nu'$.
:::

The structure of the result can also be compared with the decomposition of the *exact* self-energy of the Hubbard model by [Y. Yu, S. Iskakov, E. Gull, K. Held and F. Krien, arXiv:2401.08543](https://arxiv.org/abs/2401.08543), Eqs. (1) and (2),
\begin{align}
    \Sigma - \Sigma^{\mathrm{H}} = \Sigma^{\mathrm{2nd}} + \Sigma^{\mathrm{ch}} + \Sigma^{\mathrm{sp}} + \Sigma^{\mathrm{si}} + \Sigma^{\mathrm{mb}} \, ,
\end{align}
in which each fluctuation channel contributes a term with a Hedin vertex and a susceptibility, minus a multiple of the second-order self-energy, and $\Sigma^{\mathrm{mb}}$ collects the multi-boson diagrams. The authors note the similarity to FLEX, in which the Hedin vertices are set to their non-interacting values and the multi-boson term is absent. The result of this page has exactly this structure:

| Yu *et al.* | this page | weight of the subtracted $\Sigma^{(2)}$ |
| --- | --- | --- |
| $\Sigma^{\mathrm{ch}}$ | $\frac{1}{2}\left(\widetilde{W}_{d} - \Phi^{ph}_{(2),d}\right)$ in the $ph$ loop, from $\Sigma^{ph}_\times + \Sigma^{\overline{ph}}_\times$ | $\frac{1}{2}$ |
| $\Sigma^{\mathrm{sp}}$ | $\frac{3}{2}\left(\widetilde{W}_{m} - \Phi^{ph}_{(2),m}\right)$ in the $ph$ loop, from $\Sigma^{ph}_\times + \Sigma^{\overline{ph}}_\times$ | $\frac{3}{2}$ |
| $\Sigma^{\mathrm{si}}$ | $\frac{1}{2}\zeta\left(\widetilde{W}_{s} - \Phi^{pp}_{(2),s}\right)$ in the $pp$ loop, i.e. $\Sigma^{pp}_\times$ | $1$ |
| $\Sigma^{\mathrm{mb}}$ | absent, since $\Lambda^{U} \simeq 0$ and $\gamma^r \simeq \mathbf{1}^r$ | - |

Their charge and spin terms combine the two particle-hole channels, just as $\Sigma^{ph}_\times + \Sigma^{\overline{ph}}_\times = 2 \Sigma^{ph}_\times$ does here.

:::{danger} To do
The comparisons above cover the structure and the weights only. Check the overall signs and the frequency and momentum labels against the original papers of Bickers, Scalapino and White and against the normalization of $\chi$ and $\gamma$ used by Yu *et al.*, whose non-interacting Hedin vertices take the values $1$, $1$ and $-1$ in the charge, spin and singlet channel.
:::

(flex-variants)=
## Variants: one-shot and self-consistent FLEX

As for [$GW$](gw_approximation.md#gw-variants), the equations above do not specify which propagator enters the bubbles $\chi_0^r$ and the self-energy loops:

- **one-shot FLEX**: the bare propagator $G_0$ is used everywhere, and the self-energy is evaluated once.
- **self-consistent FLEX**: the full propagator, obtained from the Dyson equation with the current self-energy, is used in all bubbles and loops, and the equations are iterated to convergence. This is the FLEX approximation of Bickers and Scalapino, who constructed it as a conserving approximation in the sense of Baym and Kadanoff, from a Luttinger-Ward functional built from the ring and ladder diagrams.

In both cases, $\Sigma^{(2)}$ and $\Phi^r_{(2)}$ are evaluated with the same propagator as the ladders, so that the subtraction of the double-counted second-order term is exact.

:::{danger} To do
- Add diagrammatic representations of the three ladders, the cross terms and the FLEX self-energy.
- Derive the Luttinger-Ward functional of FLEX and show that the self-energy above is its functional derivative, which establishes the conserving property of the self-consistent variant.
- Discuss what changes for a non-local or retarded bare interaction, where $F_{0,m} = -F_{0,d}$ and $F_{0,t} = 0$ no longer hold, so that the triplet ladder contributes.
- Add the linearized gap (Eliashberg) equation with the FLEX pairing interaction.
:::
