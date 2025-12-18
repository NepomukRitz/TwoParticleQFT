## Two-particle channels

All diagrams contributing to the connected four-point correlator (or, equivalently, the four-point vertex) can be classified with respect to the property of two-particle reducibility. A diagram is called *two-particle reducible* if it can be separated into two parts by cutting a pair of internal propagator lines. Otherwise, it is called *two-particle irreducible*. The set of all two-particle reducible diagrams can furthermore be uniquely decomposed into three topologically distince *two-particle channels*: the particle-particle ($pp$) channel, and the two particle-hole channels ($ph$ and $\overline{ph}$). These channels are defined based on how two pairs of external legs can be separated by cutting two internal propagator lines. 

The three channels are apparent already at the level of the second-order diagrams in perturbation theory. For the connected four-point correlator, we obtain three contributions beyond the first-order diagram:

\begin{align}
G^{(4)}_{c,4321} &= G_{0,4\tilde{1}} G_{0,\tilde{2}3} F_{0,\tilde{1}\tilde{2}\tilde{3}\tilde{4}} G_{0,2\tilde{3}} G_{0,\tilde{4}1} \\
&\phantom{=} + G_{0,4\tilde{1}} G_{0,\tilde{2}3} F_{0,\tilde{1}\tilde{2}\tilde{5}\tilde{6}} G_{0,\tilde{6}\tilde{7}} G_{0,\tilde{8}\tilde{5}} F_{0,\tilde{7}\tilde{8}\tilde{3}\tilde{4}} G_{0,2\tilde{3}} G_{0,\tilde{4}1} \quad \text{($\overline{ph}$ channel)} \\
&\phantom{=} + \frac{1}{2} G_{0,4\tilde{1}} G_{0,\tilde{2}3} F_{0,\tilde{1}\tilde{5}\tilde{3}\tilde{6}} G_{0,\tilde{6}\tilde{7}} G_{0,\tilde{5}\tilde{8}} F_{0,\tilde{7}\tilde{2}\tilde{8}\tilde{4}} G_{0,2\tilde{3}} G_{0,\tilde{4}1} \quad \text{($pp$ channel)} \\
&\phantom{=} + \zeta G_{0,\tilde{2} 3} G_{0,2\tilde{3}} F_{0,\tilde{5}\tilde{2}\tilde{3}\tilde{6}} G_{0,\tilde{6}\tilde{7}} G_{0,\tilde{8}\tilde{5}} F_{0,\tilde{1}\tilde{8}\tilde{7}\tilde{4}} G_{0,4\tilde{1}} G_{0,\tilde{4}1} \quad \text{($ph$ channel)} \\
&\phantom{=} + \mathcal{O}(F_0^3)\, .
\end{align}

:::{image} diagrams/G4_PT2.png
:height: 150px
:::


:::{danger} To Do
Derive this expression, including all Wick contractions and sign factors. See Jan's handwritten notes for reference.

Also, since there is some ambiguity in the literature regarding the labeling of the two particle-hole channels, we should clarify our conventions here. Write up Fabian's explanation in an accessible way.

Furthermore, it might be instructive to explicitly show that the $\overline{ph}$ channel contribution equals $\zeta$ times the $ph$ channel contribution by exchanging the indices $2\leftrightarrow 4$. I have handwritten notes on this that just need to be typed up.
:::

From this point on, it is convenient to work directly with the four-point vertex $F$ instead of the connected four-point correlator $G^{(4)}_c$. This change amounts to amputating the external (in this case bare) propagators. In second order perturbation theory, the vertex hence reads

\begin{align}
F_{1234} = F_{0,1234} &+ F_{0,1256} G_{0,67} G_{0,85} F_{0,7834} \quad \text{($\overline{ph}$ channel)}  \\
&+ \frac{1}{2} F_{0,1536} G_{0,67} G_{0,58} F_{0,7284} \quad \text{($pp$ channel)}\\
&+ \zeta F_{0,5236} G_{0,67} G_{0,85} F_{0,1874} \quad \text{($ph$ channel)}\\
&+ \mathcal{O}(F_0^3)\, .
\end{align}

For ease of notation, it is useful to define a *connector* $\circ$ to denote summation over all indices in each two-particle channel as 
\begin{align}
[A\circ B]^{\overline{ph}}_{1234} &= A_{1256} B_{6534} \\
[A\circ B]^{pp}_{1234} &= A_{1536} B_{6254} \\
[A\circ B]^{ph}_{1234} &= A_{5236} B_{1564}\, . 
\end{align}

:::{image} diagrams/connectors.png
:height: 150px
:::

For later use, it is convenient to also define the channel-specific *identity operators* $\mathbb{1}^r$, which fulfill $A = \mathbb{1}^r \circ A = A \circ \mathbb{1}^r$ for all channels $r\in\{\overline{ph}, pp, ph\}$. Explicitly, they are given by
\begin{align}
\mathbb{1}^{\overline{ph}}_{1234} &= \delta_{14} \delta_{23} = \mathbb{1}^{pp}_{1234} \\
\mathbb{1}^{ph}_{1234} &= \delta_{12} \delta_{34} \, .
\end{align}

It is demonstrated explicitly in [Identity operators for the two-particle channel connectors](connector_identities.md) that the identity operators are consistent with the definition of the connectors in each channel.

These identity operators can also be used to define the inverse of a four-point quantity $A$ in each channel as
\begin{align}
[A^{-1}]^r_{1234} \quad \text{such that} \quad [A^{-1}]^r \circ A = A \circ [A^{-1}]^r = \mathbb{1}^r \, .
\end{align}

We furthermore define the *bare bubble* as 
\begin{align}
[\chi_0^0]_{4321} = G_{0,41} G_{0,23} \, .
\end{align}

:::{danger} To Do
The notation is not optimal here. The subscript "$0$" shall indicate that this object is distinct from a susceptibility (in fact, it is effectively the bubble term without vertex corrections). The superscript "$0$" is meant to indicate that this is the bare version of the bubble. However, having two zeros in the same symbol is confusing. We should think about better notation.
:::

This object is used to define the *bare bubble in each two-particle channel* as
\begin{align}
[\chi_0^0]^{\overline{ph}}_{4321} &= [\chi_0^0]_{4321} \\
[\chi_0^0]^{pp}_{4321} &= \frac{1}{2} [\chi_0^0]_{4321} \\
[\chi_0^0]^{ph}_{4321} &= \zeta [\chi_0^0]_{2341} \, .
\end{align}

With these definitions, we have a unified notation for the three two-particle channels, and we can write the second-order perturbation theory expression for the four-point vertex as
\begin{align}
F_{1234} = F_{0,1234} + \sum_{r\in\{\overline{ph}, pp, ph\}}(F_0 \circ [\chi_0^0]^r \circ F_0)_{1234} + \mathcal{O}(F_0^3)\, ,
\end{align}
or simply
\begin{align}
F = F_0 + \sum_{r} F_0 \circ [\chi_0^0]^r \circ F_0 + \mathcal{O}(F_0^3)\, .
\end{align}

An explicit demonstration that the terms $\sum_r F_0 \circ [\chi_0^0]^r \circ F_0$ correctly yield the second-order perturbation theory contributions to the four-point vertex $F$ in all three two-particle channels is given in [Second-order perturbation theory contributions to the vertex](vertex_PT2.md).

For later use, we also define the dressed *bubble*, sometimes also called *Lindhard function*, in the same manner as the bare bubble, but with full propagators instead of bare ones:
\begin{align}
[\chi_0]_{4321} = G_{41} G_{23} \, 
\end{align}
and
\begin{align}
[\chi_0]^{\overline{ph}}_{4321} &= [\chi_0]_{4321} \\
[\chi_0]^{pp}_{4321} &= \frac{1}{2} [\chi_0]_{4321} \\
[\chi_0]^{ph}_{4321} &= \zeta [\chi_0]_{2341} \, .
\end{align}