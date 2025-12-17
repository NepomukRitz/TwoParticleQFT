# Basic definitions

## Propagator

The one-particle propagator (or Green's function) is the two-point correlation function defined as
\begin{align}
G_{21} = -\langle c_2 \bar{c}_1 \rangle\, .
\end{align}
where (imaginary) time-ordering is implied. It is represented diagrammatically as
:::{image} diagrams/G.svg
:width: 100px
:::

## Four-point correlation function

The four-point correlation function is defined as
\begin{align}
G^{(4)}_{4231} = \langle c_4 c_2 \bar{c}_3 \bar{c}_1 \rangle\, .
\end{align}

Note that in general, the order of multi-indices in correlation functions (such as $G$ and $G^{(4)}$) is reversed compared to that in vertex functions (such as $\Sigma$ and $F$).

:::{note}
We can make contact with the convention used in some papers by relabeling the indices in $G^{(4)}$ as
\begin{align}
G^{(4)}_{1234} = \langle c_1 c_3 \bar{c}_2 \bar{c}_4 \rangle = \zeta \langle c_1 \bar{c}_2 c_3 \bar{c}_4 \rangle\, .
\end{align}
This definition is consistent with many papers employing the Vienna convention, apart from an additional sign $\zeta$ for fermions. This sign factor leads to a global minus sign in the definition of all four-point quantities (vertex, susceptibilities, etc.) compared to the Munich convention.

:::

## Self-energy

Write down Dyson equation already here!

## Two-particle vertex

In a theory of strongly correlated electrons, the full two-particle electron-electron vertex is denoted as

\begin{equation*}
F(1, 2, 3, 4) \equiv F_{1234} =
\end{equation*}

:::{image} diagrams/F.svg
:width: 100px
:::

Here, the multi-indices $1$ and $3$ label the incoming particles, while $2$ and $4$ label the outgoing particles. Each multi-index contains all quantum numbers of the corresponding particle, e.g., momentum, frequency, spin, and orbital.

:::{note}
This labeling of multi-indices is consistent with the conventions used in the Vienna community.
We choose to number the indices in diagrams going clockwise, starting from the top left corner.
Reason: This way, the diagrammatics are consistent with the Munich literature.
:::

## Two-particle channels

The full vertex $F$ can be decomposed into contributions from different two-particle channels. The main channels are the particle-hole ($ph$) channel, the transverse particle-hole ($\overline{\text{ph}}$) channel, and the particle-particle ($pp$) channel. Each channel corresponds to a specific way of connecting the incoming and outgoing particles.


## To Do

- generalized susceptibilities?
- four-point correlation function?