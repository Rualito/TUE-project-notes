
(NOTE: assumed $2\pi$ terms in phases)

Consider that you prepare some state $|\psi\rangle$, and want to estimate its energy according to some Hamiltonian $H$. Quantum Phase Estimation (QPE) allows you to estimate the energy of the state up to arbitrary order.

$|\psi\rangle$ is an eigenstate of an unitary $U$, and the eigenvalue corresponds to a phase:  $U|\psi\rangle=e^{i\phi}|\psi\rangle$. QPE estimates $\phi$ in binary form in the process (check calculation)
$$\text{QPE}\ |0\rangle^{\otimes n}|\psi\rangle = e^{i\Phi}|\tilde\phi\rangle|\psi\rangle $$
where $\tilde\phi$ is the binary form of $\phi$ truncated to $n$ bits. and $\Phi=\phi\sum_{l=0}^n 2^l$ is the remainder of the phase ($\phi=\tilde\phi+2^{-n}\Phi$)

$U=\exp \{i\,H\,\theta\}$ and $H|\psi\rangle=\varepsilon|\psi\rangle$, then
$$ U|\psi\rangle = e^{i\varepsilon\theta} |\psi\rangle $$
Consider $$|\psi\rangle = \alpha_1|\psi_1\rangle + \alpha_2|\psi_2\rangle$$
where $U|\psi_i\rangle =e^{i\Phi_i}|\psi_i\rangle$. QPE will obtain the state 
$$\text{QPE} \ |\psi\rangle = \alpha_1 e^{i\Phi_1}|\tilde\phi_1\rangle|\psi_1\rangle + \alpha_2e^{i\Phi_2}|\tilde\phi_2\rangle|\psi_2\rangle$$
When measuring the phase values $|\tilde\phi_i\rangle$, one of the eigenstates $|\psi_i\rangle$ will be selected. In essence, this process projects a state into the eigenstates (\*) of a custom $H$.

(\*) It will project onto the eigenstate space that returns the same phase $\tilde\phi$. So, $|\psi_i\rangle$ might not be eigenstates of $H$. Still, it projects onto a eigenstate space which has similar energy values within $\varepsilon\pm\delta$, where $\delta\sim2^{-n}$.     

Upon measurement, the state will be a classical ensemble between the different eigenstates 
$$\sum_i|\tilde\phi_i\rangle\langle\tilde\phi_i|\ |\psi_i\rangle\langle\psi_i|$$ 

This idea could be used in a sequential measurement scheme as described in [[Sequential Measurement-based VQE]]


With this you could also project multiple eigenstate spaces onto each other, using distinct Hamiltonians. This is not easy to do classically, but can be done with parallel QPEs.


Also look at [[@Parrish2019]] for a similar concept