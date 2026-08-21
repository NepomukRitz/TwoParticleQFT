# The $GW$ approximation

The $GW$ approximation is one of the oldest and most widely used approximations for the self-energy of an interacting many-body system. Its name refers to its defining structure: the self-energy is given by the product of a propagator $G$ and a *screened interaction* $W$. In the language of the [single boson exchange](single_boson_exchange.md) (SBE) decomposition, it arises very naturally as the approximation in which the Hedin vertices are replaced by their lowest-order contribution, $\gamma^r \simeq \mathbf{1}^r$ and $\overline{\gamma}^r \simeq \mathbf{1}^r$.

The purpose of this page is to spell out what this means concretely, in the conventions used throughout this documentation. This is worth doing carefully, because "$GW$" is used for a whole family of related but inequivalent approximations in the literature. Two choices in particular have to be made explicit, and neither of them is visible at second order in the bare interaction:

1. **Which two-particle channel** is resummed. The [Schwinger-Dyson equation](parquet_theory.md#schwinger-dyson-equation) (SDE) can be written in three ways, one per channel, which are equivalent for the *exact* vertex $F$ but not for a truncated one. As shown [below](#which-form-of-the-schwinger-dyson-equation), the two particle-hole forms turn out to yield the *same* $GW$ self-energy, whereas the particle-particle form yields a genuinely different approximation.
2. **How the spin structure is handled.** For SU(2)-symmetric systems, the density and magnetic ladders in the $ph$ channel differ already at third order in $F_0$, and the self-energy picks them up with different weights.

We work in the Matsubara formalism throughout, and we specialize to a system with SU(2) spin symmetry and a *local and instantaneous* bare interaction, i.e. the Hubbard interaction of the [Hubbard model example](starting_point.md#example-hubbard-model). This is the case in which the SBE machinery simplifies most drastically, and it is the case relevant for most applications.

(gw-scope)=
:::{important} Scope of the simplifications below
Several steps on this page rely on the objects involved being *scalars* in every degree of freedom other than spin and the bosonic transfer variable. Concretely, we assume a single band with no orbital index, and we work in the Matsubara formalism, so that there are no Keldysh indices either. Under these assumptions the bosonic Dyson equation for the screened interaction decouples into two *scalar* equations that can be solved by ordinary division, and the density and magnetic ladders reduce to geometric series in a single scalar.

None of the structural results change in the presence of orbital or Keldysh indices (the SBE equations, the spin projections of the loop products and the $\tfrac{1}{4}/\tfrac{3}{4}$ weights all carry over unchanged), but the closed-form expressions do not. With additional indices the bosonic Dyson equation becomes a genuine matrix equation in those indices at every $(\omega, \mathbf{q})$, and the "division" below has to be replaced by a matrix inversion. The same caveat applies to the RPA susceptibilities and to the Stoner criterion, which then involves the leading eigenvalue of a matrix rather than a scalar. That generalization is carried out in the section on [closed-form ladder resummation with additional indices](#closed-form-ladder-resummation-with-additional-indices), which replaces the division by a pointwise matrix inversion, states the Stoner criterion as a condition on the leading eigenvalue, and shows that the susceptibilities then require amputating the outer bare vertices rather than dividing by $U^2$.
:::

:::{note}
Everything below is written for frequencies only. As explained in the section on [frequency parametrizations](frequency_parametrizations.md), all statements carry over verbatim to the momentum dependence by replacing $\nu, \nu', \omega \rightarrow \mathbf{k}, \mathbf{k}', \mathbf{q}$.
:::

## Spin structure of the bare interaction

We first record the spin components of the antisymmetrized bare vertex of the Hubbard model, which were derived in the [Hubbard model example](starting_point.md#example-hubbard-model) of the section on the starting point,
\begin{align}
    F_{0; \sigma_1\sigma_2\sigma_3\sigma_4} = -U \left(\delta_{\sigma_1, \sigma_4} \delta_{\sigma_3, \sigma_2} - \delta_{\sigma_1, \sigma_2}\delta_{\sigma_3, \sigma_4}\right) \delta_{\sigma_2, \overline{\sigma}_4} \, ,
\end{align}
where we suppressed the (trivial) frequency and momentum dependence. Reading off the three independent spin components defined in the section on [spin parametrizations](spin_parametrizations.md) gives

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

We will also need the spin components of the $ph$ channel unit. Two related objects appear in what follows: the [channel identity operator](two-particle-channels.md#connectors-and-identity-operators) $\mathbb{1}^{ph}_{1234} = \delta_{1,2}\delta_{3,4}$, which is the unit with respect to the full connector $\circ$, and the [unit vertex](single_boson_exchange.md#sbe-equations) $\mathbf{1}^{ph}$, which is the unit with respect to $\bullet$, i.e. with respect to all degrees of freedom *except* frequency and momentum. Both carry the same spin part, $\delta_{\sigma_1, \sigma_2}\delta_{\sigma_3, \sigma_4}$, so that
\begin{align}
    \mathbf{1}^{ph}_{\uparrow\uparrow} = 1\, , \qquad \mathbf{1}^{ph}_{\uparrow\downarrow} = 0 \, , \qquad \mathbf{1}^{ph}_{\overline{\uparrow\downarrow}} = 1 \qquad \Longrightarrow \qquad \mathbf{1}^{ph}_{d} = \mathbf{1}^{ph}_{m} = 1 \, .
\end{align}
From here on we consistently use $\mathbf{1}^{ph}$, since that is the object appearing in the SBE equations.

## Spin projection of the loop products

The self-energy is obtained from a four-point object by closing two of its legs with a propagator. As discussed in the section on the [Schwinger-Dyson equation](parquet_theory.md#schwinger-dyson-equation), there are two such *loop products*,
\begin{align}
    [X \cdot G]_{12} = X_{1 \tilde{2} \tilde{1} 2} G_{\tilde{2} \tilde{1}} \, , \qquad\qquad [G \cdot X]_{12} = X_{1 2 \tilde{1} \tilde{2}} G_{\tilde{2} \tilde{1}} \, .
\end{align}
Because the propagator is diagonal in spin, $G_{\tilde{2}\tilde{1}} \sim \delta_{\tilde{\sigma}_2, \tilde{\sigma}_1}$, and because the self-energy is diagonal in spin as well, each loop product projects the four-point object $X$ onto one specific spin combination. These two combinations are *different*:
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
The *individual two-particle channels are not crossing symmetric* (see the note in the section on [two-particle channels](two-particle-channels.md#second-order-perturbation-theory)). Consequently, as soon as $X$ is a single-channel resummation — which is exactly what enters $GW$ — the two loop products are **no longer** related by a factor $\zeta$, and it matters which of them one uses. Which form of the SDE to start from therefore requires care; this is taken up [below](#which-form-of-the-schwinger-dyson-equation).
:::

(polarization-and-screened-interaction-in-the-ph-channel)=
## Polarization and screened interaction in the $ph$ channel

We now specialize to the $ph$ channel, which is the channel in which the density and magnetic fluctuations live, as is evident from its interpretation in terms of the density-density correlator discussed in the section on [two-particle channels](two-particle-channels.md#note-on-possible-confusion-regarding-ph-leftrightarrow-overline-ph).

The $GW$ approximation consists of replacing the Hedin vertices in the [SBE equations](single_boson_exchange.md#sbe-equations) by the unit vertex,
\begin{align}
    \boxed{\ \gamma^{ph} \simeq \mathbf{1}^{ph} \, , \qquad \overline{\gamma}^{ph} \simeq \mathbf{1}^{ph} \ } \, .
\end{align}
Everything else follows. The polarization then reduces to the bare bubble,
\begin{align}
    P^{ph} = \gamma^{ph} \circ \chi_0^{ph} \circ \mathbf{1}^{ph} \ \simeq \ \mathbf{1}^{ph} \circ \chi_0^{ph} \circ \mathbf{1}^{ph} \, .
\end{align}
Its spin structure is particularly simple: inserting the unit vertices into the $ph$ contraction gives $P^{ph}_{1234} = \delta_{\sigma_1, \sigma_2}\delta_{\sigma_3, \sigma_4} P^{ph}$, i.e. the polarization is proportional to the $ph$ unit vertex in spin space, with the *spin-independent* scalar
\begin{align}
    P^{ph}(\omega) = \zeta \int_\nu G(\nu) G(\nu + \omega) \, , \qquad\qquad P^{ph}_d = P^{ph}_m = P^{ph} \, .
\end{align}

:::{dropdown} Explicit calculation
Using the spin structure of the $ph$ contraction derived in the section on [spin parametrizations](spin_parametrizations.md), $[A \circ \chi_0^{ph} \circ B]_{\sigma_1 \sigma_2 \sigma_3 \sigma_4} = \sum_{\sigma_5, \sigma_6} A_{\sigma_5 \sigma_2 \sigma_3 \sigma_6} \bullet \chi_0^{ph} \bullet B_{\sigma_1 \sigma_5 \sigma_6 \sigma_4}$, and inserting $A = B = \mathbf{1}^{ph}$ with spin part $\delta_{\sigma_1, \sigma_2}\delta_{\sigma_3, \sigma_4}$,
\begin{align}
    P^{ph}_{\sigma_1\sigma_2\sigma_3\sigma_4} &= \sum_{\sigma_5, \sigma_6} \delta_{\sigma_5, \sigma_2} \delta_{\sigma_3, \sigma_6} \ \chi_0^{ph} \ \delta_{\sigma_1, \sigma_5} \delta_{\sigma_6, \sigma_4} = \delta_{\sigma_1, \sigma_2}\delta_{\sigma_3, \sigma_4} \ \chi_0^{ph} \, ,
\end{align}
which has $P_{\uparrow\uparrow} = P^{ph}$, $P_{\uparrow\downarrow} = 0$, and therefore $P_d = P_m = P^{ph}$.

For the frequency dependence, we use the $ph$ bubble contraction from the section on [frequency parametrizations](frequency_parametrizations.md),
\begin{align}
[A \circ \chi_0^{ph} \circ B](\nu, \nu', \omega) &= \zeta \int_{\nu''} A(\nu, \nu'', \omega) G(\nu'') G(\nu'' + \omega) B(\nu'', \nu', \omega)\, ,
\end{align}
with the frequency-independent $A = B = \mathbf{1}^{ph}$, which leaves $P^{ph}(\omega) = \zeta \int_{\nu} G(\nu) G(\nu + \omega)$. It depends on the bosonic transfer frequency only. $\checkmark$
:::

:::{note}
The factor $\zeta$ is the familiar closed-fermion-loop sign. For fermions, $P^{ph}(\omega) = - \int_\nu G(\nu)G(\nu+\omega)$. Many references absorb this sign into the definition of the polarization; see the [comparison with the literature](#comparison-with-the-literature) below.
:::

With the polarization at hand, the screened interaction follows from the bosonic Dyson equation,
\begin{align}
    W^{ph} = F_0 + F_0 \bullet P^{ph} \bullet W^{ph} \, .
\end{align}
Since $P^{ph}$ is proportional to the $ph$ unit vertex in spin space, the $\bullet$ contraction carries the same spin algebra as the $\circ$ contraction. That algebra is worked out explicitly in the section on [spin parametrizations](spin_parametrizations.md) — the spin sums there never touch the frequency arguments, which is precisely why the result is already stated with $\bullet$ between the two factors — and it decouples in the density/magnetic basis. The corresponding spin table for all three channels is collected in the section on [second-order perturbation theory](second_order_perturbation_theory.md#spin-structure). The bosonic Dyson equation therefore reduces to two independent *scalar* equations,
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

It is often convenient to split off the bare interaction and work with the decaying part of the screened interaction, which we denote by a tilde,
\begin{align}
    \widetilde{W}^{ph}_{d/m} \equiv W^{ph}_{d/m} - F_{0,d/m} = \frac{F_{0,d/m}^2 \, P^{ph}}{1 - F_{0,d/m} P^{ph}} = U^2 \chi_{d/m} \, ,
\end{align}
where we identified the susceptibilities in the two channels,
\begin{align}
    \chi_{d}(\omega) = \frac{P^{ph}(\omega)}{1 + U P^{ph}(\omega)} \, , \qquad\qquad \chi_{m}(\omega) = \frac{P^{ph}(\omega)}{1 - U P^{ph}(\omega)} \, .
\end{align}

:::{note}
These are the *RPA* susceptibilities in the strict sense only if the polarization is built from bare propagators, i.e. if $\chi_0^{ph}$ is replaced by the bare bubble $[\chi_0^{0}]^{ph}$. If the full propagator is used instead, as in the self-consistent variants discussed at the end of this page, the same expressions define ladder susceptibilities with dressed propagators. In neither case are they the exact physical susceptibilities, since the $GW$ approximation discards the vertex corrections contained in the Hedin vertices.
:::

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
    \boxed{\ \Sigma = \frac{1}{4}\, G \cdot \left( F_{0,d} + W^{ph}_{d}\right) \ + \ \frac{3}{4}\, G \cdot \left( F_{0,m} + W^{ph}_{m}\right) \ } \, ,
\end{align}
where the spin sum has been carried out, so that the remaining $\cdot$ denotes only the frequency and momentum contraction of the loop.

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
where we set $\nu_4 = \nu'$ and $\nu_3 = -\nu'$. Setting $\nu_1 = -\nu$ and $\nu_2 = \nu$ so that the external frequency of the self-energy is $\nu$, we translate to the $ph$-native parametrization of the section on [frequency parametrizations](frequency_parametrizations.md), $\nu_{ph} = -\nu_3$, $\nu'_{ph} = \nu_4$ and
\begin{align}
    \omega_{ph} = \nu_2 + \nu_3 = -\nu_1 - \nu_4 \, ,
\end{align}
where the second form follows from energy conservation $\nu_1 + \nu_2 + \nu_3 + \nu_4 = 0$ and involves only the two arguments that are *not* integrated over. With $\nu_1 = -\nu$ and $\nu_4 = \nu'$ this gives immediately
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
The bosonic argument of the screened interaction is the *difference* $\nu - \nu'$ of the external and the loop frequency, for both spin channels alike. This is what makes the self-energy loop a convolution, and it is the structural reason why $GW$ can reuse the same numerical machinery as second-order perturbation theory. Explicitly, the loop turns into a pointwise product after transforming to time and space, as worked out in the section on [Fourier convolution](second_order_perturbation_theory.md#fourier-convolution); the manipulation there applies verbatim with $\Phi^{ph}_{(2)}$ replaced by the weighted combination of screened interactions derived here.
:::

Finally, splitting off the static contribution and using $\widetilde{W}_{d/m} = U^2 \chi_{d/m}$ yields the form in which the $GW$ self-energy is most easily recognized,
\begin{align}
    \Sigma(\nu) = U n + U^2 \int_{\nu'} G(\nu') \left[ \frac{1}{4} \chi_{d}(\nu - \nu') + \frac{3}{4} \chi_{m}(\nu - \nu') \right] \, ,
\end{align}
with the density per spin $n = \int_\nu G(\nu) e^{i\nu 0^+}$.

:::{dropdown} The static contribution
Each spin channel contributes its bare interaction *twice*: once from the explicit $F_0$ in $\Sigma \simeq \tfrac{1}{2} G \cdot (F_0 + W^{ph})$, and once from the bare part of the screened interaction itself, since $W^{ph}_{d/m} = F_{0,d/m} + \widetilde{W}^{ph}_{d/m}$. This is the origin of the factors of two in
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

Expanding the screened interactions to leading order, $\widetilde{W}_{d/m} = U^2 P^{ph} + \mathcal{O}(U^3)$, both spin channels contribute identically, and the weights add up to one. For the dynamic part of the self-energy we thus obtain
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
which are indeed equal, since only the *square* of the bare vertex enters. The spin projection of the loop product then gives $\tfrac{1}{2}(X_d + 3X_m) = 2 U^2 P^{ph}$, and the prefactor $\tfrac{1}{2}$ of the SDE leaves $\Sigma^{(2)} = G \cdot \left( U^2 P^{ph} \right)$. $\checkmark$
:::

:::{important}
This limit fixes only the *sum* of the two channel weights, $\tfrac{1}{4} + \tfrac{3}{4} = 1$; it says nothing about the individual values. The first order at which the split becomes visible is $\mathcal{O}(U^3)$, where the density and magnetic ladders contribute with opposite signs:
\begin{align}
    \frac{1}{4}\widetilde{W}_d + \frac{3}{4}\widetilde{W}_m = U^2 P^{ph} + \frac{1}{2} U^3 \left(P^{ph}\right)^2 + \mathcal{O}(U^4) \, .
\end{align}
More generally, the term with $\ell$ bubbles carries the weight $\tfrac{3}{4} + \tfrac{1}{4}(-1)^{\ell+1}$, i.e. $1$ for odd $\ell$ and $\tfrac{1}{2}$ for even $\ell$.
:::

(stoner-criterion)=
### Stoner criterion

The magnetic screened interaction $W_m = U / (1 - U P^{ph})$ diverges when $U P^{ph}(\omega) = 1$, while the density one, $W_d = -U/(1 + U P^{ph})$, stays finite for $P^{ph} > 0$. At $\omega = 0$ and for fermions,
\begin{align}
    P^{ph}(0) = - \int_\nu G(\nu)^2 \, ,
\end{align}
which, if evaluated with the bare propagator, equals $\partial n / \partial \mu$ and is positive. The divergence condition then becomes $U \, \partial n / \partial\mu = 1$, which is the Stoner criterion for a magnetic instability. That the instability appears in the magnetic and not in the density channel is a direct consequence of the relative sign $F_{0,m} = -F_{0,d}$, and is a useful sanity check on the signs above.

(comparison-with-the-literature)=
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

(closed-form-ladder-resummation-with-additional-indices)=
## Closed-form ladder resummation with additional indices

Everything above was derived for objects that are *scalars* in every degree of freedom other than spin and the bosonic transfer variable, as announced in the [scope admonition](#gw-scope) at the top of this page. Under that assumption the bosonic Dyson equation decoupled into two scalar equations and could be solved by ordinary division. This section removes the restriction. It keeps a finite set of additional indices on the two-particle objects (Keldysh indices in the application we have in mind, although the algebra only uses that they are finite in number, so orbital indices are covered by the same argument), and shows that the density and magnetic ladders still sum in closed form, with the scalar division replaced by a matrix inversion at every $(\omega, \mathbf{q})$.

Two properties of the local Hubbard interaction survive the addition of these indices, and they are what makes the closed form possible:

1. The bare vertex $F_0$ is independent of frequency and momentum.
2. Every rung of the $ph$ ladder carries the *same* bosonic transfer variable $(\omega, \mathbf{q})$. Inserting one more bubble is therefore an *elementwise product* in $(\omega, \mathbf{q})$, not a new integration.

Together these mean that at each fixed $(\omega, \mathbf{q})$ the ladder recursion is a linear map on a finite-dimensional space, and the ladder itself is a geometric series in that map.

### The rung as a linear map

Let $k_1 k_2 k_3 k_4$ collect the additional indices, each running over a finite range, and let $P^{ph}_{k_1 k_2 k_3 k_4}(\omega,\mathbf{q})$ denote the integrated $ph$ bubble carrying them, the index-resolved generalization of the polarization $P^{ph}(\omega)$ of the [section above](#polarization-and-screened-interaction-in-the-ph-channel), to which it reduces when the indices are dropped. Write the $ph$-reducible vertex with $\ell$ bubble insertions in spin channel $c \in \{d, m\}$ as $\Phi^{(\ell)}_{c; k_1 k_2 k_3 k_4}(\omega, \mathbf{q})$; the parenthesized superscript counts bubble insertions and is not the channel label of the $\Phi^r$ used elsewhere in this documentation.

The additional indices carry no spin label, because the spin projection has already been carried out: the bare vertex entering here is one of the two components $F_{0,d} = -U$ and $F_{0,m} = +U$. Inserting one further bubble between a bare vertex on the left and $\Phi_c^{(\ell)}$ on the right therefore defines one linear map per spin channel,

\begin{align}
    \big(M_c X\big)_{k_1 k_2 k_3 k_4}
      = \sum_{k_5 k_6 k_7 k_8} F_{0,c; k_5 k_2 k_3 k_6}\,
        P^{ph}_{k_8 k_5 k_6 k_7}\, X_{k_1 k_8 k_7 k_4} \, ,
\end{align}

where every factor is evaluated at the same $(\omega, \mathbf{q})$, which is therefore suppressed. Since $F_{0,m} = -F_{0,d}$ for a local interaction, the two maps differ only by an overall sign,

\begin{align}
    M_m = -M_d \, ,
\end{align}

so a single map suffices, and we abbreviate $M \equiv M_d$ from here on. The ladder recursion is then simply

\begin{align}
    \Phi_c^{(\ell+1)} = M_c\, \Phi_c^{(\ell)} \, , \qquad\qquad \Phi_c^{(\ell)} = M_c^{\ell-1}\, \Phi_c^{(1)} \, ,
\end{align}

with $\Phi_c^{(1)} = F_{0,c} \bullet P^{ph} \bullet F_{0,c}$ the second-order vertex. Only the *square* of the bare vertex enters at first order, so $\Phi_m^{(1)} = \Phi_d^{(1)}$, and we write $\Phi^{(1)}$ for their common value. Note that applying $M_c$ is itself one more $\bullet$ contraction, $M_c X = F_{0,c} \bullet P^{ph} \bullet X$, and that this contraction is associative: chains of it need no bracketing, and the resolvents below may be manipulated exactly like matrix inverses.

:::{note}
The indices $k_1$ and $k_4$ are **spectators**: they appear on $X$ and on the result, but are not summed over. $M$ is therefore block diagonal in $(k_1, k_4)$, with identical blocks acting on the pair $(k_2, k_3)$. For two-valued Keldysh indices, $M$ acting on the full $16$-dimensional space is four copies of one $4 \times 4$ block. Either form may be used; an implementation that wants to compare against a dense reference is usually better off with the redundant $16 \times 16$ form, since it matches the index layout of the recursion literally.
:::

### The geometric series

Because $\Phi_c^{(\ell)} = M_c^{\ell-1}\Phi^{(1)}$ with $M_m = -M$, the magnetic ladder is the alternating counterpart of the density one,

\begin{align}
    \Phi_m^{(\ell)} = (-M)^{\ell-1}\, \Phi^{(1)} = (-1)^{\ell+1}\, \Phi_d^{(\ell)} \, ,
\end{align}

which is where the relative sign between the two channels enters. The two channel sums defined [above](#polarization-and-screened-interaction-in-the-ph-channel) therefore become geometric series in the single map $M$,

\begin{align}
    \widetilde{W}_d &= \sum_{\ell \ge 1} \Phi_d^{(\ell)} = \sum_{j \ge 0} M^{j}\, \Phi^{(1)} = \big(\mathbb{1} - M\big)^{-1} \Phi^{(1)} \, , \\
    \widetilde{W}_m &= \sum_{\ell \ge 1} \Phi_m^{(\ell)} = \sum_{j \ge 0} (-M)^{j}\, \Phi^{(1)} = \big(\mathbb{1} + M\big)^{-1} \Phi^{(1)} \, ,
\end{align}

and the $GW$ vertex is the weighted combination

\begin{align}
    \boxed{\ \Phi_{GW} = w_d\, \big(\mathbb{1} - M\big)^{-1} \Phi^{(1)} \ + \ w_m\, \big(\mathbb{1} + M\big)^{-1} \Phi^{(1)} \, , \qquad (w_d, w_m) = \left(\tfrac{1}{4}, \tfrac{3}{4}\right) \ } \, .
\end{align}

This is the announced replacement of the scalar division by a matrix inversion. It is a *pointwise* statement: at each $(\omega, \mathbf{q})$ one inverts a single finite matrix, and no integration couples different transfer variables. The cost is therefore independent of how many ladder orders would have been needed to reach the same accuracy by direct summation.

:::{dropdown} Consistency check: reduction to the scalar case
Setting all additional indices to a single value, $M = M_d \rightarrow F_{0,d} P^{ph} = -U P^{ph}$ and $\Phi^{(1)} \rightarrow F_{0,d}^2 P^{ph} = U^2 P^{ph}$, so that

\begin{align}
    \widetilde{W}_d \rightarrow \frac{U^2 P^{ph}}{1 + U P^{ph}} \, , \qquad\qquad \widetilde{W}_m \rightarrow \frac{U^2 P^{ph}}{1 - U P^{ph}} \, ,
\end{align}

which are exactly the scalar expressions $\widetilde{W}^{ph}_{d/m} = F_{0,d/m}^2 P^{ph} / (1 - F_{0,d/m} P^{ph})$ obtained [above](#polarization-and-screened-interaction-in-the-ph-channel). $\checkmark$
:::

### The static offsets

The objects above are the *dynamic* parts, marked by the tilde exactly as in the scalar case: the static contributions $F_{0,d} = -U$ and $F_{0,m} = +U$ are deliberately not included. They combine into the Hartree term, which is conventionally absorbed into the propagator, and leaving them out keeps the resummed objects decaying at large transfer frequency. Restoring them, if wanted, is the substitution $W_{d/m} = \widetilde{W}_{d/m} + F_{0,d/m}$.

### Convergence and the matrix Stoner criterion

The geometric series converges if and only if the *spectral radius* of the rung, meaning the largest modulus among its eigenvalues $\lambda_i$,

\begin{align}
    \rho\big(M(\omega, \mathbf{q})\big) = \max_i \big| \lambda_i\big(M(\omega,\mathbf{q})\big)\big| \, ,
\end{align}

stays below one at every $(\omega, \mathbf{q})$. The closed forms, by contrast, are defined wherever $\mathbb{1} \mp M$ is invertible, which is a strictly weaker condition. This is the same relationship as between the scalar geometric series in $U P^{ph}$ and the closed-form $W_{d/m}$ noted in the section on [$G_0 W_0$ and self-consistent $GW$](#gw-variants) at the end of this page. The condition $\rho(M) < 1$ is the matrix form of the Stoner criterion: stability of the ladder is a statement about the *leading eigenvalue* of $M$, not about a scalar exceeding one.

:::{important} Which eigenvalue, and with which sign
The magnetic channel carries $(\mathbb{1} + M)^{-1}$, so **the magnetic instability appears as an eigenvalue of $M$ approaching $-1$**, not $+1$. This is the matrix form of the statement made in the [Stoner criterion](#stoner-criterion) section, that the instability lives in the magnetic and not the density channel, and it follows from the same relative sign $F_{0,m} = -F_{0,d}$: in the scalar limit $\lambda(M) = -U P^{ph}$, so $\lambda \rightarrow -1$ is exactly $U P^{ph} \rightarrow 1$.

This has a practical consequence: the modulus of the leading eigenvalue does not identify the channel. Both $\lambda \rightarrow +1$ and $\lambda \rightarrow -1$ give $|\lambda| \rightarrow 1$, but the first makes $(\mathbb{1} - M)^{-1}$ singular and the second $(\mathbb{1} + M)^{-1}$, so the two limits signal instabilities in different channels. What distinguishes them is the sign of the eigenvalue, or its complex phase if it is not real. An implementation that pairs the wrong resolvent with the wrong channel will still produce a finite, smooth and entirely plausible answer, with the instability in the wrong channel and at the wrong temperature, and the error is invisible at $\mathcal{O}(U^2)$, where the two channels coincide.
:::

### Susceptibilities

The susceptibility in channel $c$ is the same $ph$ ladder that produced $\widetilde{W}_c$, except that it begins and ends with a bubble instead of with a bare vertex,

\begin{align}
    \chi_c = P^{ph} \; + \; P^{ph} \bullet F_{0,c} \bullet P^{ph} \; + \; P^{ph} \bullet F_{0,c} \bullet P^{ph} \bullet F_{0,c} \bullet P^{ph} \; + \; \dots
\end{align}

Each further order prepends one more factor $P^{ph} \bullet F_{0,c}$, so the term with $j$ interaction lines is $\big(P^{ph} \bullet F_{0,c}\big)^{j} P^{ph}$. This is a geometric series of exactly the kind summed above, and it closes the same way,

\begin{align}
    \chi_c = \big(\mathbb{1} - P^{ph} \bullet F_{0,c} \big)^{-1} P^{ph} \, ,
\end{align}

with the density and magnetic cases differing only through $F_{0,m} = -F_{0,d}$. Setting all additional indices to a single value gives $\chi_d \rightarrow P^{ph}/(1 + U P^{ph})$ and $\chi_m \rightarrow P^{ph}/(1 - U P^{ph})$, the two susceptibilities of the [scalar case](#polarization-and-screened-interaction-in-the-ph-channel). $\checkmark$

The rung of this series carries the same two factors as $M_c$ but in the opposite order, a bubble followed by a vertex rather than a vertex followed by a bubble, simply because the ladder now starts at a bubble. Written out in the additional indices it is the formula for $M_c$ with the two factors exchanged,

\begin{align}
    \Big(\big(P^{ph} \bullet F_{0,c}\big) \bullet X\Big)_{k_1 k_2 k_3 k_4}
      = \sum_{k_5 k_6 k_7 k_8} P^{ph}_{k_5 k_2 k_3 k_6}\,
        F_{0,c; k_8 k_5 k_6 k_7}\, X_{k_1 k_8 k_7 k_4} \, ,
\end{align}

again at fixed $(\omega, \mathbf{q})$. The indices $k_1$ and $k_4$ are spectators here too, so the block structure noted for $M_c$ carries over unchanged. Dropping the indices collapses both orders to the same product $F_{0,c} P^{ph}$, which is why a single map sufficed in the scalar case.

:::{warning} $\chi_c$ is not $\widetilde{W}_c / U^2$ once the indices are present
The two objects are built from the same ladder, and differ only in what sits at its two ends:

\begin{align}
    \widetilde{W}_c = F_{0,c} \bullet \chi_c \bullet F_{0,c} \, .
\end{align}

While $F_{0,c} = \mp U$ is a number, those two end vertices are nothing but the factor $U^2$, and dividing it out turns one object into the other. This is the origin of the scalar identification $\widetilde{W}_{d/m} = U^2 \chi_{d/m}$. Once the vertices carry indices they are tensors, and dividing $\widetilde{W}_c$ by $U^2$ does not remove them: what remains still has a vertex attached at each end, and is not a susceptibility.
:::

These are RPA susceptibilities in the strict sense only if $P^{ph}$ is built from bare propagators. The same caveat as in the scalar case applies here verbatim.

(which-form-of-the-schwinger-dyson-equation)=
## Which form of the Schwinger-Dyson equation?

The [SDE](parquet_theory.md#schwinger-dyson-equation) can be written in three equivalent ways, and the SBE identities turn each of them into a $GW$-like expression once the Hedin vertices are set to unity,
\begin{align}
    \Sigma &\simeq \frac{1}{2}\zeta \left(F_0 + W^{\overline{ph}}\right) \cdot G  \\
    \Sigma &\simeq \zeta \, W^{pp} \cdot G  \\
    \Sigma &\simeq \frac{1}{2} G \cdot \left(F_0 + W^{ph}\right) \, .
\end{align}
For the *exact* vertex the three forms of the SDE are identical. The three expressions above, however, are not related by an exact identity: each of them involves the replacement $\gamma^r \simeq \mathbf{1}^r$ made *in a specific channel*, and discarding $T^r \circ \chi_0^r \circ \mathbf{1}^r$ is a different approximation for different $r$. So the question of which form to start from is a real one.

It has a partly reassuring answer:

- the **$ph$ form** resums density and magnetic fluctuations, and is the one derived above;
- the **$\overline{ph}$ form** resums the crossed particle-hole ladder. It decouples not in the density/magnetic basis but in the combinations $X_\pm = X_{\uparrow\uparrow} \pm X_{\overline{\uparrow\downarrow}}$, for which the bare interaction takes the values $F_{0,+} = +U$ and $F_{0,-} = -U$. Nevertheless it gives **exactly the same** self-energy as the $ph$ form, to all orders;
- the **$pp$ form** resums the particle-particle ladder, i.e. it is a $T$-matrix approximation. In the singlet/triplet basis the bare interaction is $F_{0,s} = -2U$ and $F_{0,t}=0$, so only the singlet channel is screened. It agrees with the other two at $\mathcal{O}(U^2)$, as it must, but differs from $\mathcal{O}(U^3)$ onwards.

:::{important}
That the two particle-hole forms agree is not an accident: the $ph$ and $\overline{ph}$ channels are crossing images of each other, and so are the two loop products. The crossing asymmetry of the single-channel ladder is exactly compensated by the crossing asymmetry of the loop product it is contracted with. This is a welcome result, because it means that the $GW$ approximation for the Hubbard interaction does *not* inherit the ambiguity in the labelling of the two particle-hole channels discussed in the note on [$ph \leftrightarrow \overline{ph}$](two-particle-channels.md#note-on-possible-confusion-regarding-ph-leftrightarrow-overline-ph).
:::

:::{dropdown} Explicit calculation: the $\overline{ph}$ form gives the same self-energy
The spin structure of the $\overline{ph}$ contraction is
$[A \circ \chi_0^{\overline{ph}} \circ B]_{\sigma_1\sigma_2\sigma_3\sigma_4} = \sum_{\sigma_5,\sigma_6} A_{\sigma_1 \sigma_2 \sigma_5 \sigma_6} \bullet \chi_0^{\overline{ph}} \bullet B_{\sigma_6 \sigma_5 \sigma_3 \sigma_4}$, and spin conservation forces $\sigma_5 = \sigma_6$. The resulting spin table is the $\overline{ph}$ row of the table in the section on [second-order perturbation theory](second_order_perturbation_theory.md#spin-structure); it shows that the combinations $X_\pm = X_{\uparrow\uparrow} \pm X_{\overline{\uparrow\downarrow}}$ decouple, in complete analogy with the density/magnetic basis of the $ph$ channel. Using $X_{\overline{\uparrow\downarrow}} = X_m$ and $X_{\uparrow\uparrow} = \tfrac{1}{2}(X_d + X_m)$,
\begin{align}
    X_+ = \tfrac{1}{2}\left(X_d + 3X_m\right) \, , \qquad\qquad X_- = X_{\uparrow\downarrow} = \tfrac{1}{2}\left(X_d - X_m\right) \, ,
\end{align}
and for the bare vertex $F_{0,+} = 0 + U = U$, $F_{0,-} = 0 - U = -U$.

The $\overline{ph}$ bubble carries no closed-loop sign, $[A \circ \chi_0^{\overline{ph}} \circ B](\nu,\nu',\omega) = \int_{\nu''} A\, G(\nu'')G(\nu''+\omega)\, B$, so its polarization is
\begin{align}
    P^{\overline{ph}}(\omega) = \int_\nu G(\nu) G(\nu+\omega) = - P^{ph}(\omega) \, .
\end{align}
The two screened interactions of the $\overline{ph}$ channel therefore are
\begin{align}
    W^{\overline{ph}}_{\pm} = \frac{F_{0,\pm}}{1 - F_{0,\pm} P^{\overline{ph}}} = \frac{\pm U}{1 \pm U P^{ph}} \qquad \Longrightarrow \qquad W^{\overline{ph}}_{+} = - W^{ph}_{d} \, , \qquad W^{\overline{ph}}_{-} = - W^{ph}_{m} \, .
\end{align}
The $\overline{ph}$ form of the SDE uses the *other* loop product, which projects onto the density component, $[X \cdot G] \rightarrow X_d$. Expressing $X_d$ through the $\overline{ph}$ eigen-combinations, $X_d = \tfrac{1}{2}(X_+ + 3X_-)$, gives
\begin{align}
    W^{\overline{ph}}_{d} = \tfrac{1}{2}\left(W^{\overline{ph}}_{+} + 3 W^{\overline{ph}}_{-}\right) = -\tfrac{1}{2}\left(W^{ph}_{d} + 3 W^{ph}_{m}\right) \, ,
\end{align}
and therefore, with $\zeta = -1$ and $F_{0,d} = -U$,
\begin{align}
    \Sigma \simeq \frac{1}{2}\zeta \left(F_{0,d} + W^{\overline{ph}}_{d}\right) = -\frac{1}{2} F_{0,d} + \frac{1}{4} W^{ph}_{d} + \frac{3}{4} W^{ph}_{m} = \frac{U}{2} + \frac{1}{4} W^{ph}_{d} + \frac{3}{4} W^{ph}_{m} \, .
\end{align}
The $ph$ form gives $\tfrac{1}{4}(F_{0,d} + W^{ph}_d) + \tfrac{3}{4}(F_{0,m} + W^{ph}_m)$, whose static part is $\tfrac{1}{4}(-U) + \tfrac{3}{4}(+U) = U/2$. The two agree. $\checkmark$

Finally, the bosonic argument matches as well: the $\overline{ph}$ loop yields $\omega_{\overline{ph}} = \nu' - \nu$ rather than $\nu - \nu'$, but the bubble is even in the transfer frequency, $P(-\omega) = P(\omega)$, as follows from shifting the integration variable.
:::

:::{danger} To do
Quantify how much the $pp$ variant differs from the particle-hole one at $\mathcal{O}(U^3)$, and whether anything can be said about which is closer to the exact result. Relatedly, one could construct a crossing-symmetrized variant by combining the particle-hole and particle-particle forms, which is essentially what the FLEX approximation does.
:::

(gw-variants)=
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
