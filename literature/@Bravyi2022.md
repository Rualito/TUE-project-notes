---
title: Constant-cost implementations of clifford operations and multiply-controlled gates using global interactions
authors: Sergey Bravyi, Dmitri Maslov, Yunseong Nam
year: 2022
citekey: Bravyi2022
10.1103/PhysRevLett.129.230501
---

We consider quantum circuits composed of single-qubit operations and global entangling gates generated by Ising-type Hamiltonians. It is shown that such circuits can implement a large class of unitary operators commonly used in quantum algorithms at a very low cost-using a constant or effectively constant number of global entangling gates. Specifically, we report constant-cost implementations of Clifford operations with and without ancillae, constant-cost implementation of the multiply-controlled gates with linearly many ancillae, and an Oðlog Ã ðnÞÞ cost implementation of the n-controlled single-target gates using logarithmically many ancillae. This shows a significant asymptotic advantage of circuits enabled by the global entangling gates. Executing a quantum computer program requires its compilation to native gates directly supported by the controlling apparatus. While most of the existing quantum computing hardware supports arbitrary single-qubit gates as their native physical-level instruction, the choice of entangling multiqubit operations may vary strongly across different platforms. Here we focus on leveraging parallel global instructions available in some quantum computer architectures [1-3]. Such global operations draw their power from the ability to apply a layer of pairwise commuting 2-qubit gates simultaneously. A notable example is the Molmer-Sorensen gate available in the trapped-ion architecture [2,4] that evolves a system of qubits under the Ising-type Hamiltonian. In this Letter, we report a streamlined implementation of two common quantum computing subroutines enabled by global entangling gates: elements of the Clifford group and multiply-controlled gates. Clifford operations play a central role in quantum error correction, certain simulation algorithms [5], and a variety of applications based on pseudorandom unitary operators [6-8]. Multiply-controlled gates are ubiquitous in applications that rely on arithmetic circuits or the quantum singular value transformation [9,10]. We consider computational primitives that implement a selectable set of commuting two-body Ising interactions in one go, which we call global tunable gates. We furthermore treat single-qubit gates as a free resource, which is justified since the implementation of entangling operators on the physical level tends to be more difficult and error prone compared with the single-qubit gates. Such a selection of the costing metric implies that the particular nature of the Ising interaction (e.g., XX; YY; ZZ) used is irrelevant-indeed, the results hold uniformly for all possible choices of the interaction since the changes between them are accomplished by the single-qubit gates (basis change) and can be merged into the single-qubit gate layers. For the sake of simplicity of mathematical expressions , we chose to work with the CZ a interaction defined as CZ a ¼ e iπaj11ih11j. Here a ∈ ½0; 1 is a tunable parameter. In other words, CZ 0 is equivalent to the identity, whereas CZ 1 ¼ CZ is single-qubit equivalent to the CNOT gate. We define an n-qubit global tunable (GT) gate as a diagonal unitary operator Y 1≤i¡j≤n CZ aði;jÞ i;j ; where i and j indicate pairs of qubits acted upon by each CZ a gate, and we allow the parameter a ¼ aði; jÞ to be tuned individually for each pair of qubits i and j. We assume all-to-all qubit connectivity. Multiple versions of GT gates have been experimentally demonstrated [1,2,11,12]. In particular, Ref. [2] showed that the pulse complexity required for a GT gate is not much more than that required for a single 2-qubit gate, i.e., 3n − 1 degrees of freedom used for a GT instruction and 2n þ 1 for a 2-qubit gate, for an n-qubit quantum computer. This is understood by considering the pulse design space, where some number of degrees of freedom must first be spent to decouple the computational states from the mutually shared information bus at the end of the entangling operation (2n) and then using additional degrees of freedom to induce the desired degree of entanglement between qubit pairs of PHYSICAL REVIEW LETTERS 129, 230501 (2022)
