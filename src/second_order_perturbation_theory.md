# Second-order perturbation theory

Second-order perturbation theory in the bare interaction is the simplest nontrivial approximation for both the two-particle vertex and the self-energy. It is worth writing out completely, for three reasons: it is the standard starting point for iterating the [parquet equations](parquet_theory.md), it is the natural benchmark against which any implementation of those equations should be validated, and it is the order at which all the prefactors — the crossing factors of the channel bubbles, the spin sums, and the $\frac{1}{2}$ of the [Schwinger-Dyson equation](parquet_theory.md#schwinger-dyson-equation) — can still be tracked by hand.

The purpose of this page is to carry the second-order vertex and the second-order self-energy all the way down to explicit formulas, with every prefactor, spin sum, frequency argument and Keldysh index in place. The single most error-prone step is the spin sum of the self-energy loop: it contributes a factor $2$ that cancels the $\frac{1}{2}$ of the SDE exactly, so that **the dynamic second-order self-energy carries no numerical prefactor at all**.

:::{note}
The spin structure of the bare interaction and the spin projection of the loop products are derived in the section on the [$GW$ approximation](gw_approximation.md), and we simply quote the results here. That page works in the Matsubara formalism and in the $ph$ channel only; this page treats all three channels and adds the Keldysh index structure.
:::

:::{note}
The spin and frequency algebra below is written for frequencies only. As explained in the section on [frequency parametrizations](frequency_parametrizations.md), every statement carries over verbatim to the momentum dependence by replacing $\nu, \nu', \omega \rightarrow \mathbf{k}, \mathbf{k}', \mathbf{q}$. The momenta are reinstated explicitly in the collected results at the end of each part, since that is the form one compares an implementation against.
:::

We specialize throughout to a system with SU(2) spin symmetry and a *local and instantaneous* bare interaction, i.e. the Hubbard interaction of the [Hubbard model example](starting_point.md#example-hubbard-model), whose spin components are
\begin{align}
    F_{0,\uparrow\downarrow} &= -U \, , &
    F_{0,\overline{\uparrow\downarrow}} &= +U \, , &
    F_{0,\uparrow\uparrow} &= 0 \, ,
\end{align}
and hence
\begin{align}
    F_{0,d} &= -U \, , & F_{0,m} &= +U \, , & F_{0,s} &= -2U \, , & F_{0,t} &= 0 \, .
\end{align}

## Second-order vertex

As derived in the section on [two-particle channels](two-particle-channels.md#second-order-perturbation-theory), the second-order vertex is the sum of the bare vertex and one contribution per channel,
\begin{align}
    F = F_0 + \sum_{r \in \{\overline{ph},\, pp,\, ph\}} \Phi^r_{(2)} + \mathcal{O}(F_0^3) \, , \qquad\qquad
    \Phi^r_{(2)} \equiv F_0 \circ [\chi_0^{0}]^r \circ F_0 \, ,
\end{align}
where $[\chi_0^{0}]^r$ is the [bare bubble](two-particle-channels.md#bare-and-dressed-bubbles) in channel $r$. Written out with the channel connectors, these are
\begin{align}
    [\Phi^{\overline{ph}}_{(2)}]_{1234} &= F_{0,1256}\, [\chi_0^{0}]^{\overline{ph}}_{6587}\, F_{0,7834} \, , \\
    [\Phi^{pp}_{(2)}]_{1234} &= F_{0,1536}\, [\chi_0^{0}]^{pp}_{6857}\, F_{0,7284} \, , \\
    [\Phi^{ph}_{(2)}]_{1234} &= F_{0,5236}\, [\chi_0^{0}]^{ph}_{8567}\, F_{0,1874} \, ,
\end{align}
with summation over the repeated internal indices $5,6,7,8$ implied. Recall that the crossing factors are carried by the channel bubbles themselves, $[\chi_0^{0}]^{\overline{ph}}_{4321} = [\chi_0^{0}]_{4321}$, $[\chi_0^{0}]^{pp}_{4321} = \frac{1}{2}[\chi_0^{0}]_{4321}$ and $[\chi_0^{0}]^{ph}_{4321} = \zeta [\chi_0^{0}]_{2341}$, so that no further prefactors appear.

### Spin structure

Because the propagator is diagonal in spin, the spin sums of the channel contractions collapse to a double sum, and the spin structure of the bubble differs between the channels. For the $ph$ and the $pp$ channel these contractions are derived in the section on [spin parametrizations](spin_parametrizations.md); the $\overline{ph}$ channel follows in exactly the same way. Collecting all three,
\begin{align}
    [A \circ \chi_0^{\overline{ph}} \circ B]_{\sigma_1 \sigma_2 \sigma_3 \sigma_4} &= \sum_{\sigma_5, \sigma_6} A_{\sigma_1 \sigma_2 \sigma_5 \sigma_6} \bullet \chi_0^{\overline{ph}} \bullet B_{\sigma_6 \sigma_5 \sigma_3 \sigma_4} \, , \\
    [A \circ \chi_0^{pp} \circ B]_{\sigma_1 \sigma_2 \sigma_3 \sigma_4} &= \sum_{\sigma_5, \sigma_6} A_{\sigma_1 \sigma_5 \sigma_3 \sigma_6} \bullet \chi_0^{pp} \bullet B_{\sigma_6 \sigma_2 \sigma_5 \sigma_4} \, , \\
    [A \circ \chi_0^{ph} \circ B]_{\sigma_1 \sigma_2 \sigma_3 \sigma_4} &= \sum_{\sigma_5, \sigma_6} A_{\sigma_5 \sigma_2 \sigma_3 \sigma_6} \bullet \chi_0^{ph} \bullet B_{\sigma_1 \sigma_5 \sigma_6 \sigma_4} \, ,
\end{align}
where $\bullet$ denotes the contraction over all variables *except* the spin indices. Evaluating these on the three independent spin components gives the following table, valid for arbitrary four-point objects $A$ and $B$:

| channel | $\uparrow\uparrow$ | $\uparrow\downarrow$ | $\overline{\uparrow\downarrow}$ |
| --- | --- | --- | --- |
| $\overline{ph}$ | $A_{\uparrow\uparrow} B_{\uparrow\uparrow} + A_{\overline{\uparrow\downarrow}} B_{\overline{\uparrow\downarrow}}$ | $A_{\uparrow\downarrow} B_{\uparrow\downarrow}$ | $A_{\uparrow\uparrow} B_{\overline{\uparrow\downarrow}} + A_{\overline{\uparrow\downarrow}} B_{\uparrow\uparrow}$ |
| $pp$ | $A_{\uparrow\uparrow} B_{\uparrow\uparrow}$ | $A_{\uparrow\downarrow} B_{\uparrow\downarrow} + A_{\overline{\uparrow\downarrow}} B_{\overline{\uparrow\downarrow}}$ | $A_{\uparrow\downarrow} B_{\overline{\uparrow\downarrow}} + A_{\overline{\uparrow\downarrow}} B_{\uparrow\downarrow}$ |
| $ph$ | $A_{\uparrow\uparrow} B_{\uparrow\uparrow} + A_{\uparrow\downarrow} B_{\uparrow\downarrow}$ | $A_{\uparrow\downarrow} B_{\uparrow\uparrow} + A_{\uparrow\uparrow} B_{\uparrow\downarrow}$ | $A_{\overline{\uparrow\downarrow}} B_{\overline{\uparrow\downarrow}}$ |

Here and below the $\bullet \chi_0^r \bullet$ between the two factors is suppressed for readability.

:::{dropdown} Explicit calculation
The $\uparrow\uparrow$ and $\uparrow\downarrow$ entries of the $ph$ row and the whole $pp$ row are derived in the section on [spin parametrizations](spin_parametrizations.md). The remaining entries follow from the same two ingredients: spin conservation, $A_{\sigma_1\sigma_2\sigma_3\sigma_4} \sim \delta_{\sigma_1 + \sigma_3, \sigma_2 + \sigma_4}$, and the definitions $A_{\sigma\sigma\sigma\sigma} = A_{\uparrow\uparrow}$, $A_{\sigma\overline{\sigma}\overline{\sigma}\sigma} = A_{\uparrow\downarrow}$, $A_{\sigma\sigma\overline{\sigma}\overline{\sigma}} = A_{\overline{\uparrow\downarrow}}$.

**$ph$, $\overline{\uparrow\downarrow}$ component.** Setting $(\sigma_1 \sigma_2 \sigma_3 \sigma_4) = (\sigma \sigma \overline{\sigma} \overline{\sigma})$,
\begin{align}
    [A \circ \chi_0^{ph} \circ B]_{\overline{\uparrow\downarrow}} &= \sum_{\sigma_5, \sigma_6} A_{\sigma_5 \sigma \overline{\sigma} \sigma_6} \bullet \chi_0^{ph} \bullet B_{\sigma \sigma_5 \sigma_6 \overline{\sigma}} \, .
\end{align}
The first factor requires $\sigma_5 + \overline{\sigma} = \sigma + \sigma_6$, which of the four choices of $(\sigma_5, \sigma_6)$ only $(\sigma, \overline{\sigma})$ satisfies. Hence
\begin{align}
    [A \circ \chi_0^{ph} \circ B]_{\overline{\uparrow\downarrow}} &= A_{\sigma \sigma \overline{\sigma} \overline{\sigma}} \bullet \chi_0^{ph} \bullet B_{\sigma \sigma \overline{\sigma} \overline{\sigma}} = A_{\overline{\uparrow\downarrow}} \bullet \chi_0^{ph} \bullet B_{\overline{\uparrow\downarrow}} \, .
\end{align}

**$\overline{ph}$ channel.** Here $[\chi_0]^{\overline{ph}}_{\sigma_4 \sigma_3 \sigma_2 \sigma_1} \sim \delta_{\sigma_4,\sigma_1} \delta_{\sigma_2,\sigma_3}$, and with the connector $[A \circ B]^{\overline{ph}}_{1234} = A_{1256} B_{6534}$ the four internal spin sums reduce to the double sum quoted above. For the $\uparrow\uparrow$ component, $A_{\sigma \sigma \sigma_5 \sigma_6}$ requires $\sigma_5 = \sigma_6$, leaving $(\sigma,\sigma)$ and $(\overline{\sigma},\overline{\sigma})$,
\begin{align}
    [A \circ \chi_0^{\overline{ph}} \circ B]_{\uparrow\uparrow} &= A_{\sigma\sigma\sigma\sigma} \bullet \chi_0^{\overline{ph}} \bullet B_{\sigma\sigma\sigma\sigma} + A_{\sigma\sigma\overline{\sigma}\overline{\sigma}} \bullet \chi_0^{\overline{ph}} \bullet B_{\overline{\sigma}\overline{\sigma}\sigma\sigma} = A_{\uparrow\uparrow} B_{\uparrow\uparrow} + A_{\overline{\uparrow\downarrow}} B_{\overline{\uparrow\downarrow}} \, .
\end{align}
For the $\uparrow\downarrow$ component, $A_{\sigma \overline{\sigma} \sigma_5 \sigma_6}$ requires $\sigma + \sigma_5 = \overline{\sigma} + \sigma_6$, i.e. $(\sigma_5, \sigma_6) = (\overline{\sigma}, \sigma)$, and
\begin{align}
    [A \circ \chi_0^{\overline{ph}} \circ B]_{\uparrow\downarrow} &= A_{\sigma \overline{\sigma} \overline{\sigma} \sigma} \bullet \chi_0^{\overline{ph}} \bullet B_{\sigma \overline{\sigma} \overline{\sigma} \sigma} = A_{\uparrow\downarrow} B_{\uparrow\downarrow} \, .
\end{align}
For the $\overline{\uparrow\downarrow}$ component, $A_{\sigma \sigma \sigma_5 \sigma_6}$ again requires $\sigma_5 = \sigma_6$, and
\begin{align}
    [A \circ \chi_0^{\overline{ph}} \circ B]_{\overline{\uparrow\downarrow}} &= A_{\sigma\sigma\sigma\sigma} \bullet \chi_0^{\overline{ph}} \bullet B_{\sigma\sigma\overline{\sigma}\overline{\sigma}} + A_{\sigma\sigma\overline{\sigma}\overline{\sigma}} \bullet \chi_0^{\overline{ph}} \bullet B_{\overline{\sigma}\overline{\sigma}\overline{\sigma}\overline{\sigma}} = A_{\uparrow\uparrow} B_{\overline{\uparrow\downarrow}} + A_{\overline{\uparrow\downarrow}} B_{\uparrow\uparrow} \, .
\end{align}
Each row of the table satisfies the SU(2) identity $[\ldots]_{\uparrow\uparrow} = [\ldots]_{\uparrow\downarrow} + [\ldots]_{\overline{\uparrow\downarrow}}$, as it must, upon inserting $A_{\overline{\uparrow\downarrow}} = A_{\uparrow\uparrow} - A_{\uparrow\downarrow}$. $\checkmark$
:::

:::{note}
The $\overline{ph}$ and $ph$ rows are related by interchanging $\uparrow\downarrow \leftrightarrow \overline{\uparrow\downarrow}$ everywhere, which is the spin-space imprint of the crossing symmetry relating the two particle-hole channels (see the note on [$ph \leftrightarrow \overline{ph}$](two-particle-channels.md#note-on-possible-confusion-regarding-ph-leftrightarrow-overline-ph)). The $pp$ row is invariant under this interchange in the sense appropriate to a crossing-symmetric channel.
:::

Inserting $A = B = F_0$, and using $F_{0,\uparrow\uparrow} = 0$, the three channel contributions to the second-order vertex have the spin components

| channel | $\uparrow\uparrow$ | $\uparrow\downarrow$ | $\overline{\uparrow\downarrow}$ | $d$ | $m$ | $s$ | $t$ |
| --- | --- | --- | --- | --- | --- | --- | --- |
| $\overline{ph}$ | $U^2$ | $U^2$ | $0$ | $2U^2$ | $0$ | $U^2$ | $U^2$ |
| $pp$ | $0$ | $2U^2$ | $-2U^2$ | $2U^2$ | $-2U^2$ | $4U^2$ | $0$ |
| $ph$ | $U^2$ | $0$ | $U^2$ | $U^2$ | $U^2$ | $-U^2$ | $U^2$ |

in units of the corresponding $\bullet \chi_0^r \bullet$ contraction, i.e. the entry $X$ stands for $X \bullet [\chi_0^{0}]^r \bullet {} $ with the bare vertices stripped off. The $d/m$ and $s/t$ combinations follow from $X_{d/m} = X_{\uparrow\uparrow} \pm X_{\uparrow\downarrow}$ (upper sign for $d$), $X_s = X_{\uparrow\downarrow} - X_{\overline{\uparrow\downarrow}}$ and $X_t = X_{\uparrow\uparrow}$.

:::{note}
The $ph$ row has $\Phi^{ph}_{(2),d} = \Phi^{ph}_{(2),m} = U^2 \bullet [\chi_0^{0}]^{ph} \bullet {}$: at second order the density and magnetic channels coincide, because $F_{0,m} = -F_{0,d}$ and the two bare vertices enter quadratically. They part ways only at third order, as discussed in the section on the [$GW$ approximation](gw_approximation.md#polarization-and-screened-interaction-in-the-ph-channel). Likewise, $\Phi^{pp}_{(2),t} = 0$, since a local interaction does not act in the triplet particle-particle channel.
:::

### Frequency and momentum parametrization

In the channel-native [parametrizations](frequency_parametrizations.md), the bare bubbles read
\begin{align}
    [\chi_0^{0}]^{\overline{ph}}_{4321}(\nu, \omega) &= G_{0,41}(\nu)\, G_{0,23}(\nu + \omega) \, , \\
    [\chi_0^{0}]^{pp}_{4321}(\nu, \omega) &= \tfrac{1}{2}\, G_{0,41}(\nu)\, G_{0,23}(-\nu - \omega) \, , \\
    [\chi_0^{0}]^{ph}_{4321}(\nu, \omega) &= \zeta\, G_{0,21}(\nu)\, G_{0,43}(\nu + \omega) \, ,
\end{align}
and the channel contractions couple only the fermionic variables,
\begin{align}
    [A \circ \chi_0^{r} \circ B](\nu, \nu', \omega) &= \int_{\nu''} A(\nu, \nu'', \omega) \bullet \chi_0^{r}(\nu'', \omega) \bullet B(\nu'', \nu', \omega) \, .
\end{align}
Because the bare vertex of a local, instantaneous interaction is independent of frequency and momentum, it drops out of the loop, and every $\Phi^r_{(2)}$ depends on the transfer variables of its own channel only,
\begin{align}
    \Phi^r_{(2)}(\omega, \mathbf{q}) &= F_0 \bullet \left( \int_{\nu'', \mathbf{k}''} [\chi_0^{0}]^{r}(\nu'', \omega; \mathbf{k}'', \mathbf{q}) \right) \bullet F_0 \, .
\end{align}

:::{note}
This is the statement that at second order the vertex consists of three purely bosonic *$K_1$* objects, one per channel — the lowest tier of the asymptotic decomposition of the vertex. Each of them, however, is bosonic with respect to a *different* channel's transfer variable, so the three cannot be added without first transforming them into a common parametrization.
:::

### Result in the Keldysh formalism

For an instantaneous interaction the bare vertex takes the simple form derived in the section on the [Keldysh formalism](keldysh_formalism.md#four-point-vertex),
\begin{align}
    F_0^{k_1 k_2 k_3 k_4} &=
    \begin{cases}
        F_0 / 2 & \text{if } k_1 + k_2 + k_3 + k_4 \text{ odd} \\
        0 & \text{otherwise}\, ,
    \end{cases}
\end{align}
with $F_0$ the spin component under consideration, and the bubble inherits the Keldysh structure of the propagators, $\chi_0^{k_4 k_3 k_2 k_1} = G^{k_4 k_1} G^{k_2 k_3}$. Collecting everything, the three channel contributions to the second-order vertex are
\begin{align}
    [\chi_0^{0,\overline{ph}}]^{k_4 k_3 k_2 k_1}(\nu, \omega; \mathbf{k}, \mathbf{q}) &= G_0^{k_4 k_1}(\nu, \mathbf{k})\, G_0^{k_2 k_3}(\nu + \omega, \mathbf{k} + \mathbf{q}) \, , \\
    [\chi_0^{0,pp}]^{k_4 k_3 k_2 k_1}(\nu, \omega; \mathbf{k}, \mathbf{q}) &= \tfrac{1}{2}\, G_0^{k_4 k_1}(\nu, \mathbf{k})\, G_0^{k_2 k_3}(-\nu - \omega, -\mathbf{k} - \mathbf{q}) \, , \\
    [\chi_0^{0,ph}]^{k_4 k_3 k_2 k_1}(\nu, \omega; \mathbf{k}, \mathbf{q}) &= \zeta\, G_0^{k_2 k_1}(\nu, \mathbf{k})\, G_0^{k_4 k_3}(\nu + \omega, \mathbf{k} + \mathbf{q}) \, ,
\end{align}
and, with $\hat{\chi}^{r}(\omega, \mathbf{q}) \equiv \int_{\nu, \mathbf{k}} [\chi_0^{0,r}](\nu, \omega; \mathbf{k}, \mathbf{q})$ denoting the bubble integrated over its fermionic variables,
\begin{align}
    [\Phi^{\overline{ph}}_{(2)}]^{k_1 k_2 k_3 k_4}(\omega, \mathbf{q}) &= F_0^{k_1 k_2 k_5 k_6}\ \hat{\chi}^{\overline{ph},\, k_6 k_5 k_8 k_7}(\omega, \mathbf{q})\ F_0^{k_7 k_8 k_3 k_4} \, , \\
    [\Phi^{pp}_{(2)}]^{k_1 k_2 k_3 k_4}(\omega, \mathbf{q}) &= F_0^{k_1 k_5 k_3 k_6}\ \hat{\chi}^{pp,\, k_6 k_8 k_5 k_7}(\omega, \mathbf{q})\ F_0^{k_7 k_2 k_8 k_4} \, , \\
    [\Phi^{ph}_{(2)}]^{k_1 k_2 k_3 k_4}(\omega, \mathbf{q}) &= F_0^{k_5 k_2 k_3 k_6}\ \hat{\chi}^{ph,\, k_8 k_5 k_6 k_7}(\omega, \mathbf{q})\ F_0^{k_1 k_8 k_7 k_4} \, ,
\end{align}
with the loop measures
\begin{align}
    \int_\nu &= \zeta i \int \frac{d\nu}{2\pi} = \int \frac{d\nu}{2\pi i} \quad \text{(fermions, Keldysh)} \, , &
    \int_{\mathbf{k}} &= \int_{\mathrm{BZ}} \frac{d^d k}{(2\pi)^d} \, .
\end{align}

:::{note}
When Keldysh indices are displayed alongside the channel label we attach them to the bracket and abbreviate $[\chi_0^{0,r}]^{k_4 k_3 k_2 k_1} \equiv \big[[\chi_0^{0}]^{r}\big]^{k_4 k_3 k_2 k_1}$, and likewise for $\Phi^r_{(2)}$. The Matsubara expressions are obtained by dropping all Keldysh indices and replacing $\int_\nu \rightarrow \frac{1}{\beta}\sum_\nu$.
:::

## Second-order self-energy

The lowest nontrivial order of the [Schwinger-Dyson equation](parquet_theory.md#schwinger-dyson-equation) already yields the complete second-order self-energy. Starting from its third form and replacing the full vertex and the full propagators by their bare counterparts, $F \rightarrow F_0$ and $G \rightarrow G_0$, the dynamic term becomes
\begin{align}
    \Sigma^{(2)} &= \frac{1}{2}\, G_0 \cdot \Phi^{ph}_{(2)} \, ,
\end{align}
i.e. the self-energy closes exactly the $ph$ contribution to the second-order vertex derived above. Writing out the loop product,
\begin{align}
    \Sigma^{(2)}_{12} &= \frac{1}{2}\, [\Phi^{ph}_{(2)}]_{1 2 \tilde{1} \tilde{2}}\, G_{0,\tilde{2}\tilde{1}} \, .
\end{align}

:::{danger} To do
Add a diagrammatic representation of the second-order self-energy, obtained by inserting the second-order vertex diagrams into `diagrams/sde.png`.
:::

### Spin structure of the closing loop

As shown in the section on the [spin projection of the loop products](gw_approximation.md#spin-projection-of-the-loop-products), the loop product $[G \cdot X]$ projects the four-point object $X$ onto
\begin{align}
    [G \cdot X] \ \longrightarrow \ X_{\uparrow\uparrow} + X_{\overline{\uparrow\downarrow}} = \tfrac{1}{2}\left( X_d + 3 X_m \right) \, ,
\end{align}
which is a sum over the internal spin of the loop and hence contributes a factor $2$ relative to a single spin component. Combined with the $\frac{1}{2}$ of the SDE,
\begin{align}
    \Sigma^{(2)}_{\sigma\sigma} &= \frac{1}{2}\left( [\Phi^{ph}_{(2)}]_{\uparrow\uparrow} + [\Phi^{ph}_{(2)}]_{\overline{\uparrow\downarrow}} \right) \bullet G_0
    = \frac{1}{4}\left( [\Phi^{ph}_{(2)}]_{d} + 3\, [\Phi^{ph}_{(2)}]_{m} \right) \bullet G_0 \, ,
\end{align}
the familiar $\frac{1}{4}(d + 3m)$ weighting. Reading the $ph$ row of the table above, $[\Phi^{ph}_{(2)}]_{\uparrow\uparrow} = [\Phi^{ph}_{(2)}]_{\overline{\uparrow\downarrow}}$ and $[\Phi^{ph}_{(2)}]_{d} = [\Phi^{ph}_{(2)}]_{m}$, so the two terms are equal and
\begin{align}
    \boxed{\ \Sigma^{(2)}_{\sigma\sigma} = F_{0,\uparrow\downarrow} \bullet [\chi_0^{0}]^{ph} \bullet F_{0,\uparrow\downarrow} \bullet G_0 \ } \, .
\end{align}
The $\frac{1}{2}$ of the SDE has been used up by the spin sum: **the dynamic second-order self-energy carries net prefactor $1$, and it is obtained by inserting the single spin component $F_{0,\uparrow\downarrow} = -U$ at both ends of the bubble.**

:::{important}
This is the point at which a factor $2$ is easily lost. The two surviving spin components of $\Phi^{ph}_{(2)}$,
\begin{align}
    [\Phi^{ph}_{(2)}]_{\uparrow\uparrow} + [\Phi^{ph}_{(2)}]_{\overline{\uparrow\downarrow}}
    &= F_{0,\uparrow\downarrow} \bullet [\chi_0^{0}]^{ph} \bullet F_{0,\uparrow\downarrow}
     + F_{0,\overline{\uparrow\downarrow}} \bullet [\chi_0^{0}]^{ph} \bullet F_{0,\overline{\uparrow\downarrow}} \, ,
\end{align}
are *equal*, so contracting the single scalar $F_0 = F_{0,\uparrow\downarrow} = -U$ accounts for exactly one half of the spin sum. An implementation that carries no spin index and inserts the scalar $F_0 = -U$ must therefore use net prefactor $\frac{1}{2} \times 2 = 1$, not $\frac{1}{2}$.
:::

:::{dropdown} Consistency check with the $\overline{ph}$ form of the SDE
The first form of the SDE gives $\Sigma^{(2)} = \frac{1}{2} \zeta\, \Phi^{\overline{ph}}_{(2)} \cdot G_0$, where the loop product has the opposite orientation and hence projects onto the density component, $[X \cdot G] \rightarrow X_d$. Reading $\Phi^{\overline{ph}}_{(2),d} = 2U^2$ from the $\overline{ph}$ row of the table, i.e.
\begin{align}
    \Phi^{\overline{ph}}_{(2),d} &= F_{0,\overline{\uparrow\downarrow}} \bullet [\chi_0^{0}]^{\overline{ph}} \bullet F_{0,\overline{\uparrow\downarrow}} + F_{0,\uparrow\downarrow} \bullet [\chi_0^{0}]^{\overline{ph}} \bullet F_{0,\uparrow\downarrow} \, ,
\end{align}
again two equal terms, we obtain
\begin{align}
    \Sigma^{(2)}_{\sigma\sigma} &= \frac{1}{2}\, \zeta\, \Phi^{\overline{ph}}_{(2),d} \bullet G_0 = F_{0,\uparrow\downarrow} \bullet \zeta [\chi_0^{0}]^{\overline{ph}} \bullet F_{0,\uparrow\downarrow} \bullet G_0 \, ,
\end{align}
which agrees with the $ph$ result because $[\chi_0^{0}]^{ph}_{4321} = \zeta [\chi_0^{0}]_{2341} = \zeta [\chi_0^{0}]^{\overline{ph}}_{2341}$. $\checkmark$
:::

:::{dropdown} Consistency check with the $GW$ self-energy
The $GW$ self-energy derived in the section on the [$GW$ approximation](gw_approximation.md#the-gw-self-energy) reads
\begin{align}
    \Sigma(\nu) = U n + U^2 \int_{\nu'} G(\nu') \left[ \tfrac{1}{4} \chi_{d}(\nu - \nu') + \tfrac{3}{4} \chi_{m}(\nu - \nu') \right] \, .
\end{align}
To lowest order the RPA susceptibilities reduce to the bare polarization, $\chi_{d/m} \rightarrow P^{ph}$, and the weights add up to one, leaving
\begin{align}
    \Sigma^{(2)}(\nu) = U^2 \int_{\nu'} P^{ph}(\nu - \nu')\, G(\nu') \, , \qquad P^{ph}(\omega) = \zeta \int_\nu G(\nu) G(\nu+\omega) \, ,
\end{align}
which is exactly the boxed result above, since $F_{0,\uparrow\downarrow}^2 = U^2$ and $\int_\nu [\chi_0^{0}]^{ph} = P^{ph}$ for unit vertices. $\checkmark$
:::

### Frequency and momentum parametrization

It remains to parametrize the closing loop. As for the [Keldysh indices](keldysh_formalism.md#self-energy), it is the *second* index of $\Sigma$ that carries the arguments, opposite to $G_{21} = G(\nu_2)\delta(\nu_2 + \nu_1)$, i.e.
\begin{align}
    \Sigma_{12} &= \Sigma(\nu_2, \mathbf{k}_2)\, \delta(\nu_1 + \nu_2)\, \delta(\mathbf{k}_1 + \mathbf{k}_2) \, .
\end{align}
With this convention one finds for a general four-point object $A$ parametrized in the $ph$ channel
\begin{align}
    [G \cdot A](\nu, \mathbf{k}) &= \int_{\nu', \mathbf{k}'} A^{ph}(\nu', \nu', \nu - \nu'; \mathbf{k}', \mathbf{k}', \mathbf{k} - \mathbf{k}')\, G(\nu', \mathbf{k}') \, .
\end{align}
The vertex thus enters with *both* of its fermionic arguments set to the loop variables, and with transfer variables $\omega = \nu - \nu'$ and $\mathbf{q} = \mathbf{k} - \mathbf{k}'$. This is the same result as the frequency parametrization of the loop in the section on the [$GW$ approximation](gw_approximation.md#frequency-parametrization); we repeat the derivation here with the momenta reinstated and with the index convention for $\Sigma$ made explicit.

:::{dropdown} Explicit calculation
That the arguments of $\Sigma$ sit on its second index follows from the [Dyson equation](keldysh_formalism.md#dyson-equation), which in multi-index notation reads $G_{21} = G_{0,21} + G_{0,2\tilde{1}} \Sigma_{\tilde{1}\tilde{2}} G_{\tilde{2}1}$, matching the Keldysh chain $G_0^{k_2 k_{\tilde{1}}} \Sigma^{k_{\tilde{1}} k_{\tilde{2}}} G^{k_{\tilde{2}} k_1}$. The two propagators fix $\nu_{\tilde{1}} = -\nu_2$ and $\nu_{\tilde{2}} = -\nu_1 = \nu_2$, so that $G(\nu_2) = G_0(\nu_2) + G_0(\nu_2) \Sigma(\nu_2) G(\nu_2)$ requires $\Sigma_{\tilde{1}\tilde{2}} = \Sigma(\nu_{\tilde{2}}) \delta(\nu_{\tilde{1}} + \nu_{\tilde{2}})$.

Suppressing the momenta (they follow identically) and using $G_{\tilde{2}\tilde{1}} = G(\nu_{\tilde{2}}) \delta(\nu_{\tilde{2}} + \nu_{\tilde{1}})$ together with $A_{1 2 \tilde{1} \tilde{2}} = A^{ph}(-\nu_{\tilde{1}}, \nu_{\tilde{2}}, \nu_{\tilde{1}} + \nu_2)\, \delta(\nu_1 + \nu_2 + \nu_{\tilde{1}} + \nu_{\tilde{2}})$, we have
\begin{align}
    [G \cdot A]_{12} &= A_{1 2 \tilde{1} \tilde{2}}\, G_{\tilde{2}\tilde{1}} \\
    &= \int_{\nu_{\tilde{1}}, \nu_{\tilde{2}}} A^{ph}(-\nu_{\tilde{1}}, \nu_{\tilde{2}}, \nu_{\tilde{1}} + \nu_2)\, \delta(\nu_1 + \nu_2 + \nu_{\tilde{1}} + \nu_{\tilde{2}})\, G(\nu_{\tilde{2}})\, \delta(\nu_{\tilde{2}} + \nu_{\tilde{1}}) \\
    &= \int_{\nu_{\tilde{2}}} A^{ph}(\nu_{\tilde{2}}, \nu_{\tilde{2}}, \nu_2 - \nu_{\tilde{2}})\, G(\nu_{\tilde{2}})\, \delta(\nu_1 + \nu_2) \, ,
\end{align}
where the $\nu_{\tilde{1}}$ integration was performed with $\delta(\nu_{\tilde{2}} + \nu_{\tilde{1}})$, setting $\nu_{\tilde{1}} = -\nu_{\tilde{2}}$ and reducing the second delta function to $\delta(\nu_1 + \nu_2)$. Identifying $\nu = \nu_2$ and renaming $\nu_{\tilde{2}} \rightarrow \nu'$ gives the expression quoted above. $\checkmark$
:::

### Result in the Keldysh formalism

Collecting the spin result, the parametrization, and the Keldysh indices, the dynamic second-order self-energy of the Hubbard interaction is
\begin{align}
    [\chi_0^{0,ph}]^{k_4 k_3 k_2 k_1}(\nu, \omega; \mathbf{k}, \mathbf{q}) &= \zeta\, G_0^{k_2 k_1}(\nu, \mathbf{k})\, G_0^{k_4 k_3}(\nu + \omega, \mathbf{k} + \mathbf{q}) \, , \\
    [\Phi^{ph}_{(2)}]^{k_1 k_2 k_3 k_4}(\omega, \mathbf{q}) &= F_0^{k_5 k_2 k_3 k_6} \left( \int_{\nu'', \mathbf{k}''} [\chi_0^{0,ph}]^{k_8 k_5 k_6 k_7}(\nu'', \omega; \mathbf{k}'', \mathbf{q}) \right) F_0^{k_1 k_8 k_7 k_4} \, , \\
    \Sigma^{(2), k_1 k_2}(\nu, \mathbf{k}) &= \int_{\nu', \mathbf{k}'} [\Phi^{ph}_{(2)}]^{k_1 k_2 k_3 k_4}(\nu - \nu', \mathbf{k} - \mathbf{k}')\, G_0^{k_4 k_3}(\nu', \mathbf{k}') \, ,
\end{align}
with $F_0^{k_1 k_2 k_3 k_4} = -U/2$ for odd index sum and zero otherwise, and summation over repeated Keldysh indices implied. There are exactly two loops, and hence two factors of $\frac{1}{2\pi i}$ and two factors of $(2\pi)^{-d}$, and no further numerical prefactor.

:::{note}
Two practical simplifications follow from causality. Since $G^{11} = 0$, the bubble $[\chi_0^{0,ph}]^{k_4 k_3 k_2 k_1}$ vanishes whenever $k_1 = k_2 = 1$ or $k_3 = k_4 = 1$, which removes seven of its sixteen components. Since $F_0^{k_1 k_2 k_3 k_4}$ is nonzero only for an odd index sum, only eight of the sixteen vertex components contribute at each end. Finally, $\Sigma^{22} = 0$ identically.
:::

:::{note}
For a self-consistent evaluation of the SDE one replaces $G_0 \rightarrow G$ and one of the two bare vertices by the full vertex $F$. The density and magnetic channels are then no longer equal and the spin-resolved form
\begin{align}
    \Sigma^{k_1 k_2}(\nu, \mathbf{k}) &= \frac{1}{4} \int_{\nu', \mathbf{k}'} \left( [\Phi^{ph}_{d}]^{k_1 k_2 k_3 k_4} + 3\, [\Phi^{ph}_{m}]^{k_1 k_2 k_3 k_4} \right)\!(\nu - \nu', \mathbf{k} - \mathbf{k}')\, G^{k_4 k_3}(\nu', \mathbf{k}')
\end{align}
must be used, with $\Phi^{ph}_{m/d} = F_{m/d} \bullet \chi_0^{ph} \bullet F_{0,m/d}$ (the spin table above holds for $A \neq B$ as well). The vertex is then no longer independent of the fermionic variables, and both of its fermionic arguments are set to the loop variables $\nu'$ and $\mathbf{k}'$, as derived above.
:::
