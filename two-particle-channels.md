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
:::

:::{note}
Note that the connected four-point correlator is crossing symmetric as well, i.e., it is invariant under the exchange of any two external legs (up to a sign factor $\zeta$ for fermions). While this property holds at every order in perturbation theory, each individual two-particle channel is not crossing symmetric. Instead, crossing symmetry relates the $\overline{ph}$ and $ph$ channels to each other, while the $pp$ channel is crossing symmetric itself. On the level of the second-order contributions shown above, this is demonstrated explicitly below.

:::{dropdown} Explicit calculation
Exchanging the two outgoing legs $2\leftrightarrow 4$ in the $ph$ channel contribution, relabeling the internal indices $\tilde{1} \rightarrow \tilde{3}$ and using the crossing symmetry of the bare vertices yields
\begin{align}
    &\zeta G_{0,\tilde{2} 3} G_{0,4\tilde{3}} F_{0,\tilde{5}\tilde{2}\tilde{3}\tilde{6}} G_{0,\tilde{6}\tilde{7}} G_{0,\tilde{8}\tilde{5}} F_{0,\tilde{1}\tilde{8}\tilde{7}\tilde{4}} G_{0,2\tilde{1}} G_{0,\tilde{4}1} \\
    &= \zeta G_{0,\tilde{2} 3} G_{0,4\tilde{1}} F_{0,\tilde{5}\tilde{2}\tilde{1}\tilde{6}} G_{0,\tilde{6}\tilde{7}} G_{0,\tilde{8}\tilde{5}} F_{0,\tilde{3}\tilde{8}\tilde{7}\tilde{4}} G_{0,2\tilde{3}} G_{0,\tilde{4}1} \\
    &= \zeta G_{0,\tilde{2} 3} G_{0,4\tilde{1}} (\zeta F_{0,\tilde{1}\tilde{2}\tilde{5}\tilde{6}}) G_{0,\tilde{6}\tilde{7}} G_{0,\tilde{8}\tilde{5}} (\zeta F_{0,\tilde{7}\tilde{8}\tilde{3}\tilde{4}}) G_{0,2\tilde{3}} G_{0,\tilde{4}1} \\
    &= \zeta G_{0,4\tilde{1}} G_{0,\tilde{2} 3}  F_{0,\tilde{1}\tilde{2}\tilde{5}\tilde{6}} G_{0,\tilde{6}\tilde{7}} G_{0,\tilde{8}\tilde{5}}  F_{0,\tilde{7}\tilde{8}\tilde{3}\tilde{4}} G_{0,2\tilde{3}} G_{0,\tilde{4}1}\, ,
\end{align}
which is indeed $\zeta$ times the $\overline{ph}$ channel contribution. For the $pp$ channel contribution, exchanging the legs $2\leftrightarrow 4$, relabeling the internal indices $\tilde{1} \rightarrow \tilde{3}$ and using the crossing symmetry of just one of the bare vertices gives
\begin{align}
    &\frac{1}{2} G_{0,2\tilde{1}} G_{0,\tilde{2}3} F_{0,\tilde{1}\tilde{5}\tilde{3}\tilde{6}} G_{0,\tilde{6}\tilde{7}} G_{0,\tilde{5}\tilde{8}} F_{0,\tilde{7}\tilde{2}\tilde{8}\tilde{4}} G_{0,4\tilde{3}} G_{0,\tilde{4}1} \\
    &= \frac{1}{2} G_{0,2\tilde{3}} G_{0,\tilde{2}3} F_{0,\tilde{3}\tilde{5}\tilde{1}\tilde{6}} G_{0,\tilde{6}\tilde{7}} G_{0,\tilde{5}\tilde{8}} F_{0,\tilde{7}\tilde{2}\tilde{8}\tilde{4}} G_{0,4\tilde{1}} G_{0,\tilde{4}1} \\
    &= \frac{1}{2} G_{0,4\tilde{1}} G_{0,\tilde{2}3} (\zeta F_{0,\tilde{1}\tilde{5}\tilde{3}\tilde{6}}) G_{0,\tilde{6}\tilde{7}} G_{0,\tilde{5}\tilde{8}} F_{0,\tilde{7}\tilde{2}\tilde{8}\tilde{4}} G_{0,2\tilde{3}}  G_{0,\tilde{4}1}\, ,
\end{align}
which is indeed equal to the $\zeta$ times original $pp$ channel contribution, confirming its crossing symmetry.
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

:::{note}
The gray lines in the image above in this case *do not* indicate propagators, but rather the index contractions specific to each channel. We might want to use a different visual representation (dotted lines?) to avoid confusion.
:::

For later use, it is convenient to also define the channel-specific *identity operators* $\mathbb{1}^r$, which fulfill $A = \mathbb{1}^r \circ A = A \circ \mathbb{1}^r$ for all channels $r\in\{\overline{ph}, pp, ph\}$. Explicitly, they are given by
\begin{align}
\mathbb{1}^{\overline{ph}}_{1234} &= \delta_{14} \delta_{23} = \mathbb{1}^{pp}_{1234} \\
\mathbb{1}^{ph}_{1234} &= \delta_{12} \delta_{34} \, .
\end{align}

:::{dropdown} Explicit calculation
Demonstrating that the identity operators defined this way work as intended is straightforward but somewhat tedious. Here, we explicitly write out all indices for each channel to show that the definitions are correct.
\begin{align}
[A \circ \mathbb{1}^{\overline{ph}}]_{1234} &= A_{1256} \mathbb{1}^{\overline{ph}}_{6534} = A_{1256} \delta_{64} \delta_{53} = A_{1234} \\
[\mathbb{1}^{\overline{ph}} \circ A]_{1234} &= \mathbb{1}^{\overline{ph}}_{1256} A_{6534} = \delta_{16} \delta_{25} A_{6534} = A_{1234}  \\ \\ 
[A \circ \mathbb{1}^{pp}]_{1234} &= A_{1536} \mathbb{1}^{pp}_{6254} = A_{1536} \delta_{64} \delta_{25} = A_{1234} \\
[\mathbb{1}^{pp} \circ A]_{1234} &= \mathbb{1}^{pp}_{1536} A_{6254} = \delta_{61} \delta_{53} A_{6254} = A_{1234}  \\ \\
[A \circ \mathbb{1}^{ph}]_{1234} &= A_{5236} \mathbb{1}^{ph}_{1564} = A_{5236} \delta_{15} \delta_{64} = A_{1234} \\
[\mathbb{1}^{ph} \circ A]_{1234} &= \mathbb{1}^{ph}_{5236} A_{1564} = \delta_{52} \delta_{36} A_{1564} = A_{1234}  \, .
\end{align}

Indeed, the identity operators have the right properties. $\checkmark$
:::

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

:::{dropdown} Explicit calculation
With the definitions of the channel-specific connectors $\circ$ and the bare bubbles $[\chi_0^0]^r$ given above, we have for the three channels:

\begin{align}
\text{$\overline{ph}$:}\quad  [F_0 \circ [\chi_0^0]^{\overline{ph}} \circ F_0]_{1234} &= F_{0,1256} [[\chi_0^0]^{\overline{ph}} \circ F]_{6534} = F_{0,1256} [\chi_0^0]^{\overline{ph}}_{6587} F_{0,7834} \\
&= F_{0,1256} [\chi_0^0]_{6587} F_{0,7834} =  F_{0,1256} G_{0,67} G_{0,85} F_{0,7834} \\ \\
\text{$pp$:}\quad  [F_0 \circ [\chi_0^0]^{pp} \circ F_0]_{1234} &= F_{0,1536} [[\chi_0^0]^{pp} \circ F]_{6254} = F_{0,1536} [\chi_0^0]^{pp}_{6857} F_{0,7284} \\
&= \frac{1}{2} F_{0,1536} [\chi_0^0]_{6857} F_{0,7284} = \frac{1}{2} F_{0,1536} G_{0,67} G_{0,58} F_{0,7284} \\ \\
\text{$ph$:}\quad  [F_0 \circ [\chi_0^0]^{ph} \circ F_0]_{1234} &= F_{0,5236} [[\chi_0^0]^{ph} \circ F]_{1564} = F_{0,5236} [\chi_0^0]^{ph}_{8564} F_{0,1874} \\
&= \zeta F_{0,5236} [\chi_0^0]_{6587} F_{0,1874} = \zeta F_{0,5236} G_{0,67} G_{0,85} F_{0,1874} \, .
\end{align}

These are indeed the correct expressions. $\checkmark$
:::

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