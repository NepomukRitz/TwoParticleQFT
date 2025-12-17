# Starting point: Many-body Hamiltonian and action

We begin with a general many-body Hamiltonian for interacting particles in second quantization, $H[c^\dagger, c]$, for which the partition function is given by the path integral in imaginary time,
\begin{align}
    Z &= \int \mathcal{D}[\bar{c}, c] \, e^{-S[\bar{c}, c]} \\
    S[\bar{c}, c] &= \int_0^\beta d\tau \left\{ \sum_1 \bar{c}_1(\tau) \partial_\tau c_1(\tau) + H[c_1^\dagger(\tau), c_1(\tau+0^-)] \right\} = S_0 + S_I\, .
\end{align}

:::{note}
The shift by a negative infinitesimal in $c^\dagger(\tau) c(\tau+0^-)$ ensures that the normal ordering $\bar{c}c$ is preserved in perturbative expansions.
:::

The multi-index $1$ denotes all quantum numbers of the fields, e.g. momentum, spin, and orbital.

In generic notation, we can write for an arbitrary quartic interaction:
\begin{align}
S = S_0 + S_I &= -\sum_{1,2} \bar{c}_1 (G_0)^{-1}_{12} c_2 - \frac{1}{4} \sum_{1,2,3,4} \bar{c}_1 \bar{c}_3 F_{0;1234} c_2 c_4 \, .
\end{align}

:::{note}
- $(G_0)^{-1}_{12}$ must be negative definite (i.e. all its eigenvalues must be negative) to ensure convergence of the path integral.
- The minus sign in front of the interaction term cancels the minus signs in the expansion of $e^{-S_I}$.
- The sums over multi-indices will be omitted in the future; summation over repeated indices is implied.
- $F_0$ is (anti-) symmetric in the arguments: $F_{0;1234} = \zeta F_{0;3214} = \zeta F_{0;1432} = \zeta^2 F_{0;3412}$, where $\zeta = -1$ for fermions and $\zeta = +1$ for bosons. The factor $(1/2)^2=1/4$ above compensates for summing over terms that are identical due to this *crossing symmetry*.
:::

:::{warning}
**About conventions**

- Different communities use different conventions for numbering the multi-indices. Here, we follow the Vienna convention and use the arabic numbers $(1,2)$ for two-point functions and $(1,2,3,4)$ for four-point functions. In the Munich convention, the action is parametrized as 
\begin{align}
S = - \bar{c}_{1'} (G_0)^{-1}_{1'1} c_{1} - \frac{1}{4} \bar{c}_{1'} \bar{c}_{2'} F_{0;1'2'|12} c_2 c_1 \, .
\end{align}
When converting between the two conventions, we can therefore use the correspondences
\begin{align}
(1,2) &\leftrightarrow (1',1) \\
(1,2,3,4) &\leftrightarrow (1', 2, 2', 1) \, .
\end{align}
:::

Diagrammatically, the bare four-point vertex $F_0$ is represented as the Hugenholtz diagram,
:::{image} diagrams/F_0.svg
:width: 100px
:::
where we number the legs clockwise starting from the bottom left.