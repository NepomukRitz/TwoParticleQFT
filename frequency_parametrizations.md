# Frequency parametrizations

:::{note}
The following section also applies to the momentum dependence of one- and two-particle quantities. For concreteness and ease of notation, we focus on frequency parametrizations here. For momentum parametrizations, simply replace all frequency variables $\nu$, $\nu'$, and $\omega$ by momentum variables $\mathbf{k}$, $\mathbf{k}'$, and $\mathbf{q}$, respectively.
:::

In thermal equilibrium, energy conservation implies that all $n$-point functions only depend on $n-1$ frequencies independently. For example, the two-particle vertex depends on only three independent frequency arguments. There are (quite literally!) infinitely many ways to choose these three frequencies, and different choices are more or less convenient depending on the context. 

The first decision to make lies already in the definition of the Fourier transform from imaginary time to Matsubara frequency space: One can decide to either assign a positive sign to all four frequencies or to choose different signs for incoming and outgoing particles.

Here, we choose the first option. Starting with the two-point Green's function in imaginary time (and suppressing all further dependencies for the sake of clarity), we have
\begin{align}
    G(\nu_2, \nu_1) &= \int_0^\beta d\tau_2 d\tau_1 \, e^{i\nu_2 \tau_2} e^{i\nu_1 \tau_1} G(\tau_2, \tau_1)\, .
\end{align}
(Imaginary) time-translation invariance then implies that $G$ only depends on the difference $\tau_1 - \tau_2$, which in (Matsubara) frequency space translates to a delta function enforcing $\nu_2 + \nu_1 = 0$. Thus, we can write
\begin{align}
    G(\nu_2, \nu_1) &\equiv G(\nu_2) \delta(\nu_2 + \nu_1)\, .
\end{align}

:::{note}
The explicit form of the $\delta$-function in the expression above depends on the formalism used. In the finite-temperature Matsubara formalism, it is a Kronecker delta $\beta \delta_{\nu_2, -\nu_1}$, also carrying one factor of inverse temperature $\beta$ for proper normalization (remember that each Matsubara sum comes with a factor $1/\beta$). In the zero-temperature Matsubara formalism and in the real-frequency Keldysh formalism, it is a Dirac delta $2\pi \delta(\nu_2 + \nu_1)$, including a factor of $2\pi$.

Likewise, when we write down frequency integrations further below, we will denote them as $\int_\nu$ and deliberately leave open whether this represents a Matsubara sum or a real-frequency integral. In the finite temperature Matsubara formalism, this then corresponds to $\frac{1}{\beta} \sum_\nu$ while in the zero-temperature Matsubara formalism it corresponds to $\int \frac{d\nu}{2\pi}$. When the frequency integration is done as part of a loop or bubble contraction in the Keldysh formalism, the normalization factor will furthermore include a factor of $-i$, i.e., $\int_\nu = \int \frac{d\nu}{2\pi i}$.
:::

The Fourier transform of the two-particle vertex reads
\begin{align}
    F(\nu_1, \nu_2, \nu_3, \nu_4) = \int_0^\beta d\tau_1 d\tau_2 d\tau_3 d\tau_4 \, &e^{i\nu_1 \tau_1} e^{i\nu_2 \tau_2} e^{i\nu_3 \tau_3} e^{i\nu_4 \tau_4} F(\tau_1, \tau_2, \tau_3, \tau_4) \, ,
\end{align}
with energy conservation implying $\nu_1 + \nu_2 + \nu_3 + \nu_4 = 0$. Thus, we have $F(\nu_1, \nu_2, \nu_3, \nu_4) \sim \delta(\nu_1 + \nu_2 + \nu_3 + \nu_4)$ and three independent frequency arguments suffice to parametrize the vertex.

:::{note}
This choice for defining the Fourier transform is the common one used in the Vienna convention. In the Munich convention, one would instead define 
\begin{align}
    G(\nu_2, \nu_1) &= \int_0^\beta d\tau_2 d\tau_1 \, e^{i\nu_2 \tau_2} e^{-i\nu_1 \tau_1} G(\tau_2, \tau_1) \\
    F(\nu_1, \nu_2, \nu_3, \nu_4) &= \int_0^\beta d\tau_1 d\tau_2 d\tau_3 d\tau_4 \, e^{i\nu_1 \tau_1} e^{-i\nu_2 \tau_2} e^{i\nu_3 \tau_3} e^{-i\nu_4 \tau_4} F(\tau_1, \tau_2, \tau_3, \tau_4) \, .
\end{align}
Remember that the role of incoming and outgoing frequencies is interchanged between correlation functions and vertices. With this definition, energy conservation implies $\nu_1 = \nu_2$ for two-point functions and $\nu_1 + \nu_3 = \nu_2 + \nu_4$ for the two-particle vertex.

This difference in convention then propagates to all subsequent definitions of frequency parametrizations.
:::

The next choice to make is which three frequencies to use as independent variables. Here, it is common to choose linear combinations of the four original frequencies that reflect the physical processes occurring in the three different [two-particle channels](two-particle-channels.md) ($\overline{ph}$, $pp$, $ph$), meaning that two particles with energy $\nu$ and $\nu'$, respectively, scatter, thereby exchanging an energy transfer $\omega$. This process is different in the three channels, leading to different definitions of $\nu$, $\nu'$, and $\omega$ in each case. 

One natural choice for these channel-native frequency parametrizations (consistent with a large part of the Vienna community) is given by

\begin{align}
    \overline{ph}: \ \nu_1 &= -\nu &\ pp:\ \nu_1 &= -\nu &\ ph:\ \nu_1 &= -\nu'-\omega \\
    \nu_2 &= \nu + \omega &\ \nu_2 &= -\nu' - \omega &\ \nu_2 &= \nu + \omega \\
    \nu_3 &= -\nu' - \omega &\ \nu_3 &= \nu + \omega &\ \nu_3 &= -\nu \\
    \nu_4 &= \nu' &\ \nu_4 &= \nu' &\ \nu_4 &= \nu' \, .
\end{align}
The parametrizations are identical for the $\overline{ph}$ and $ph$ channels, up to the exchange of $\nu_1 \leftrightarrow \nu_3$, consistent with crossing symmetry.


This parametrization is illustrated in the following diagram:

:::{image} diagrams/frequency_parametrization.png
:height: 150px
:::

We can thus parametrize the vertex in each channel as
\begin{align}
    F(\nu_1, \nu_2, \nu_3, \nu_4) &\equiv F^{\overline{ph}}(\nu, \nu', \omega) = F^{\overline{ph}}(-\nu_1, \nu_4, \nu_1 + \nu_2) \delta(\nu_1 + \nu_2 + \nu_3 + \nu_4) \\
    &\equiv F^{pp}(\nu, \nu', \omega) = F^{pp}(-\nu_1, \nu_4, \nu_1 + \nu_3) \delta(\nu_1 + \nu_2 + \nu_3 + \nu_4) \\
    &\equiv F^{ph}(\nu, \nu', \omega) = F^{ph}(-\nu_3, \nu_4, \nu_3 + \nu_2) \delta(\nu_1 + \nu_2 + \nu_3 + \nu_4)\, .
\end{align}

:::{warning}
Beware that the superscript indicating the channel parametrization is often not written explicitly. Which channel parametrization is used must then be inferred from the context.
:::

:::{danger} To do
Make a note about symmetric frequency parametrizations.
:::
Another main benefit of these *channel-native* frequency parametrizations is that only two instead of all three frequencies enter the bubble $\chi_0$ when connecting two vertices parametrized in the respective channel. To see this, we define the frequency parametrization of the bubble from the section on [two-particle channels](two-particle-channels.md) as
\begin{align}
    [\chi_0]_{4321}(\nu_2, \nu_1) &= G_{41}(\nu_2) G_{23}(\nu_1) \, ,
\end{align}
where the indices in the subscripts now denote all dependencies other than frequency. In the three channels, we define
\begin{align}
    [\chi_0^{\overline{ph}}]_{4321}(\nu, \omega) &= [\chi_0]_{4321}(\nu, \nu + \omega) \\
    [\chi_0^{pp}]_{4321}(\nu, \omega) &= \frac{1}{2} [\chi_0]_{4321}(\nu, -\nu - \omega) \\
    [\chi_0^{ph}]_{4321}(\nu, \omega) &= \zeta [\chi_0]_{2341}(\nu, \nu + \omega)\, .
\end{align}

We furthermore define the filled connector symbol $\bullet$ in the same way as the connector $\circ$ in the section on [two-particle channels](two-particle-channels.md), but now denoting contractions across all dependencies *except* frequency. Then, we can write down the bubble contractions in each channel $r$ in a unified way as
\begin{align}
    [A \circ \chi_0^r \circ B](\nu, \nu', \omega) &= \int_{\nu''} A(\nu, \nu'', \omega) \bullet \chi_0^r(\nu'', \omega) \bullet B(\nu'', \nu', \omega) \, ,
\end{align}
where $A$ and $B$ are two generic four-point objects parametrized in the way native to channel $r$.

:::{dropdown} Explicit calculations
In the $\overline{ph}$ channel we have
\begin{align}
[A \circ \chi_0^{\overline{ph}} \circ B](\nu_1, \nu_2, \nu_3, \nu_4) &= [A \circ \chi_0^{\overline{ph}} \circ B](-\nu_1, \nu_4, \nu_1 + \nu_2) \delta(\nu_1 + \nu_2 + \nu_3 + \nu_4) \\
&= \int_{\substack{\nu_5,\nu_6 \\ \nu_7,\nu_8}} A(\nu_1, \nu_2, \nu_5, \nu_6) G(\nu_6, \nu_7) G(\nu_8, \nu_5) B(\nu_7, \nu_8, \nu_3, \nu_4) \\
&= \int_{\nu_6, \nu_8} A(\nu_1, \nu_2, -\nu_8, \nu_6) G(\nu_6) G(\nu_8) B(-\nu_6, \nu_8, \nu_3, \nu_4) \\
&= \int_{\nu_6, \nu_8} A(-\nu_1, \nu_6, \nu_1 + \nu_2) \delta(\nu_1 + \nu_2 - \nu_8 + \nu_6) G(\nu_6) G(\nu_8) B(\nu_6, \nu_4, \nu_8 - \nu_6) \delta(-\nu_6 + \nu_8 + \nu_3 + \nu_4) \\
&= \int_{\nu_6} A(-\nu_1, \nu_6, \nu_1 + \nu_2)  G(\nu_6) G(\nu_6 + \nu_1 + \nu_2) B(\nu_6, \nu_4, \nu_1 + \nu_2) \delta(\nu_1 + \nu_2 + \nu_3 + \nu_4)\, ,
\end{align}
where we used that $\int_{\nu_8} \delta(\nu_1 + \nu_2 - \nu_8 + \nu_6) \delta(-\nu_6 + \nu_8 + \nu_3 + \nu_4) =  \delta(\nu_1 + \nu_2 + \nu_3 + \nu_4)$, setting $\nu_8 = \nu_6 + \nu_1 + \nu_2$. Identifying $\nu = -\nu_1$, $\nu' = \nu_4$, and $\omega = \nu_1 + \nu_2$ in the $\overline{ph}$ channel and renaming $\nu_6 \rightarrow \nu''$ we thus find
\begin{align}
[A \circ \chi_0^{\overline{ph}} \circ B](\nu, \nu', \omega) &= \int_{\nu''} A(\nu, \nu'', \omega) G(\nu'') G(\nu'' + \omega) B(\nu'', \nu', \omega) \, .
\end{align}

In the $pp$ channel, we have
\begin{align}
[A \circ \chi_0^{pp} \circ B](\nu_1, \nu_2, \nu_3, \nu_4) &= [A \circ \chi_0^{pp} \circ B](-\nu_1, \nu_4, \nu_1 + \nu_3) \delta(\nu_1 + \nu_2 + \nu_3 + \nu_4) \\
&= \frac{1}{2} \int_{\substack{\nu_5,\nu_6 \\ \nu_7,\nu_8}} A(\nu_1, \nu_5, \nu_3, \nu_6) G(\nu_6, \nu_7) G(\nu_5, \nu_8) B(\nu_7, \nu_2, \nu_8, \nu_4) \\
&= \frac{1}{2} \int_{\nu_5,\nu_6} A(\nu_1, \nu_5, \nu_3, \nu_6) G(\nu_6) G(\nu_5) B(-\nu_6, \nu_2, -\nu_5, \nu_4) \\
&= \frac{1}{2} \int_{\nu_5,\nu_6} A(-\nu_1, \nu_6, \nu_1 + \nu_3)\delta(\nu_1 + \nu_5 + \nu_3 + \nu_6) G(\nu_6) G(\nu_5) B(\nu_6, \nu_4, -\nu_5 - \nu_6) \delta(-\nu_6 + \nu_2 - \nu_5 + \nu_4) \\
&= \frac{1}{2} \int_{\nu_6} A(-\nu_1, \nu_6, \nu_1 + \nu_3) G(\nu_6) G(-\nu_6 - \nu_1 - \nu_3) B(\nu_6, \nu_4, \nu_1 + \nu_3) \delta(\nu_1 + \nu_2 + \nu_3 + \nu_4) \, ,
\end{align}
where we used that $\int_{\nu_5} \delta(\nu_1 + \nu_5 + \nu_3 + \nu_6) \delta(-\nu_6 + \nu_2 - \nu_5 + \nu_4) =  \delta(\nu_1 + \nu_2 + \nu_3 + \nu_4)$, setting $\nu_5 = -\nu_6 - \nu_1 - \nu_3$. Identifying $\nu = -\nu_1$, $\nu' = \nu_4$, and $\omega = \nu_1 + \nu_3$ in the $pp$ channel and renaming $\nu_6 \rightarrow \nu''$ we thus find
\begin{align}
[A \circ \chi_0^{pp} \circ B](\nu, \nu', \omega) &= \frac{1}{2} \int_{\nu''} A(\nu, \nu'', \omega) G(\nu'') G(-\nu'' - \omega) B(\nu'', \nu', \omega) \, .
\end{align}

In the $ph$ channel, we have
\begin{align}
[A \circ \chi_0^{ph} \circ B](\nu_1, \nu_2, \nu_3, \nu_4) &= [A \circ \chi_0^{ph} \circ B](-\nu_3, \nu_4, \nu_3 + \nu_2) \delta(\nu_1 + \nu_2 + \nu_3 + \nu_4) \\
&= \zeta \int_{\substack{\nu_5,\nu_6 \\ \nu_7,\nu_8}} A(\nu_5, \nu_2, \nu_3, \nu_6) G(\nu_6, \nu_7) G(\nu_8, \nu_5) B(\nu_1, \nu_8, \nu_7, \nu_4) \\
&= \zeta \int_{\nu_6,\nu_8} A(-\nu_8, \nu_2, \nu_3, \nu_6) G(\nu_6) G(\nu_8) B(\nu_1, \nu_8, -\nu_6, \nu_4) \\ 
&= \zeta \int_{\nu_6,\nu_8} A(-\nu_3, \nu_6, \nu_2 + \nu_3) \delta(-\nu_8 + \nu_2 + \nu_3 + \nu_6) G(\nu_6) G(\nu_8) B(\nu_6, \nu_4, \nu_8 - \nu_6) \delta(\nu_1 + \nu_8 - \nu_6 + \nu_4) \\
&= \zeta \int_{\nu_6} A(-\nu_3, \nu_6, \nu_2 + \nu_3) G(\nu_6) G(\nu_6 + \nu_2 + \nu_3) B(\nu_6, \nu_4, \nu_2 + \nu_3) \delta(\nu_1 + \nu_2 + \nu_3 + \nu_4) \, ,
\end{align}
where we used that $\int_{\nu_8} \delta(-\nu_8 + \nu_2 + \nu_3 + \nu_6) \delta(\nu_1 + \nu_8 - \nu_6 + \nu_4) =  \delta(\nu_1 + \nu_2 + \nu_3 + \nu_4)$, setting $\nu_8 = \nu_6 + \nu_2 + \nu_3$. Identifying $\nu = -\nu_3$, $\nu' = \nu_4$, and $\omega = \nu_2 + \nu_3$ in the $ph$ channel and renaming $\nu_6 \rightarrow \nu''$ we thus find
\begin{align}
[A \circ \chi_0^{ph} \circ B](\nu, \nu', \omega) &= \zeta \int_{\nu''} A(\nu, \nu'', \omega) G(\nu'') G(\nu'' + \omega) B(\nu'', \nu', \omega) \, .
\end{align}

These are indeed the correct expressions for the bubble contractions in the respective channel-native frequency parametrizations. $\checkmark$
:::
