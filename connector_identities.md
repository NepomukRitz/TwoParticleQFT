# Identity operators for the two-particle channel connectors

Demonstrating that the identity operators defined in the section on [two-particle channels](two-particle-channels.md) work as intended is straightforward but somewhat tedious. Here, we explicitly write out all indices for each channel to show that the definitions are correct.
\begin{align}
[A \circ \mathbb{1}^{\overline{ph}}]_{1234} &= A_{1256} \mathbb{1}^{\overline{ph}}_{6534} = A_{1256} \delta_{64} \delta_{53} = A_{1234} \\
[\mathbb{1}^{\overline{ph}} \circ A]_{1234} &= \mathbb{1}^{\overline{ph}}_{1256} A_{6534} = \delta_{16} \delta_{25} A_{6534} = A_{1234}  \\ \\ 
[A \circ \mathbb{1}^{pp}]_{1234} &= A_{1536} \mathbb{1}^{pp}_{6254} = A_{1536} \delta_{64} \delta_{25} = A_{1234} \\
[\mathbb{1}^{pp} \circ A]_{1234} &= \mathbb{1}^{pp}_{1536} A_{6254} = \delta_{61} \delta_{53} A_{6254} = A_{1234}  \\ \\
[A \circ \mathbb{1}^{ph}]_{1234} &= A_{5236} \mathbb{1}^{ph}_{1564} = A_{5236} \delta_{15} \delta_{64} = A_{1234} \\
[\mathbb{1}^{ph} \circ A]_{1234} &= \mathbb{1}^{ph}_{5236} A_{1564} = \delta_{52} \delta_{36} A_{1564} = A_{1234}  \, .
\end{align}