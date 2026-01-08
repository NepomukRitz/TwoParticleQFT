# Two-particle QFT in the real-frequency Keldysh formalism

Alternatively to the imaginary-time (Matsubara) formalism used on the other pages, two-particle quantum field theory can also be formulated in the real-frequency Keldysh formalism. This is particularly useful for studying non-equilibrium steady states, but can also be applied to equilibrium situations, avoiding the need for analytic continuation from imaginary to real frequencies.

:::{note}
Here, we will only discuss the Keldysh formalism in the steady state, which permits a Fourier transform from time to frequency space. In time-dependent situations, the two-particle quantities depend on more complicated time arguments (e.g., two-particle Green's functions depend on four time arguments), which makes the treatment more involved. We do not discuss this case here.
:::

## Many-body action in the Keldysh formalism

We begin again with the many-body Hamiltonian in second quantization. In the Keldysh formalism, the partition function is given by the path integral
\begin{align}
    Z &= \int \mathcal{D}[\bar{c}, c] \,e^{i S[\bar{c}, c]} \\
    S[\bar{c}, c] &= \int_\mathcal{C} dt \left\{ \sum_1 \bar{c}_1(t) i \partial_t c_1(t) - H[c_1^\dagger(t), c(t)] \right\} = S_0 + S_I \, ,
\end{align}
where the time integral runs along the Keldysh contour $\mathcal{C}$, which consists of a forward and backward branch running from $t=-\infty$ to $t=+\infty$ and back. The fields $\bar{c}_1(t)$ and $c_1(t)$ are defined on the contour, with the index $1$ again denoting all single-particle quantum numbers (e.g., momentum, spin, ...).

For an arbitrary quartic interaction, we can write the action as
\begin{align}
    S = S_0 + S_I = \overline{c}_1 (G_0^{-1})_{12} c_2 + \frac{1}{4} \overline{c}_1 \overline{c}_3 F_{0,1234} c_2 c_4 \, ,
\end{align}
where repeated indices imply summation/integration. Here, $G_0$ is the bare propagator and $F_0$ the bare four-point vertex, defined on the Keldysh contour.

## Correlation functions

The two-point and four-point correlation functions are defined as in the Matsubara formalism, with an additional contour-ordering operator $\mathcal{T}_\mathcal{C}$ and one factor of $i$,
\begin{align}
    G_{21} &= -i \langle \mathcal{T}_\mathcal{C} c_2 \overline{c}_1 \rangle \, , \\
    G^{(4)}_{4231} &= i \langle \mathcal{T}_\mathcal{C} c_4 c_2 \overline{c}_3 \overline{c}_1 \rangle \, .
\end{align}

:::{dropdown} Note on signs and prefactors
The factors of $i$ are motivated as follows. Correlation functions are most cleanly derived as functional derivatives of a generating functional with respect to source fields. The generating function in the Keldysh formalism reads
\begin{align}
    Z[\bar{J}, J] = \int \mathcal{D}[\bar{c}, c] \,e^{i S[\bar{c}, c] + i \bar{J} c + i \overline{c} J} \, .
\end{align}
Now, due to the factor of $i$ in the exponent, each functional derivative with respect to a source field brings down a factor of $i$, 
\begin{align}
    \frac{\delta}{\delta \bar{J}} &\leftrightarrow i c \, ; & \frac{\delta}{\delta J} &\leftrightarrow i \overline{c} \, .
\end{align}
Hence, a contour-ordered $2n$-point correlation function will contain a prefactor of $1/i^{(2n)}$,
\begin{align}
    \langle T_\mathcal{C} c_1 \ldots c_n \overline{c}_{n+1} \ldots \overline{c}_{2n} \rangle = \frac{1}{i^{2n}} \frac{1}{Z} \frac{\delta^{2n} Z}{\delta \bar{J}_1 \ldots \delta \bar{J}_n \delta J_{n+1} \ldots \delta J_{2n}} \Bigg|_{\bar{J}=J=0} \, .
\end{align}
Now, for an interacting theory, such computations cannot be done exactly. But we can do them for a non-interacting theory, for which we can compute the Gaussian path integral. The generating functional for the non-interacting theory reads
\begin{align}
    Z_0[\bar{J}, J] &= \int \mathcal{D}[\bar{c}, c] \,e^{i \bar{c} (G_0^{-1}) c + i \bar{J} c + i \overline{c} J} \\
    &= Z_0[0,0] \, e^{-i \bar{J} G_0 J} \, ,
\end{align}
where $Z_0[0,0]$ is the partition function of the non-interacting theory without sources. Taking functional derivatives, we find that each pair of fields contributes a factor of $-i G_0$ to the correlation function,
\begin{align}
    \frac{\delta^2 Z_0[\bar{J}, J]}{\delta \bar{J} \delta J} &= (-i) G_{0} Z_0 \, .
\end{align}
We hence find that the two-point correlation function is given by
\begin{align}
    \langle T_\mathcal{C} c \overline{c} \rangle_0 = \frac{1}{i^2} (-i) G_0 = i G_0 \ \Leftrightarrow \ G_0 = -i \langle T_\mathcal{C} c \overline{c} \rangle_0 \, .
\end{align}
By analogy, we demand the same normalization for the interacting theory.

For higher-point correlation functions, the situation is not so clear and indeed different conventions exist in the literature. Here, we follow the commonly used convention that an $n$-point correlation function contains a prefactor of $(-i)^{(n-1)}$.
:::

As a consequence, the tree expansion of the four-point correlation function reads
\begin{align}
    iG^{(4)}_{4231} = G_{41} G_{23} + \zeta G_{43} G_{21} + i G^{(4)}_{c,4321}\, ,
\end{align}
with the connected part given by
\begin{align}
    G^{(4)}_{c,4321} = - G_{4\tilde{1}} G_{2\tilde{3}} F_{\tilde{1}\tilde{2}\tilde{3}\tilde{4}} G_{\tilde{2}3} G_{\tilde{4}1}\, .
\end{align}

::::{dropdown} Note on signs and prefactors
For the disconnected terms, this form of the tree-expansion is motivated by the non-interacting case, where Wick's theorem gives
\begin{align}
    G^{(4)}_{0, 4321} &= i \langle T_\mathcal{C} c_4 c_2 \overline{c}_3 \overline{c}_1 \rangle_0 = i \left( \langle T_\mathcal{C} c_4 \bar{c}_1\rangle_0 \langle T_\mathcal{C} c_2 \bar{c}_3\rangle_0 + \zeta \langle T_\mathcal{C} c_4 \bar{c}_3\rangle_0 \langle T_\mathcal{C} c_2 \bar{c}_1\rangle_0 \right) \\
    &= i \left( i G_{0,41} i G_{0,23} + \zeta i G_{0,43} i G_{0,21} \right) = -i \left( G_{0,41} G_{0,23} + \zeta G_{0,43} G_{0,21} \right) \\ & \\
    \Leftrightarrow \quad i G^{(4)}_{0, 4321} &= G_{0,41} G_{0,23} + \zeta G_{0,43} G_{0,21} \, .
\end{align}

The sign of the connected part is best motivated by the first-order contribution in perturbation theory in the bare interaction $F_0$,
:::{image} diagrams/G4_PT.png
:::
::::

