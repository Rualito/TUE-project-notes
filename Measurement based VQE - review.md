[[@Ferguson]]
Proposal of a new approach based on the measurement-based model of quantum computation MBQC.

An entangled state is prepared and computation made by single-qubit measurements.

Universal quantum computing is limited by the number of qubits and gates that can be performed (size and depth), with MBQC is limited by the size of the entagled state one can generate.

Technique name: MB-VQE.
Use a taylored entangled state - custom state that allows the exploration of an appropriate corner of the system's Hilbert space.

circuit VQE's can be translated to MB-VQEs. This translation is advantageous for circuits containing a large fraction of Clifford gates.

MBQC uses graph states, which are stabilizer states of the operators $S_n$
$$ S_n=X_n\prod_kZ_k$$
where $k$ refers to the vertices connected to site $n$.

Output state is generated after measuring out auxiliary states. These auxiliary states are measured in either the eigenbasis of the Pauli operators or a parameterised basis (parameterised rotations before measurement). The rotated basis is $R(\theta)$
$$R(\theta)\equiv\{(|0\rangle\pm e^{i\theta} |1\rangle)/\sqrt{2}\}$$
To make the computation deterministic, adaptive measurements are required -> it applies $X$ and $Z$ gates to the output qubits depending on the measurement results (Pauli), or adapting $R(\theta)$ from earlier measurement outcomes [[@Raussendorf2003]]. 

An advantage of MBQC is the possibility to simultaneously perform all nonadaptive measurements at the beginning of the calculation -> the clifford part of the circuit with single and multi-qubit gates (see [[@Bravyi2022]])

