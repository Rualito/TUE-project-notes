
This is a bit more abstract in definition. In general, you have a unitary circuit $U$ defined as a sequence of implementable gates on the platform. Usually this is done with some two-qubit gate (such as CNOT) and single qubit gates.


## Circuit transpilation and error correction
There are a few things to consider. 
 * Rydberg atoms are capable of multi-atom interactions. Transpilation to multi-qubit gates might be more efficient than sequences of two-qubit gates.
 * Atom rearrangement allows for improved connectivity of the system, leading to smaller depth.
 * Mid-circuit measurements followed by fast classical computations allow for quantum error correction codes.






