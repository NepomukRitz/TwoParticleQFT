# Two-particle QFT in the real-frequency Keldysh formalism

Alternatively to the imaginary-time (Matsubara) formalism used on the other pages, two-particle quantum field theory can also be formulated in the real-frequency Keldysh formalism. This is particularly useful for studying non-equilibrium steady states, but can also be applied to equilibrium situations, avoiding the need for analytic continuation from imaginary to real frequencies.

:::{note}
Here, we will only discuss the Keldysh formalism in the steady state, which permits a Fourier transform from time to frequency space. In time-dependent situations, the two-particle quantities depend on more complicated time arguments (e.g., two-particle Green's functions depend on four time arguments), which makes the treatment more involved. We do not discuss this case here.
:::

:::{danger} To do
Introduce the Keldysh contour before going into specifics on the many-body action and correlation functions.
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

## Keldysh index structure of two- and four-point functions

Since a general $n$-point function is given via an expectation value of a product of $n$  fields, which can each be placed on either of the two branches of the Keldysh contour, it will have $2^n$ Keldysh components in total.

### Propagator

Starting, with the two-point Green's function, we can arrange its four Keldysh components in a $2\times 2$ matrix,
\begin{align}
    (G^{c_2 c_1}) = 
    \begin{pmatrix}
        G^{--} & G^{-+} \\
        G^{+-} & G^{++}
    \end{pmatrix} \, ,
\end{align}
where the superscripts $c_2, c_1 \in \{-, +\}$ denote whether the corresponding time argument is on the forward or backward branch of the contour, respectively. Explicitly, the components read
\begin{align}
    G^{-|+}(t_2, t_1) &= -i \langle \mathcal{T}_\mathcal{C} c^-(t_2) \overline{c}^+(t_1) \rangle = - \zeta i \langle \overline{c}(t_1) c(t_2) \rangle \equiv G^<(t_2, t_1) \\
    G^{+|-}(t_2, t_1) &= -i \langle \mathcal{T}_\mathcal{C} c^+(t_2) \overline{c}^-(t_1) \rangle = -i \langle c(t_2) \overline{c}(t_1) \rangle \equiv G^>(t_2, t_1) \\
    G^{--}(t_2, t_1) &= -i \langle \mathcal{T}_{\mathcal{C}} c^-(t_2) \overline{c}^-(t_1) \rangle = G^>(t_2, t_1) \theta(t_2 - t_1) + G^<(t_2, t_1) \theta(t_1 - t_2) \\
    G^{++}(t_2, t_1) &= -i \langle \mathcal{T}_{\mathcal{C}} c^+(t_2) \overline{c}^+(t_1) \rangle = G^<(t_2, t_1) \theta(t_2 - t_1) + G^>(t_2, t_1) \theta(t_1 - t_2) \, ,
\end{align}
where we have suppressed all other dependencies for ease of notation. Here, the contour-time-ordering has been made explicit and the *greater* and *lesser* Green's functions $G^>$ and $G^<$ have been introduced.

As can be confirmed by direct calculation, the four Keldysh components are not independent, but satisfy the relation
\begin{align}
    G^{-|+} + G^{+|-} = G^{--} + G^{++} \, .
\end{align}

:::{danger} To do
- Show this explicitly.
- Discuss the caveat that this relation does not hold if $t_1 = t_2$. 
:::

Making use of this redundancy motivates the *Keldysh rotation*, defined as
\begin{align}
    G^{k_2 k_1} = D^{k_2 c_2} G^{c_2 c_1} (D^{-1})^{c_1 k_1} \, ,
\end{align}
with the transformation matrix
\begin{align}
    D &= \frac{1}{\sqrt{2}}
    \begin{pmatrix}
        1 & -1 \\
        1 & 1
    \end{pmatrix}\, ; &
    D^{-1} &= \frac{1}{\sqrt{2}}
    \begin{pmatrix}
        1 & 1 \\
        -1 & 1
    \end{pmatrix} \, .
\end{align}
The Keldysh-rotated Green's function then takes the form
\begin{align}
    (G^{k_2 k_1}) =
    \begin{pmatrix}
        0 & G^A \\
        G^R & G^K
    \end{pmatrix} \, ,
\end{align}
where the component $G^{11}$ vanishes by construction. $G^R(t_2, t_1) = -i \langle [c(t_2), \overline{c}(t_1)]_\zeta \rangle \theta(t_2 - t_1)$ is the physically relevant *retarded Green's function*, $G^A(t_2, t_1) = [G^R(t_1, t_2)]^*$ is the *advanced* component, and $G^K(t_2, t_1) = G^>(t_2, t_1) + G^<(t_2, t_1) = -[G^K(t_1, t_2)]^*$ is the *Keldysh* component.

### Bubble

This Keldysh structure of the propagator carries over to the [bubble](two-particle-channels#bare-and-dressed-bubbles), following directly from its definition as a product of two propagators. In Keldysh space, the bubble reads
\begin{align}
    \chi_0^{k_4, k_3, k_2, k_1} = G^{k_4 k_1} G^{k_2 k_3} \, .
\end{align}

Formally organizing the $16$ Keldysh components in a $4\times 4$ matrix, we find the explicit structure
\begin{align}
    (\chi_0^{k_4 k_3 k_2 k_1}) &=
    \begin{pmatrix}
        1111 & 1112 & 1121 & 1122 \\
        1211 & 1212 & 1221 & 1222 \\
        2111 & 2112 & 2121 & 2122 \\
        2211 & 2212 & 2221 & 2222
    \end{pmatrix} \\
    &= 
    \begin{pmatrix}
        G^{11} G^{11} & G^{12} G^{11} & G^{11} G^{21} & G^{12} G^{21} \\
        G^{11} G^{12} & G^{12} G^{12} & G^{11} G^{22} & G^{12} G^{22} \\
        G^{21} G^{11} & G^{22} G^{11} & G^{21} G^{21} & G^{22} G^{21} \\
        G^{21} G^{12} & G^{22} G^{12} & G^{21} G^{22} & G^{22} G^{22}
    \end{pmatrix} \\
    &=
    \begin{pmatrix}
        0 & 0 & 0 & G^A G^R \\
        0 & G^A G^A & 0 & G^A G^K \\
        0 & 0 & G^R G^R & G^K G^R \\
        G^R G^A & G^K G^A & G^R G^K & G^K G^K
    \end{pmatrix}\, .
\end{align}


### Self-energy

The Keldysh rotation can be applied to the self-energy, $\Sigma^{k_1 k_2} = D^{k_1 c_1} \Sigma^{c_1 c_2} (D^{-1})^{c_2 k_1}$, leading to the following Keldysh structure,
\begin{align}
    (\Sigma^{k_1 k_2}) =
    \begin{pmatrix}
        \Sigma^{K} & \Sigma^{R} \\
        \Sigma^{A} & 0
    \end{pmatrix} \, .
\end{align} 
Due to causality, the component $\Sigma^{22}$ vanishes identically. Note that, compared to $G$, the Keldysh indices $k_1$ and $k_2$ of the self-energy are interchanged.

:::{dropdown} Reason why
This fact can be most easily motivated by looking at the Dyson equation in the form $G^{-1} = G_0^{-1} - \Sigma$. Since in the inverse of the $2\times 2$ Keldysh matrix 
\begin{align}
\begin{pmatrix}
    0 & A \\
    R & K
\end{pmatrix}^{-1} = 
\frac{1}{0\cdot K - A R} 
\begin{pmatrix}
    K & -A \\
    -R & 0
\end{pmatrix} =
\begin{pmatrix}
    -A^{-1} K R^{-1} & R^{-1} \\
    A^{-1} & 0
\end{pmatrix} \, ,
\end{align}
the positions of the retarded and advanced components are swapped, and the other non-trivial component is the $1\times 1$ component. It follows that the self-energy must have the same structure.
:::

### Dyson equation

Speaking of the Dyson equation, which reads in its most general form
\begin{align}
    G = G_0 + G_0 \circ \Sigma \circ G \, ,
\end{align}
where the connector $\circ$ denotes contractions in time and single-particle quantum numbers. Making the Keldysh structure explicit, separate Dyson equations for the individual Keldysh components can be derived. They read
\begin{align}
    G^{R} &= G_0^{R} + G_0^{R} \bullet \Sigma^{R} \bullet G^{R} \, , \\
    G^{A} &= G_0^{A} + G_0^{A} \bullet \Sigma^{A} \bullet G^{A} \, , \\
    G^{K} &= (1 + G^{R} \bullet \Sigma^{R}) \bullet G_0^{K} \bullet (1 + \Sigma^{A} \bullet G^{A}) + G^{R} \bullet \Sigma^{K} \bullet G^{A} \, ,
\end{align}
where the bullet $\bullet$ denotes contractions over all indices and variables except the Keldysh indices.


:::{dropdown} Explicit derivation
To derive these equations, we start from the general Dyson equation written explicitly in Keldysh space,
\begin{align}
    \begin{pmatrix}
        0 & G^{A} \\
        G^{R} & G^{K}
    \end{pmatrix} &=
    \begin{pmatrix}
        0 & G_0^{A} \\
        G_0^{R} & G_0^{K}
    \end{pmatrix} +
    \begin{pmatrix}
        0 & G_0^{A} \\
        G_0^{R} & G_0^{K}
    \end{pmatrix} \bullet
    \begin{pmatrix}
        \Sigma^{K} & \Sigma^{R} \\
        \Sigma^{A} & 0
    \end{pmatrix} \bullet
    \begin{pmatrix}
        0 & G^{A} \\
        G^{R} & G^{K}
    \end{pmatrix} \\
    &= \begin{pmatrix}
        0 & G_0^{A} \\
        G_0^{R} & G_0^{K}
    \end{pmatrix} + 
    \begin{pmatrix}
        0 & G_0^{A} \bullet \Sigma^{A} \bullet G^{A} \\
        G_0^{R} \bullet \Sigma^{R} \bullet G^{R} & (G_0^{R} \bullet \Sigma^{K} + G_0^{K} \bullet \Sigma^{A})  \bullet G^{A} + G_0^{R} \bullet \Sigma^{R} \bullet G^{K}
    \end{pmatrix} \, .
\end{align}
We directly obtain the two independent Dyson equations for the retarded and advanced components,
\begin{align}
    G^{R} &= G_0^{R} + G_0^{R} \bullet \Sigma^{R} \bullet G^{R} \, , \\
    G^{A} &= G_0^{A} + G_0^{A} \bullet \Sigma^{A} \bullet G^{A} \, ,
\end{align}
as well as the equation for the Keldysh component,
\begin{align}
    G^{K} &= G_0^{K} + G_0^{R} \bullet \Sigma^{K} \bullet G^{A} + G_0^{K} \bullet \Sigma^{A} \bullet G^{A} + G_0^{R} \bullet \Sigma^{R} \bullet G^{K} \, .
\end{align}
To solve the last equation for $G^K$, we first rewrite it as
\begin{align}
    (1 - G_0^{R} \bullet \Sigma^{R}) \bullet G^{K} &= G_0^{K} \bullet (1 + \Sigma^{A} \bullet G^{A}) + G_0^{R} \bullet \Sigma^{K} \bullet G^{A} \, .
\end{align}
Next, we observe that we can utilize the Dyson equation for $G^R$ (twice) to write
\begin{align}
    (1 - G_0^{R} \bullet \Sigma^{R})^{-1} &= G^R \bullet (G^{R})^{-1} (1 - G_0^{R} \bullet \Sigma^{R})^{-1} \\
    &= G^R \bullet (G^R - G_0^R \bullet \Sigma^R \bullet G^R)^{-1} \\
    &= \boxed{G^R \bullet (G_0^R)^{-1}} \\
    &= G^R \bullet [(G^R)^{-1} + \Sigma^R] = \boxed{1 + G^R \bullet \Sigma^R} \, .
\end{align}
Hence, we obtain for the Keldysh component
\begin{align}
    G^{K} &= \underbrace{(1 - G_0^{R} \bullet \Sigma^{R})^{-1}}_{= 1 + G^R \bullet \Sigma^R} \bullet G_0^{K} \bullet (1 + \Sigma^{A} \bullet G^{A}) + \underbrace{(1 - G_0^{R} \bullet \Sigma^{R})^{-1}}_{= G^R \bullet (G_0^R)^{-1}} \bullet G_0^{R} \bullet \Sigma^{K} \bullet G^{A} \\
    &= (1 + G^{R} \bullet \Sigma^{R}) \bullet G_0^{K} \bullet (1 + \Sigma^{A} \bullet G^{A}) + G^{R} \bullet \Sigma^{K} \bullet G^{A} \, . \ \checkmark 
\end{align}
:::

In practice, one will calculate all Keldysh components of $\Sigma$, evaluate the Dyson equations for the retarded and advanced components first (usually in the more practical form $(G^{R/A})^{-1} = (G_0^{R/A})^{-1} - \Sigma^{R/A}$, and finally evaluate the third equation to obtain $G^K$.

:::{note}
Often, the Keldysh component of the bare propagator is zero, $G_0^K = 0$, which is, e.g., the case for the Hubbard model (strictly speaking, it is a purely regularizing term $\sim i0^+$, which can be omitted in the presence of a Keldysh component of the self-energy). In this case, the Dyson equation for the Keldysh component simplifies to
\begin{align}
    G^{K} = G^{R} \bullet \Sigma^{K} \bullet G^{A} \, .
\end{align}
:::

:::{danger} To do
- Discuss fluctuation-dissipation theorem in equilibrium.
:::

### Four-point vertex

The Keldysh rotation for the four-point vertex is defined as
\begin{align}
    F^{k_1 k_2 k_3 k_4} = D^{k_1 c_1} D^{k_3 c_3} F^{c_1 c_2 c_3 c_4} (D^{-1})^{c_2 k_2} (D^{-1})^{c_4 k_4} \, .
\end{align}
This leads to a $2^4=16$-component object in Keldysh space. As for the self-energy, the component that vanishes identically due to causality is the one where all Keldysh indices are $2$,
\begin{align}
    F^{2222} = 0 \, .
\end{align} 

For an *instantaneous* bare interaction (i.e., local in time), such as, e.g.,  the Hubbard interaction, the bare interaction strongly simplifies in Keldysh space, taking the form
\begin{align}
    F_0^{k_1 k_2 k_3 k_4} =
    \begin{cases}
        F_0 / 2 & \text{if } k_1 + k_2 + k_3 + k_4 \text{ odd} \\
        0 & \text{otherwise}\, .
    \end{cases}
\end{align}

:::{dropdown} Explicit calculation

For an instantaneous interaction, we have in contour space that
\begin{align}
    F_0^{c_1 c_2 c_3 c_4} = -c_1 \delta_{c_1=c_2=c_3=c_4} F_0 \, ,
\end{align}
where $F_0$ encodes all other dependencies (e.g., time, momentum, spin, ...). Performing the Keldysh rotation and using that $D^{-1} = D^T$, we find
\begin{align}
    F_0^{k_1 k_2 k_3 k_4} &= D^{k_1 c_1} D^{k_3 c_3} (-c_1 \delta_{c_1=c_2=c_3=c_4} F_0) (D^{-1})^{c_2 k_2} (D^{-1})^{c_4 k_4} \\
    &= - F_0 D^{k_1 c_1} D^{k_3 c_3} \ c \ (D^{-1})^{c_2 k_2} (D^{-1})^{c_4 k_4} \\
    &= - F_0 \left[ D^{k_1 | -} D^{k_3 | -} (-1) (D^{-1})^{- | k_2} (D^{-1})^{- | k_4} + D^{k_1 | +} D^{k_3 | +} (D^{-1})^{+ | k_2} (D^{-1})^{+ | k_4} \right] \\
    &= F_0 \left[ D^{k_1 | -} D^{k_3 | -} D^{k_2 | -} D^{k_4 | -} -  D^{k_1 | +} D^{k_3 | +} D^{k_2 | +} D^{k_4 | +}\right]\, .
\end{align}
Now, inserting the elements of the transformation matrix $D$,
\begin{align}
    D^{k | -} &= \frac{1}{\sqrt{2}}\, ; & & &
    D^{k | +} &= \frac{1}{\sqrt{2}} (-1)^{k} \, ,
\end{align}
we find
\begin{align}
    F_0^{k_1 k_2 k_3 k_4} &= \frac{F_0}{4} \left[ 1 - (-1)^{k_1 + k_2 + k_3 + k_4} \right] \\
    &=
    \begin{cases}
        F_0 / 2 & \text{if } k_1 + k_2 + k_3 + k_4 \text{ odd} \\
        0 & \text{otherwise}\, .
    \end{cases}
\end{align}
:::