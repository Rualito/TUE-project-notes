---
tags:
  - Hamiltonian
  - RydbergDynamics
---


Using the QPE mid-circuit measurement method, we want to implement some evolution unitary $U=\exp\{-i\, M\,t\}$, where $M$ is an information matrix that essentially extracts information out of the state and projects it accordingly.
$$M|\psi\rangle = m |\psi\rangle $$
In a digital circuit, how do we implement $U$ efficiently? 

The dynamics of Rydberg atoms follow a continuous-time Hamiltonian, which we can use as an ansatz. The Schrodinger's time-dependent equation is 
$$ i \frac{d}{dt} |\psi\rangle = H(t) |\psi\rangle $$
where $H$ takes the form
$$H(t) = \sum_{i,j} \frac{C_6}{R_{ij}^6}\, n_i\,n_j + \sum_i(\Omega_i(t) |1\rangle\langle r| + h.c) +  \Delta_i(t) n_i $$
$J_{ij}(t)$ is controlled by the atom lattice, while $\Omega(t)$ and $\Delta_i(t)$ by the laser parameters. 

The $\Omega_i(t)$ and $\Delta_i(t)$ act as an ansatz for the information Hamiltonian. 

Alternatively, a similar system that has similar dynamics is the Ising model. 
$$H(t)= \sum_{ij} J_{ij}\ Z_i Z_j \ +\ \sum_i \Omega_{i}(t)X_i + \Delta_i(t) Z_i  $$
where $J$ is fixed and $\Omega(t)$ and $\Delta(t)$ are tunable.



