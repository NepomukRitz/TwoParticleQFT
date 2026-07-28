# The $GW$ approximation

The $GW$ approximation is one of the oldest and most widely used approximations for the self-energy of an interacting many-body system. Its name refers to its defining structure: the self-energy is given by the product of a propagator $G$ and a *screened interaction* $W$. In the language of the [single boson exchange](single_boson_exchange.md) (SBE) decomposition, it arises very naturally as the approximation in which the Hedin vertices are replaced by their lowest-order contribution, $\gamma^r \simeq \mathbf{1}^r$ and $\overline{\gamma}^r \simeq \mathbf{1}^r$.

The purpose of this page is to spell out what this means concretely, in the conventions used throughout this documentation. This is worth doing carefully, because "$GW$" is used for a whole family of related but inequivalent approximations in the literature. Two choices in particular have to be made explicit, and neither of them is visible at second order in the bare interaction:

1. **Which two-particle channel** is resummed. The [Schwinger-Dyson equation](parquet_theory.md#schwinger-dyson-equation) (SDE) can be written in three equivalent ways, one per channel. These are equivalent only for the *exact* vertex $F$; once $F$ is truncated, they yield three genuinely different approximations.
2. **How the spin structure is handled.** For SU(2)-symmetric systems, the density and magnetic ladders in the $ph$ channel differ already at third order in $F_0$, and the self-energy picks them up with different weights.

We work in the Matsubara formalism throughout, and we specialize to a system with SU(2) spin symmetry and a *local and instantaneous* bare interaction, i.e. the Hubbard interaction of the [Hubbard model example](starting_point.md). This is the case in which the SBE machinery simplifies most drastically, and it is the case relevant for most applications.

:::{note}
Everything below is written for frequencies only. As explained in the section on [frequency parametrizations](frequency_parametrizations.md), all statements carry over verbatim to the momentum dependence by replacing $\nu, \nu', \omega \rightarrow \mathbf{k}, \mathbf{k}', \mathbf{q}$.
:::

## Spin structure of the bare interaction

We first record the spin components of the antisymmetrized bare vertex of the Hubbard model, which were derived in the section on the [starting point](starting_point.md#example-hubbard-model),
\begin{align}
    F_{0; \sigma_1\sigma_2\sigma_3\sigma_4} = -U \left(\delta_{\sigma_1, \sigma_4} \delta_{\sigma_3, \sigma_2} - \delta_{\sigma_1, \sigma_2}\delta_{\sigma_3, \sigma_4}\right) \delta_{\sigma_2, \overline{\sigma}_4} \, ,
\end{align}
where we suppressed the (trivial) frequency, momentum and time dependence. Reading off the three independent spin components defined in the section on [spin parametrizations](spin_parametrizations.md) gives

\begin{align}
    F_{0,\uparrow\downarrow} &= F_{0;\sigma\overline{\sigma}\overline{\sigma}\sigma} = -U \\
    F_{0,\overline{\uparrow\downarrow}} &= F_{0;\sigma\sigma\overline{\sigma}\overline{\sigma}} = +U \\
    F_{0,\uparrow\uparrow} &= F_{0;\sigma\sigma\sigma\sigma} = 0 \, ,
\end{align}
and hence, in the density/magnetic and singlet/triplet bases,
\begin{align}
    F_{0,d} &= F_{0,\uparrow\uparrow} + F_{0,\uparrow\downarrow} = -U  & F_{0,s} &= 2 F_{0,\uparrow\downarrow} - F_{0,\uparrow\uparrow} = -2U \\
    F_{0,m} &= F_{0,\uparrow\uparrow} - F_{0,\uparrow\downarrow} = +U  & F_{0,t} &= F_{0,\uparrow\uparrow} = 0 \, .
\end{align}

:::{dropdown} Explicit calculation
For $F_{0,\uparrow\downarrow}$ we set $(\sigma_1,\sigma_2,\sigma_3,\sigma_4) = (\sigma,\overline{\sigma},\overline{\sigma},\sigma)$. Then $\delta_{\sigma_1,\sigma_4} \delta_{\sigma_3,\sigma_2} = 1$, while $\delta_{\sigma_1,\sigma_2}\delta_{\sigma_3,\sigma_4} = 0$, and the overall constraint $\delta_{\sigma_2, \overline{\sigma}_4} = 1$ is satisfied. Hence $F_{0,\uparrow\downarrow} = -U$.

For $F_{0,\overline{\uparrow\downarrow}}$ we set $(\sigma_1,\sigma_2,\sigma_3,\sigma_4) = (\sigma,\sigma,\overline{\sigma},\overline{\sigma})$. Now $\delta_{\sigma_1,\sigma_4} \delta_{\sigma_3,\sigma_2} = 0$ while $\delta_{\sigma_1,\sigma_2}\delta_{\sigma_3,\sigma_4} = 1$, and again $\delta_{\sigma_2, \overline{\sigma}_4} = 1$. Hence $F_{0,\overline{\uparrow\downarrow}} = -U(0-1) = +U$.

For $F_{0,\uparrow\uparrow}$ all four spins are equal, so the constraint $\delta_{\sigma_2, \overline{\sigma}_4}$ vanishes identically and $F_{0,\uparrow\uparrow} = 0$. This is consistent with the SU(2) identity $F_{\uparrow\uparrow} = F_{\uparrow\downarrow} + F_{\overline{\uparrow\downarrow}}$, since $-U + U = 0$. $\checkmark$
:::

:::{note}
That $F_{0,t} = 0$ is the familiar statement that a purely local Hubbard interaction does not act in the triplet particle-particle channel, since two electrons of equal spin cannot occupy the same site.
:::

We will also need the spin components of the channel-specific [identity operators](two-particle-channels.md#connectors-and-identity-operators). For the $ph$ channel, $\mathbb{1}^{ph}_{1234} = \delta_{12}\delta_{34}$, whose spin part is $\delta_{\sigma_1\sigma_2}\delta_{\sigma_3\sigma_4}$, so that
\begin{align}
    \mathbb{1}_{\uparrow\uparrow} = 1\, , \qquad \mathbb{1}_{\uparrow\downarrow} = 0 \, , \qquad \mathbb{1}_{\overline{\uparrow\downarrow}} = 1 \qquad \Longrightarrow \qquad \mathbb{1}_{d} = \mathbb{1}_{m} = 1 \, .
\end{align}
The same holds for the non-frequency unit vertex $\mathbf{1}^{ph}$ introduced in the section on [SBE equations](single_boson_exchange.md#sbe-equations).

## Spin projection of the loop products

The self-energy is obtained from a four-point object by closing two of its legs with a propagator. As discussed in the section on the [Schwinger-Dyson equation](parquet_theory.md#schwinger-dyson-equation), there are two such *loop products*,
\begin{align}
    [X \cdot G]_{12} = X_{1 \tilde{2} \tilde{1} 2} G_{\tilde{2} \tilde{1}} \, , \qquad\qquad [G \cdot X]_{12} = X_{1 2 \tilde{1} \tilde{2}} G_{\tilde{2} \tilde{1}} \, .
\end{align}
Because the propagator is diagonal in spin, $G_{\tilde{2}\tilde{1}} \sim \delta_{\tilde{\sigma}_2 \tilde{\sigma}_1}$, and because the self-energy is diagonal in spin as well, each loop product projects the four-point object $X$ onto one specific spin combination. These two combinations are *different*:
\begin{align}
    [X \cdot G] &\ \longrightarrow \ X_{\uparrow\uparrow} + X_{\uparrow\downarrow} = X_d \\
    [G \cdot X] &\ \longrightarrow \ X_{\uparrow\uparrow} + X_{\overline{\uparrow\downarrow}} = \frac{1}{2}\left( X_d + 3 X_m \right) \, .
\end{align}

:::{dropdown} Explicit calculation
Write the external spins as $\sigma_1 = \sigma_2 = \sigma$ and denote the internal spin by $\tilde\sigma$. For the first loop product, the relevant spin pattern is $X_{\sigma \tilde\sigma \tilde\sigma \sigma}$, so that
\begin{align}
    \sum_{\tilde\sigma} X_{\sigma \tilde\sigma \tilde\sigma \sigma} = X_{\sigma\sigma\sigma\sigma} + X_{\sigma \overline\sigma \overline\sigma \sigma} = X_{\uparrow\uparrow} + X_{\uparrow\downarrow} = X_d \, .
\end{align}
For the second loop product, the pattern is $X_{\sigma \sigma \tilde\sigma \tilde\sigma}$, so that
\begin{align}
    \sum_{\tilde\sigma} X_{\sigma \sigma \tilde\sigma \tilde\sigma} = X_{\sigma\sigma\sigma\sigma} + X_{\sigma \sigma \overline\sigma \overline\sigma} = X_{\uparrow\uparrow} + X_{\overline{\uparrow\downarrow}} \, .
\end{align}
The SU(2) identity $X_{\uparrow\uparrow} = X_{\uparrow\downarrow} + X_{\overline{\uparrow\downarrow}}$ implies $X_{\overline{\uparrow\downarrow}} = X_{\uparrow\uparrow} - X_{\uparrow\downarrow} = X_m$, and with $X_{\uparrow\uparrow} = \tfrac{1}{2}(X_d + X_m)$ we obtain
\begin{align}
    X_{\uparrow\uparrow} + X_{\overline{\uparrow\downarrow}} = \tfrac{1}{2}(X_d + X_m) + X_m = \tfrac{1}{2}\left(X_d + 3 X_m\right) \, . \ \checkmark
\end{align}
:::

:::{important}
This is where the weights $\tfrac{1}{4}$ and $\tfrac{3}{4}$, familiar from the $GW$ literature for the Hubbard model, originate. They are a property of the *loop product*, not of the ladder resummation, and they follow directly from the SU(2) structure of a four-point vertex. No appeal to crossing symmetry is needed to obtain them.
:::

The two projections look inequivalent, but for a *crossing-symmetric* $X$ they are not: the identity $[X\cdot G] = \zeta [G \cdot X]$ quoted in the section on the [Schwinger-Dyson equation](parquet_theory.md#schwinger-dyson-equation) follows from $X_{1 \tilde{2} \tilde{1} 2} = \zeta X_{1 2 \tilde{1} \tilde{2}}$. For the bare vertex, which is crossing symmetric and frequency independent, we can check this on the spin components directly:
\begin{align}
    \zeta F_{0,d} = -(-U) = U = \tfrac{1}{2}\left(F_{0,d} + 3 F_{0,m}\right) = \tfrac{1}{2}\left(-U + 3U\right) \, . \ \checkmark
\end{align}

:::{warning}
The *individual two-particle channels are not crossing symmetric* (see the note in the section on [two-particle channels](two-particle-channels.md#second-order-perturbation-theory)). Consequently, as soon as $F$ is replaced by a single-channel resummation — which is exactly what $GW$ does — the two loop products are **no longer** related by a factor $\zeta$, and the three forms of the SDE cease to be equivalent. This is discussed in more detail [below](gw_approximation.md#which-form-of-the-schwinger-dyson-equation).
:::

## Polarization and screened interaction in the $ph$ channel

We now specialize to the $ph$ channel, which is the channel in which the density and magnetic fluctuations live, as is evident from its interpretation in terms of the density-density correlator discussed in the section on [two-particle channels](two-particle-channels.md#note-on-possible-confusion-regarding-ph-leftrightarrow-overline-ph).

The $GW$ approximation consists of replacing the Hedin vertices in the [SBE equations](single_boson_exchange.md#sbe-equations) by the unit vertex,
\begin{align}
    \boxed{\ \gamma^{ph} \simeq \mathbf{1}^{ph} \, , \qquad \overline{\gamma}^{ph} \simeq \mathbf{1}^{ph} \ } \, .
\end{align}
Everything else follows. The polarization then reduces to the bare bubble,
\begin{align}
    P^{ph} = \gamma^{ph} \circ \chi_0^{ph} \circ \mathbf{1}^{ph} \ \simeq \ \mathbb{1}^{ph} \circ \chi_0^{ph} \circ \mathbb{1}^{ph} \, .
\end{align}
Its spin structure is particularly simple: inserting the identity operators into the $ph$ contraction gives $P^{ph}_{1234} = \delta_{\sigma_1\sigma_2}\delta_{\sigma_3\sigma_4} P^{ph}$, i.e. the polarization is proportional to the $ph$ unit vertex in spin space, with the *spin-independent* scalar
\begin{align}
    P^{ph}(\omega) = \zeta \int_\nu G(\nu) G(\nu + \omega) \, , \qquad\qquad P^{ph}_d = P^{ph}_m = P^{ph} \, .
\end{align}

:::{dropdown} Explicit calculation
Using the spin structure of the $ph$ contraction derived in the section on [spin parametrizations](spin_parametrizations.md), $[A \circ \chi_0^{ph} \circ B]_{\sigma_1 \sigma_2 \sigma_3 \sigma_4} = \sum_{\sigma_5, \sigma_6} A_{\sigma_5 \sigma_2 \sigma_3 \sigma_6} \bullet \chi_0^{ph} \bullet B_{\sigma_1 \sigma_5 \sigma_6 \sigma_4}$, and inserting $A = B = \mathbb{1}^{ph}$ with spin part $\delta_{\sigma_1\sigma_2}\delta_{\sigma_3\sigma_4}$,
\begin{align}
    P^{ph}_{\sigma_1\sigma_2\sigma_3\sigma_4} &= \sum_{\sigma_5, \sigma_6} \delta_{\sigma_5 \sigma_2} \delta_{\sigma_3 \sigma_6} \ \chi_0^{ph} \ \delta_{\sigma_1 \sigma_5} \delta_{\sigma_6 \sigma_4} = \delta_{\sigma_1\sigma_2}\delta_{\sigma_3\sigma_4} \ \chi_0^{ph} \, ,
\end{align}
which has $P_{\uparrow\uparrow} = P^{ph}$, $P_{\uparrow\downarrow} = 0$, and therefore $P_d = P_m = P^{ph}$.

For the frequency dependence, we use the $ph$ bubble contraction from the section on [frequency parametrizations](frequency_parametrizations.md),
\begin{align}
[A \circ \chi_0^{ph} \circ B](\nu, \nu', \omega) &= \zeta \int_{\nu''} A(\nu, \nu'', \omega) G(\nu'') G(\nu'' + \omega) B(\nu'', \nu', \omega)\, ,
\end{align}
with the frequency-independent $A = B = \mathbb{1}^{ph}$, which leaves $P^{ph}(\omega) = \zeta \int_{\nu} G(\nu) G(\nu + \omega)$. It depends on the bosonic transfer frequency only. $\checkmark$
:::

:::{note}
The factor $\zeta$ is the familiar closed-fermion-loop sign. For fermions, $P^{ph}(\omega) = - \int_\nu G(\nu)G(\nu+\omega)$. Many references absorb this sign into the definition of the polarization; see the [comparison with the literature](gw_approximation.md#comparison-with-the-literature) below.
:::

With the polarization at hand, the screened interaction follows from the bosonic Dyson equation,
\begin{align}
    W^{ph} = F_0 + F_0 \bullet P^{ph} \bullet W^{ph} \, .
\end{align}
Since $P^{ph}$ is proportional to the $ph$ unit vertex in spin space, the $\bullet$ contraction carries the same spin algebra as the $\circ$ contraction, which decouples in the density/magnetic basis. The bosonic Dyson equation therefore reduces to two independent *scalar* equations,
\begin{align}
    W^{ph}_{d/m}(\omega) = F_{0,d/m} + F_{0,d/m} \, P^{ph}(\omega) \, W^{ph}_{d/m}(\omega) \, ,
\end{align}
with the closed-form solutions
\begin{align}
    \boxed{\ W^{ph}_{d}(\omega) = \frac{F_{0,d}}{1 - F_{0,d} P^{ph}(\omega)} = \frac{-U}{1 + U P^{ph}(\omega)} \, , \qquad W^{ph}_{m}(\omega) = \frac{F_{0,m}}{1 - F_{0,m} P^{ph}(\omega)} = \frac{+U}{1 - U P^{ph}(\omega)} \ } \, .
\end{align}

:::{important}
This is the point at which the density and magnetic channels part ways. Because $F_{0,m} = - F_{0,d}$ for a local Hubbard interaction, the two ladders are built from the *same* bubbles but with opposite sign of the rung. They therefore agree at second order in $U$ and differ from third order onwards. Any calculation that keeps only a single bubble — such as second-order perturbation theory — is blind to this distinction.
:::

It is often convenient to split off the bare interaction and work with the decaying part of the screened interaction,
\begin{align}
    \Delta W^{ph}_{d/m} \equiv W^{ph}_{d/m} - F_{0,d/m} = \frac{F_{0,d/m}^2 \, P^{ph}}{1 - F_{0,d/m} P^{ph}} = U^2 \chi_{d/m} \, ,
\end{align}
where we identified the RPA susceptibilities in the two channels,
\begin{align}
    \chi_{d}(\omega) = \frac{P^{ph}(\omega)}{1 + U P^{ph}(\omega)} \, , \qquad\qquad \chi_{m}(\omega) = \frac{P^{ph}(\omega)}{1 - U P^{ph}(\omega)} \, .
\end{align}

## The $GW$ self-energy

We start from the $ph$ form of the Schwinger-Dyson equation,
\begin{align}
    \Sigma = G \cdot F_0 + \frac{1}{2} G \cdot \left( F \circ \chi^{ph}_0 \circ F_0 \right) \, ,
\end{align}
and use the exact SBE identity $F \circ \chi_0^{r} \circ F_0 = \overline{\gamma}^{r} \bullet W^{r} - F_0$ derived in the section on the [SDE in SBE form](single_boson_exchange.md#schwinger-dyson-equation-in-sbe-form). Setting $\overline{\gamma}^{ph} \simeq \mathbf{1}^{ph}$ gives $F \circ \chi_0^{ph} \circ F_0 \simeq W^{ph} - F_0$, and therefore
\begin{align}
    \Sigma \simeq \frac{1}{2} G \cdot \left( F_0 + W^{ph} \right) \, ,
\end{align}
which is precisely the third line of the SBE form of the SDE with the Hedin vertex set to unity. Projecting onto spin components with $[G \cdot X] \rightarrow \tfrac{1}{2}(X_d + 3X_m)$, the factor $\tfrac{1}{2}$ combines with the $\tfrac{1}{2}$ of the SDE into the weights $\tfrac{1}{4}$ and $\tfrac{3}{4}$:
\begin{align}
    \boxed{\ \Sigma = \frac{1}{4}\left( F_{0,d} + W^{ph}_{d}\right) \cdot G \ + \ \frac{3}{4}\left( F_{0,m} + W^{ph}_{m}\right) \cdot G \ } \, ,
\end{align}
where the remaining $\cdot$ now denotes only the frequency, momentum and time contraction of the loop.

### Frequency parametrization

The loop closes the two legs of the screened interaction that carry the bosonic transfer frequency of the $ph$ channel. Writing out the frequency structure gives
\begin{align}
    \Sigma(\nu) = \int_{\nu'} G(\nu') \left[ \frac{1}{4}\left( F_{0,d} + W^{ph}_{d}(\nu - \nu')\right) + \frac{3}{4}\left( F_{0,m} + W^{ph}_{m}(\nu - \nu')\right) \right] \, .
\end{align}

:::{dropdown} Explicit calculation
Write the loop product with explicit frequency arguments. Using $G_{\tilde 2 \tilde 1}(\nu_{\tilde 2}, \nu_{\tilde 1}) = G(\nu_{\tilde 2})\delta(\nu_{\tilde 2} + \nu_{\tilde 1})$ and $\Sigma_{12}(\nu_1, \nu_2) = \Sigma(\nu_2) \delta(\nu_1 + \nu_2)$, we have for a general four-point object $X$
\begin{align}
    [G \cdot X](\nu_1, \nu_2) = \int_{\nu_3, \nu_4} X(\nu_1, \nu_2, \nu_3, \nu_4) \, G(\nu_4) \, \delta(\nu_3 + \nu_4) = \int_{\nu'} X(\nu_1, \nu_2, -\nu', \nu') \, G(\nu') \, ,
\end{align}
where we set $\nu_4 = \nu'$ and $\nu_3 = -\nu'$. Setting $\nu_1 = -\nu$ and $\nu_2 = \nu$ so that the external frequency of the self-energy is $\nu$, and translating to the $ph$-native parametrization of the section on [frequency parametrizations](frequency_parametrizations.md), $\nu_{ph} = -\nu_3$, $\nu'_{ph} = \nu_4$, $\omega_{ph} = \nu_3 + \nu_2$, we find
\begin{align}
    \nu_{ph} = \nu' \, , \qquad \nu'_{ph} = \nu' \, , \qquad \omega_{ph} = \nu - \nu' \, ,
\end{align}
and therefore
\begin{align}
    \Sigma(\nu) = \int_{\nu'} X^{ph}(\nu', \nu', \nu - \nu') \, G(\nu') \, .
\end{align}
Since the screened interaction depends on the bosonic frequency only, $X^{ph}(\nu',\nu',\omega) = W^{ph}(\omega)$ with $\omega = \nu - \nu'$. $\checkmark$
:::

:::{note}
The bosonic argument of the screened interaction is the *difference* $\nu - \nu'$ of the external and the loop frequency, for both spin channels alike. This is what makes the self-energy loop a convolution, and it is the structural reason why $GW$ can reuse the same numerical machinery as second-order perturbation theory.
:::

Finally, splitting off the static contribution and using $\Delta W_{d/m} = U^2 \chi_{d/m}$ yields the form in which the $GW$ self-energy is most easily recognized,
\begin{align}
    \Sigma(\nu) = U n + U^2 \int_{\nu'} G(\nu') \left[ \frac{1}{4} \chi_{d}(\nu - \nu') + \frac{3}{4} \chi_{m}(\nu - \nu') \right] \, ,
\end{align}
with the density per spin $n = \int_\nu G(\nu) e^{i\nu 0^+}$.

:::{dropdown} The static contribution
The static part collects the two bare-interaction terms plus the bare parts of the two screened interactions,
\begin{align}
    \frac{1}{4}\left(2 F_{0,d}\right) + \frac{3}{4}\left(2 F_{0,m}\right) = \frac{1}{2}\left( F_{0,d} + 3 F_{0,m}\right) = \frac{1}{2}\left(-U + 3U\right) = U \, ,
\end{align}
which, contracted with the loop $\int_{\nu'} G(\nu') e^{i\nu' 0^+} = n$, gives $\Sigma_\mathrm{H} = U n$. This is the correct Hartree term: it agrees with the direct evaluation of the first term of the SDE,
\begin{align}
    \Sigma_\mathrm{H} = \zeta F_0 \cdot G \ \rightarrow \ \zeta F_{0,d} \, n = (-1)(-U) n = U n \, ,
\end{align}
which is a nontrivial consistency check on the two spin projections. For the particle-hole symmetric case $n = 1/2$ and $\Sigma_\mathrm{H} = U/2$, as expected. $\checkmark$
:::

## Limits and checks

### Reduction to second-order perturbation theory

Expanding the screened interactions to leading order, $\Delta W_{d/m} = U^2 P^{ph} + \mathcal{O}(U^3)$, both spin channels contribute identically, and the weights add up to one. For the dynamic part of the self-energy we thus obtain
\begin{align}
    \Sigma^{(2)}(\nu) = \left(\frac{1}{4} + \frac{3}{4}\right) U^2 \int_{\nu'} G(\nu') P^{ph}(\nu-\nu') = U^2 \int_{\nu'} G(\nu') P^{ph}(\nu - \nu') \, .
\end{align}
Written out, and using $\zeta = -1$,
\begin{align}
    \Sigma^{(2)}(\nu) = - U^2 \int_{\nu'} \int_{\nu''} G(\nu') G(\nu'') G(\nu'' + \nu - \nu') \, ,
\end{align}
which is the familiar second-order (dynamic) self-energy of the Hubbard model, with the static Hartree term $Un$ accounted for separately.

:::{dropdown} Direct check from the Schwinger-Dyson equation
At second order, $F \rightarrow F_0$, so that $X = F_0 \circ \chi_0^{ph} \circ F_0$. Using the $ph$-channel decoupling $[A \circ \chi_0^{ph} \circ B]_{d/m} = A_{d/m} \bullet \chi_0^{ph} \bullet B_{d/m}$ from the section on [spin parametrizations](spin_parametrizations.md),
\begin{align}
    X_d = F_{0,d}^2 P^{ph} = U^2 P^{ph} \, , \qquad\qquad X_m = F_{0,m}^2 P^{ph} = U^2 P^{ph} \, ,
\end{align}
which are indeed equal, since only the *square* of the bare vertex enters. The spin projection of the loop product then gives $\tfrac{1}{2}(X_d + 3X_m) = 2 U^2 P^{ph}$, and the prefactor $\tfrac{1}{2}$ of the SDE leaves $\Sigma^{(2)} = U^2 P^{ph} \cdot G$. $\checkmark$
:::

:::{important}
This limit fixes only the *sum* of the two weights, $w_d + w_m = 1$. It cannot be used to validate the individual values $w_d = \tfrac{1}{4}$ and $w_m = \tfrac{3}{4}$. The first order at which the split becomes visible is $\mathcal{O}(U^3)$, where the density and magnetic ladders contribute with opposite signs:
\begin{align}
    \frac{1}{4}\Delta W_d + \frac{3}{4}\Delta W_m = U^2 P^{ph} + \frac{1}{2} U^3 \left(P^{ph}\right)^2 + \mathcal{O}(U^4) \, .
\end{align}
More generally, the term with $\ell$ bubbles carries the weight $\tfrac{3}{4} + \tfrac{1}{4}(-1)^{\ell+1}$, i.e. $1$ for odd $\ell$ and $\tfrac{1}{2}$ for even $\ell$.
:::

### Stoner criterion

The magnetic screened interaction $W_m = U / (1 - U P^{ph})$ diverges when $U P^{ph}(\omega) = 1$, while the density one, $W_d = -U/(1 + U P^{ph})$, stays finite for $P^{ph} > 0$. At $\omega = 0$ and for fermions,
\begin{align}
    P^{ph}(0) = - \int_\nu G(\nu)^2 \, ,
\end{align}
which, if evaluated with the bare propagator, equals $\partial n / \partial \mu$ and is positive. The divergence condition then becomes $U \, \partial n / \partial\mu = 1$, which is the Stoner criterion for a magnetic instability. That the instability appears in the magnetic and not in the density channel is a direct consequence of the relative sign $F_{0,m} = -F_{0,d}$, and is a useful sanity check on the signs above.

### Comparison with the literature

The result agrees with the $GW$ equations for the Hubbard atom given in Sec. 4.2 of [Kiese et al., SciPost Phys. Codebases 24 (2024)](https://doi.org/10.21468/SciPostPhysCodeb.24), who write
\begin{align}
    \Sigma(\nu) &\approx \frac{U n}{2} - \frac{1}{\beta} \sum_{\nu'} G(\nu') \left[ \frac{1}{4}\eta^{D}(\nu - \nu') + \frac{3}{4}\eta^{M}(\nu-\nu')\right] \, , \\
    \eta^{D/M}(\omega) &= \frac{\pm U}{1 \mp U P(\omega)} \, , \qquad P(\omega) = \frac{1}{\beta}\sum_\nu G(\omega + \nu) G(\nu) \, .
\end{align}
Their polarization does not carry the closed-loop sign, so $P = -P^{ph}$, and consequently their screened interactions are related to ours by an overall sign,
\begin{align}
    W^{ph}_{d} = - \eta^{D} \, , \qquad\qquad W^{ph}_{m} = - \eta^{M} \, .
\end{align}
With $\tfrac{1}{4}F_{0,d} + \tfrac{3}{4}F_{0,m} = U/2$ accounting for their explicit $Un/2$, the two expressions are identical term by term.

:::{note}
The relative sign between $W$ and $\eta$ is not a discrepancy, but reflects the different sign convention for the bare interaction: in our antisymmetrized Hugenholtz convention $F_{0,d} = -U$, whereas the density component of the bare interaction is defined as $+U$ there.
:::

## Which form of the Schwinger-Dyson equation?

The [SDE](parquet_theory.md#schwinger-dyson-equation) can be written in three equivalent ways, and the SBE identities turn each of them into a $GW$-like expression once the Hedin vertices are set to unity,
\begin{align}
    \Sigma &\simeq \frac{1}{2}\zeta \left(F_0 + W^{\overline{ph}}\right) \cdot G  \\
    \Sigma &\simeq \zeta \, W^{pp} \cdot G  \\
    \Sigma &\simeq \frac{1}{2} G \cdot \left(F_0 + W^{ph}\right) \, .
\end{align}
For the *exact* vertex these three are identical. For the truncated vertex they are not, because a single-channel resummation is not crossing symmetric. They correspond to three physically distinct approximations, which resum three different classes of fluctuations:

- the **$ph$ form** resums density and magnetic fluctuations, and is the one derived above;
- the **$\overline{ph}$ form** resums the crossed particle-hole ladder. It does not decouple in the density/magnetic basis, but in the combinations $X_{\uparrow\uparrow} \pm X_{\overline{\uparrow\downarrow}}$, for which the bare interaction takes the values $F_{0,+} = +U$ and $F_{0,-} = -U$;
- the **$pp$ form** resums the particle-particle ladder, i.e. it is a $T$-matrix approximation. In the singlet/triplet basis the bare interaction is $F_{0,s} = -2U$ and $F_{0,t}=0$, so only the singlet channel is screened.

:::{dropdown} Spin decoupling in the $\overline{ph}$ channel
The spin structure of the $\overline{ph}$ contraction is
$[A \circ \chi_0^{\overline{ph}} \circ B]_{\sigma_1\sigma_2\sigma_3\sigma_4} = \sum_{\sigma_5,\sigma_6} A_{\sigma_1 \sigma_2 \sigma_5 \sigma_6} \bullet \chi_0^{\overline{ph}} \bullet B_{\sigma_6 \sigma_5 \sigma_3 \sigma_4}$.
Spin conservation forces $\sigma_5 = \sigma_6$, so that
\begin{align}
    [A \circ \chi_0^{\overline{ph}} \circ B]_{\uparrow\uparrow} &= A_{\uparrow\uparrow} \bullet \chi_0^{\overline{ph}} \bullet B_{\uparrow\uparrow} + A_{\overline{\uparrow\downarrow}} \bullet \chi_0^{\overline{ph}} \bullet B_{\overline{\uparrow\downarrow}} \\
    [A \circ \chi_0^{\overline{ph}} \circ B]_{\overline{\uparrow\downarrow}} &= A_{\uparrow\uparrow} \bullet \chi_0^{\overline{ph}} \bullet B_{\overline{\uparrow\downarrow}} + A_{\overline{\uparrow\downarrow}} \bullet \chi_0^{\overline{ph}} \bullet B_{\uparrow\uparrow} \, ,
\end{align}
and hence the combinations $X_\pm = X_{\uparrow\uparrow} \pm X_{\overline{\uparrow\downarrow}}$ decouple, in complete analogy with the density/magnetic basis of the $ph$ channel. In terms of the density/magnetic components, $X_+ = \tfrac{1}{2}(X_d + 3X_m)$ and $X_- = X_{\uparrow\downarrow} = \tfrac{1}{2}(X_d - X_m)$. For the bare vertex, $F_{0,+} = 0 + U = U$ and $F_{0,-} = 0 - U = -U$.
:::

:::{warning}
The remark at the end of the section on the [SBE approximation](single_boson_exchange.md#sbe-approximation), that setting $\gamma^r \simeq \mathbf{1}^r$ in the $pp$ form gives "precisely the $GW$ expression", should be read as a statement about the *structural form* $\Sigma \simeq \zeta W \cdot G$ rather than about its diagrammatic content. For a local Hubbard interaction, the $pp$ form resums particle-particle ladders and therefore describes pairing rather than charge and spin fluctuations. Which of the three forms deserves the name "$GW$" is ultimately a matter of convention, but for the Hubbard model the $ph$ form is the one that reproduces the standard charge-plus-spin-fluctuation $GW$ self-energy.
:::

:::{danger} To do
Work out explicitly how much the three $GW$ variants differ at $\mathcal{O}(U^3)$, and whether any statement can be made about which one is closest to the exact result. Relatedly, one could construct a crossing-symmetrized $GW$ variant by averaging the three forms.
:::

## Variants: $G_0 W_0$ and self-consistent $GW$

The equations above do not yet specify which propagator enters the bubble $\chi_0^{ph}$ and the self-energy loop. Two common choices are:

- **$G_0 W_0$** (one-shot): the bare propagator $G_0$ is used everywhere, so $\chi_0^{ph}$ is built from $[\chi_0^0]^{ph}$ and the self-energy is evaluated once. The result is not a conserving approximation, but it is cheap and avoids the self-consistency loop.
- **self-consistent $GW$**: the full propagator $G$, obtained from the Dyson equation with the current self-energy, is used in both the bubble and the loop, and the equations are iterated to convergence. This is a $\Phi$-derivable, conserving approximation in the sense of Baym and Kadanoff.

Intermediate variants (self-consistency in the self-energy loop but not in the polarization, or vice versa) exist as well and are sometimes labelled $GW_0$ or $G_0W$.

:::{note}
Independently of the choice above, both the density and the magnetic ladder are geometric series in $U P^{ph}$. They converge only for $|U P^{ph}| < 1$. The closed-form expressions for $W_{d/m}$ given above remain well defined beyond that point (except exactly at the pole), but the physical content of the approximation should be treated with care once the magnetic channel approaches its instability, since $GW$ neglects precisely the vertex corrections that regulate it.
:::

:::{danger} To do
- Add diagrammatic representations for the polarization, the screened interaction and the $GW$ self-energy.
- Discuss what changes for a non-local or retarded bare interaction, where $W^r$ acquires a momentum or frequency dependence beyond the bosonic transfer variable, and where $F_{0,m} = -F_{0,d}$ no longer holds.
- Relate the expression derived here to the FLEX approximation, which additionally includes the particle-particle ladder and subtracts the double-counted second-order term.
- Add references to the original $GW$ literature (Hedin) and to its applications to the Hubbard model.
:::
