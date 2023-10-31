

## Initial idea

By using mid circuit measurements, we can extract some information about the state of the quantum system, and use it downstream to achieve the task more efficiently
![[Pasted image 20230817165711.png]]

One interesting way to interpret the extraction of information from a quantum system is through QPE. With it we project the state into the eigenstates of an information hamiltonian $H_I$, and from the readout we know which eigenstate was the system projected into. This formulation also allows for weak measurements when $H_I$ is close enough to the identity.

From this, there are a few questions
1. How to implement QPE in the NISQ era?
2. Which information Hamiltonians are useful for VQE?
3. What can we do with the extracted information?

## Typical application 

In VQE, one usually wants to find the ground state of some objective Hamiltonian $H_O$. It can be described, for instance, with a sum of Pauli strings
$$H_O = \sum_i^{L} c_i P_i $$
where $P_i \in \{I, X, Y, Z\}^{\otimes n}$

Since any Pauli string verifies the following $P_i^2=I$, and so represent an Hamiltonian with two energy levels. Then $H_O$ has $\min (2^L, 2^N)$ energy levels 

## QPE in the NISQ era
### QPE overview
Lets say you have an unitary propagator $U=\exp \{ -i\, H_I\, \theta\}$, where 
$$H_I=\sum_i \varepsilon_i |\varepsilon_i\rangle\langle \varepsilon_i| $$
and some state to probe
$$|\psi\rangle = \alpha |\varepsilon_1\rangle + \beta |\varepsilon_2\rangle $$
Then QPE does the following
$$ QPE |0\rangle|\psi\rangle = \alpha e^{-i\Phi_1}|\overline {\theta\varepsilon_1}\rangle|\varepsilon_1\rangle + \beta e^{-i\Phi_2}|\overline {\theta\varepsilon_2}\rangle|\varepsilon_2\rangle  $$
where $\Phi_1$, $\Phi_2$ are some phases originating from the QPE evolution, and $|\overline{\theta \varepsilon_i}\rangle$ are the states that are read out. 

Actually, depending on the size of the QPE, on the angle $\theta$, and on the degeneracy of $H_I$ the measurement process will not project into just one of the eigenstates, but into an eigenstate space of all of the eigenstates that would lead to that measurement result.
### Choosing an efficient $H_I$

In QPE, in order to measure $n$ bits of information out of the state, one requires the controlled propagation of $U^{2^n}$. If there are no assumptions about $H_I$ or its propagation, it will be exponential in time, which isn't pleasant for NISQ.

Let's say that $U_I=S\, D_I\, S^\dagger$, where $D_I$ is a diagonal operator with the eigenphases of $U_I$, and $S$ is a change of basis operator.  Thus
$$ U_I^{2^n} = S D_I^{2^n} S^\dagger  $$
If $D_I$ can be implemented with controlled-Z rotation operations (such as $C_kR_z(\phi)$), then, since they all commute between each other, we can use the fact that $$C_kR_z(\phi)^n=C_kR_z(n\phi)=C_kR_z(n\phi \mod 2\pi)$$
and have essentially a linear QPE circuit. With this process, the energy level structure of $H_I$ can be fine tuned with $D_I$. Each $C_kR_z(\phi)$ induces an energy level split on $H_I$. 

From this, there are a few ideas that come up
- Hamiltonian cloning: We could try to find an $H_I$ that mimics the level structure of $H_O$. This likely to be an hard task, as an exponential number of levels have to be matched. Thus it likely is much harder than just finding the ground state.
- Divide and conquer: It could be that it is enough to have an $H_I$ that is 'close enough' to $H_O$. Then, from each energy level we could act differently on the outcome of the projection, using some variational method. 

These ideas fall to the ground on the following realisation: it is easy to generate the eigenstates of $H_I$ using $S$, since 
$$ S|i\rangle = |\varepsilon_i\rangle $$
So, after projection, one of the eigenstates/spaces is generated at random. One could simply generate the desired superposition of eigenstates with a simple circuit before applying $S$. All of the QPE machinery is unnecessary if $H_I$ is constructed from a diagonalization. 

If one can implement the evolution of $H_O$ easily in the circuit (without resorting to diagonalization of course), then there may be interesting approaches to finding the groundstate by iteratively splitting the eigenspace. Although, in the end, it may not be NISQ friendly.  

