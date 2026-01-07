# Single boson exchange decomposition and approximation

The *single boson exchange* (SBE) decomposition is an alternative way to decompose the full vertex $F$ into diagrammatic contributions, based on the idea that many interaction processes can be effectively described by the exchange of a single bosonic particle (e.g., a spin or charge fluctuation). 

## Interaction reducibility

This framework employs the concept of *interaction reducibility* (also called $U$-reducibility), which is related but distinct from the two-particle reducibility used in [parquet theory](parquet_theory.md). Any given diagram is called *$U$-reducible* if it can be separated into two parts by removing a single bare internal interaction vertex $F_0$. There are three distinct channels in which this can happen, corresponding to the same channels as in two-particle reducibility: the particle-hole ($ph$), the transverse particle-hole ($\overline{ph}$), and the particle-particle ($pp$) channel. Indeed, any diagram that is $U$-reducible in channel $r$ is also two-particle reducible in that channel. The inverse is not true, however.

:::{danger} To do
Illustrate the concept of $U$-reducibility with diagrams.
:::

## SBE decomposition

The sum of all diagrams that are $U$-reducible in channel $r$ is denoted by $\Delta^r$, while the sum of all diagrams that are not $U$-reducible in any of the three channels is denoted by $\Lambda^{U}$. The full vertex $F$ can then be decomposed as
\begin{align}
    F = \Lambda^{U} + \sum_{r \in \{\overline{ph}, pp, ph\}} \Delta^{r} - 2F_0 \, .
\end{align}
The bare interaction vertex $F_0$ is formally $U$-reducible in all three channels and therefore contained in each of the three $\Delta^r$. To avoid double counting, we therefore need to subtract $2F_0$.

:::{warning}
Make sure not to confuse the $U$-reducible diagrams $\Delta^r$ with a hybridization function $\Delta(\nu)$ appearing in impurity models. 
:::

Similarly to the parquet theory, one can also define the *$U$-irreducible vertex in channel $r$* as
\begin{align}
    T^r = F - \Delta^r = \Lambda^{U} + \sum_{r' \neq r} \Delta^{r'} - 2F_0 \, .
\end{align}

## SBE equations

The main strength of the SBE decomposition over the parquet decomposition lies in significant simplifications in the case where the bare interaction $F_0$ is local (i.e., momentum-independent) and instantaneous (i.e., frequency-independent), (as, e.g., in the Hubbard model). As in the chapter on [two-particle channels](two-particle-channels#connectors-and-identity-operators), it is in this case useful to introduce a unit vertex for non-frequency-momentum quantum numbers in channel $r$, $\mathbf{1}^r$, which satisfies $F = \mathbf{1}^r \bullet F = F \bullet \mathbf{1}^r$, where the symbol $\bullet$ denotes contractions over all quantum numbers, indices and other degrees of freedom except frequency (and momenta).

One then defines the *Hedin vertices* $\gamma^r$ as
\begin{align}
    \gamma^r &= \mathbf{1}^r + \mathbf{1}^r \circ \chi^r_0 \circ T^r \\
    \overline{\gamma}^r &= \mathbf{1}^r + T^r \circ \chi^r_0 \circ \mathbf{1}^r \, ,
\end{align}
where $\chi^r_0$ is the dressed bubble in channel $r$. The Hedin vertices are $U$-reducible in channel $r$ and, crucially, depend only on two frequenies (or momenta), since the dependence on the third frequency is trivially contracted away through the $\circ$ contraction with $\mathbf{1}^r$. 

The Hedin vertices describe the effective coupling between fermionic particles and collective bosonic fluctuations in channel $r$, as can be seen from the main result of SBE theory:
The $U$-reducible diagrams in channel $r$ can be written as
\begin{align}
    \Delta^r = \overline{\gamma}^r \bullet W^r \bullet \gamma^r \, ,
\end{align}
where $W^r$ is the *screened interaction* in channel $r$, defined through the *bosonic Dyson equation*
\begin{align}
    W^r &= F_0 + F_0 \circ \chi^r_0 \circ \overline{\gamma}^r \bullet W^r \\
    &= F_0 + W^r \bullet \gamma^r \circ \chi^r_0 \circ F_0 \, .
\end{align}
Again, the screened interaction is $U$-reducible in channel $r$ and, crucially, depends only on a single frequency or momentum (for an instantaneous or local bare interaction, respectively).

Defining the polarizations in channel $r$ as
\begin{align}
    P^r &= \gamma^r \circ \chi_0^r \circ \mathbf{1}^r \\
    &= \mathbf{1}^r \circ \chi_0^r \circ \overline{\gamma}^r\, ,
\end{align}
the bosonic Dyson equation can be written more compactly as
\begin{align}
    W^r = F_0 + F_0 \bullet P^r \bullet W^r = F_0 + W^r \bullet P^r \bullet F_0 \, .
\end{align}

In summary, the equations to solve for the $U$-reducible contributions of the vertex read,
\begin{align}
     W^r &= F_0 + F_0 \bullet P^r \bullet W^r = F_0 + W^r \bullet P^r \bullet F_0 \\
     P^r &= \gamma^r \circ \chi_0^r \circ \mathbf{1}^r = \mathbf{1}^r \circ \chi_0^r \circ \overline{\gamma}^r \\
     \gamma^r &= \mathbf{1}^r + \mathbf{1}^r \circ \chi_0^r \circ T^r \\
     \overline{\gamma}^r &= \mathbf{1}^r + T^r \circ \chi_0^r \circ \mathbf{1}^r \\
     T^r &= F - \overline{\gamma}^r \bullet W^r \bullet \gamma^r\, .
\end{align}
As in parquet theory, these equations can be solved self-consistently by iteration, starting from an initial guess. Again, this procedure requires knowledge of the $U$-irreducible vertex $\Lambda^{U}$ to compute $T^r$ from $F$, which is generally unknown. In practice, one therefore often resorts to approximations for $\Lambda^{U}$, such as the *SBE approximation*, discussed [below](single-boson-exchange#sbe-approximation).

## Schwinger-Dyson equation in SBE form

Finally, the self-energy should again be included through the Schwinger-Dyson equation (SDE) as discussed in the chapter on [parquet theory](parquet_theory.md#schwinger-dyson-equation). In terms of SBE objects, it takes a simple form, since one can derive that
\begin{align}
    F_0 \circ \chi_0^r \circ F &= W^r \bullet \gamma^r - F_0 \\
    F \circ \chi_0^r \circ F_0 &= \overline{\gamma}^r \bullet W^r - F_0 \, .
\end{align}

:::{dropdown} Explicit derivation
Using the decomposition of the $U$-reducible diagrams into Hedin vertices and screened interactions, as well as the definition of the polarizations, and the Dyson equation for the screened interaction, we have
\begin{align}
    F_0 \circ \chi_0^r \circ F &= F_0 \circ \chi_0^r \circ \left( \Delta^r + T^r \right) \\
    &= F_0 \circ \chi_0^r \circ \left( \overline{\gamma}^r \bullet W^r \bullet \gamma^r + T^r \right) \\
    &= F_0 \bullet \mathbf{1}^r \circ \chi_0^r \circ \overline{\gamma}^r \bullet W^r \bullet \gamma^r + F_0 \bullet \mathbf{1}^r \circ \chi_0^r \circ T^r \\
    &= F_0 \bullet P^r \bullet W^r \bullet \gamma^r + F_0 \bullet \gamma^r - F_0 \\
    &= W^r \bullet \gamma^r - F_0 \bullet \gamma^r + F_0 \bullet \gamma^r - F_0 \\
    &= W^r \bullet \gamma^r - F_0 \, ,
\end{align}
and similarly,
\begin{align}
    F \circ \chi_0^r \circ F_0 &= \left( \Delta^r + T^r \right) \circ \chi_0^r \circ F_0 \\
    &= \left( \overline{\gamma}^r \bullet W^r \bullet \gamma^r + T^r \right) \circ \chi_0^r \circ F_0 \\
    &= \overline{\gamma}^r \bullet W^r \bullet \gamma^r \circ \chi_0^r \circ \mathbf{1}^r \bullet F_0 + T^r \circ \chi_0^r \circ \mathbf{1}^r \bullet F_0 \\
    &= \overline{\gamma}^r \bullet W^r \bullet P^r \bullet F_0 + \overline{\gamma}^r \bullet F_0 - F_0 \\
    &= \overline{\gamma}^r \bullet W^r - \overline{\gamma}^r \bullet F_0 + \overline{\gamma}^r \bullet F_0 - F_0 \\
    &= \overline{\gamma}^r \bullet W^r - F_0\, .\ \checkmark
\end{align}
:::

The SDE can therefore be written as
\begin{align}
    \Sigma &= \frac{1}{2} \zeta (F_0 + W^{\overline{ph}} \bullet \gamma^{\overline{ph}}) \cdot G \\
    &= \zeta (W^{pp} \bullet \gamma^{pp}) \cdot G \\
    &= \frac{1}{2} G \cdot (F_0 + \overline{\gamma}^{ph} \bullet W^{ph}) \, .
\end{align}

:::{danger} To do
- Add diagrammatic representations of the SBE equations. 
- Elaborate on the relation to the parquet equations. In particular, introduce multi-boson exchange diagrams.
- Formulate the SBE equations in terms of decaying objects (i.e. subtracting the bare interaction from the screened interaction, and subtract the identity from the Hedin vertices).
- Discuss what changes if the bare interaction is non-local or retarded.
- Add references to the original literature on SBE theory.
:::

## SBE approximation

In the *SBE approximation*, one neglects the $U$-irreducible vertex altogether $\Lambda^{U} \simeq 0$. This approximation is motivated by the conjecture that, in many physical situations, the dominant contributions to the full vertex arise from the exchange of single bosonic fluctuations, while more complex processes involving multiple boson exchanges are less important. Since $F \simeq \sum_r \Delta^r - 2F_0$ in this approximation, we have for the $U$-irreducible vertex in channel $r$,
\begin{align}
    T^r &\simeq \sum_{r' \neq r} \Delta^{r'} - 2F_0 \\
    &= \sum_{r' \neq r} \overline{\gamma}^{r'} \bullet W^{r'} \bullet \gamma^{r'} - 2F_0 \, .
\end{align}

We note in passing, that the SBE formulation of the SDE is reminiscent of the equation for $\Sigma$ in the $GW$ approximation. Indeed, the $GW$ approximation can be seen as a further simplification of the SBE approximation, where the Hedin vertices are approximated by their lowest-order contribution, $\gamma^r \simeq \mathbf{1}^r$ and $\overline{\gamma}^r \simeq \mathbf{1}^r$. The self-energy is then given by 
\begin{align}
    \Sigma \simeq \zeta W^{pp} \cdot G \, ,
\end{align}
which is precisely the $GW$ expression for the self-energy.