---
title: Quantum filter diagonalization: Quantum eigendecomposition without full quantum phase estimation
authors: Robert M. Parrish, Peter L. McMahon
year: 2019
citekey: Parrish2019

---

We develop a quantum filter diagonalization method (QFD) that lies somewhere between the variational quantum eigensolver (VQE) and the phase estimation algorithm (PEA) in terms of required quantum circuit resources and conceptual simplicity. QFD uses a set of of time-propagated guess states as a variational basis for approximate diagonalization of a sparse Pauli Hamiltonian. The variational coefficients of the basis functions are determined by the Rayleigh-Ritz procedure by classically solving a generalized eigenvalue problem in the space of time-propagated guess states. The matrix elements of the subspace Hamiltonian and subspace metric matrix are each determined in quantum circuits by a one-ancilla extended swap test, i.e., statistical convergence of a one-ancilla PEA circuit. These matrix elements can be determined by many parallel quantum circuit evaluations, and the final Ritz estimates for the eigenvectors can conceptually be prepared as a linear combination over separate quantum state preparation circuits. The QFD method naturally provides for the computation of ground-state, excited-state, and transition expectation values. We numerically demonstrate the potential of the method by classical simulations of the QFD algorithm for an N=8 octamer of BChl-a chromophores represented by an 8-qubit ab initio exciton model (AIEM) Hamiltonian. Using only a handful of time-displacement points and a coarse, variational Trotter expansion of the time propagation operators, the QFD method recovers an accurate prediction of the absorption spectrum.

