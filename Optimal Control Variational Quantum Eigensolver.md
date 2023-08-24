
## Finding the lowest energy state of a given Hamiltonian (eg. chemistry problems)

In VQE the usual control loop is the following
 1. Prepare initial state $|\psi_0\rangle$, classical parameters (angles) $\vec \theta_i$ 
 2. Run quantum simulation -> $|\psi_{F,i}\rangle = U(\vec \theta_i) |\psi_0\rangle$ 
 3. Measure energy $E(\vec \theta_i) = \text{Tr} [H\ \rho_{F,i}]$   
 4. Classical optimiser computes $\vec\theta_i \rightarrow \vec\theta_{i+1}$ based on $E(\vec\theta_i)$ 
 5. Return to step 2 if $E(\vec\theta_i)$ not satisfactory

## Optimal control

Mid-circuit measurements could allow for (dynamical?) error correction. Soft (incomplete) measurements could extract some information from the system and perhaps obtain advantage. 

## Pulse based VQE

 - Analog single qubit pulses are executed continuously throughout the evolution 
 - Short entanglement-generating pulses happen globally for all atoms at predefined instants 
 
![[Pasted image 20230814174554.png]]

If the global entanglement pulses are instantaneous, then the process can be seen as
![[Pasted image 20230814175059.png]]

The entanglement pulses are limited by the topology of the lattice -> interactions only between nearest neighbours.
The single atom pulses can also encode [[Qubit state transport#Atom transport via tweezers|transport via tweezers]], essentially changing the lattice through the process.
 - It is hard to define the transport paths and the 'lattices-at-entanglement' in a general way.
 - Arbitrary transport might not be viable/applicable in a near term system. Need to assume limitations on the transport options.

## Mid-circuit measurement for VQE
![[Pasted image 20230814175627.png]]

The main system ($|\psi_i\rangle$) weakly interacts with ancilla qubits through a $C-V(\vec\lambda)$ operation as a way to get some insight of the state of the system. The ancilla are measured at each 'observation' step, which naturally introduces noise into the system. The result of the observation step is fed back as a control parameter down the line, hopefully gaining some coherence back (think measurement based QC). This chain of operations has a similar structure to [[Recurrent systems#Recurrent neural networks|Recurrent Neural Networks]]. See also [[@barryQuantumPartiallyObservable2014]] and [[Measurement based VQE - review]].

This is another way of looking at the circuit architecture
![[Pasted image 20230815130541.png]]
$U(\vec \theta)$ and $W(\vec \alpha)$ are parameterised ansatze for the VQE, which may include quantum error correction codes. The $W$ circuit may take as long as the measurement $t_{meas}$ + $t_{class}$ classical computation times. The output of the classical computation $f(x)$ is fed back into the $U(\vec\theta)$ ansatze. This could be  a way to correct quantum errors (quantum error correction QEC) or a way to improve the convergence speed of the VQE by adapting the $\vec\theta$ parameters mid execution.  ^cc4605

See [[Recurrent systems]] and [[Quantum Error Correction]] for more ideas of control loops and dynamical quantum-classical methods.
 
For application in VQE's, it might be useful to look at [[Mid-circuit energy estimation]].

This concept is explored with better detail in [[Mid-circuit measurement]].

## Hamiltonian evolution ansatze

If $U(\vec\theta)$ is of the form $$ U(\vec \theta)=\exp\left\{-i \vec\theta\cdot\vec H\right\}$$ i.e. is an Hamiltonian evolution, then $$ U(\vec\theta+\Delta\vec\theta) \simeq U(\vec\theta)\ U(\Delta \vec\theta) $$
if $[\theta_i\, H_i, \theta_j\,H_j]\sim 0$ (intuitively, $\Delta\vec\theta$ has to have a similar direction to $\vec\theta$).
In a typical VQE process, the iterations start like
$|\varphi_0\rangle=|0\rangle$ 
$|\varphi_1\rangle = U(\vec\theta_1) |\varphi_0\rangle$
$|\varphi_2\rangle=U(\vec\theta_2)|\varphi_0\rangle$ 
$\cdots$
We can write
$|\varphi_2\rangle=U(\vec\theta_2)\, U^\dagger(\vec\theta_1)|\varphi_1\rangle$ 
where $\vec\theta_2 = \vec\theta_1 +\Delta\vec\theta$, and thus $U(\vec\theta_2)\simeq U(\Delta\vec\theta)\,U(\vec\theta_1)$. Then
$$|\varphi_2\rangle \simeq U(\Delta\vec\theta) | \varphi_1\rangle $$
meaning that we can approximately take a small evolution step from the previous iteration, as long as $\Delta\vec \theta$ doesn't change direction considerably. This decomposition is advantageous if $U(\vec\theta_1)$ is expensive and $U(\Delta \vec\theta)$ is cheap.



