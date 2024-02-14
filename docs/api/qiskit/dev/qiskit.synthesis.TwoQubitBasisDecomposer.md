---
title: TwoQubitBasisDecomposer
description: API reference for qiskit.synthesis.TwoQubitBasisDecomposer
in_page_toc_min_heading_level: 1
python_api_type: class
python_api_name: qiskit.synthesis.TwoQubitBasisDecomposer
---

# TwoQubitBasisDecomposer

<span id="qiskit.synthesis.TwoQubitBasisDecomposer" />

`qiskit.synthesis.TwoQubitBasisDecomposer(gate, basis_fidelity=1.0, euler_basis='U', pulse_optimize=None)`[GitHub](https://github.com/qiskit/qiskit/tree/stable/1.0/qiskit/synthesis/two_qubit/two_qubit_decompose.py "view source code")

Bases: [`object`](https://docs.python.org/3/library/functions.html#object "(in Python v3.12)")

A class for decomposing 2-qubit unitaries into minimal number of uses of a 2-qubit basis gate.

**Parameters**

*   **gate** ([*Gate*](qiskit.circuit.Gate "qiskit.circuit.Gate")) – Two-qubit gate to be used in the KAK decomposition.
*   **basis\_fidelity** ([*float*](https://docs.python.org/3/library/functions.html#float "(in Python v3.12)")) – Fidelity to be assumed for applications of KAK Gate. Default 1.0.
*   **euler\_basis** ([*str*](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.12)")) – Basis string to be provided to OneQubitEulerDecomposer for 1Q synthesis. Valid options are \[‘ZYZ’, ‘ZXZ’, ‘XYX’, ‘U’, ‘U3’, ‘U1X’, ‘PSX’, ‘ZSX’, ‘RR’].
*   **pulse\_optimize** (*None or* [*bool*](https://docs.python.org/3/library/functions.html#bool "(in Python v3.12)")) – If True, try to do decomposition which minimizes local unitaries in between entangling gates. This will raise an exception if an optimal decomposition is not implemented. Currently, only \[\{CX, SX, RZ}] is known. If False, don’t attempt optimization. If None, attempt optimization but don’t raise if unknown.

## Methods

### decomp0

<span id="qiskit.synthesis.TwoQubitBasisDecomposer.decomp0" />

`static decomp0(target)`

Decompose target \~Ud(x, y, z) with 0 uses of the basis gate. Result Ur has trace: $|Tr(Ur.Utarget^dag)| = 4|(cos(x)cos(y)cos(z)+ j sin(x)sin(y)sin(z)|$, which is optimal for all targets and bases

### decomp1

<span id="qiskit.synthesis.TwoQubitBasisDecomposer.decomp1" />

`decomp1(target)`

Decompose target \~Ud(x, y, z) with 1 uses of the basis gate \~Ud(a, b, c). Result Ur has trace: .. math:

```python
|Tr(Ur.Utarget^dag)| = 4|cos(x-a)cos(y-b)cos(z-c) + j sin(x-a)sin(y-b)sin(z-c)|
```

which is optimal for all targets and bases with z==0 or c==0

### decomp2\_supercontrolled

<span id="qiskit.synthesis.TwoQubitBasisDecomposer.decomp2_supercontrolled" />

`decomp2_supercontrolled(target)`

Decompose target \~Ud(x, y, z) with 2 uses of the basis gate.

For supercontrolled basis \~Ud(pi/4, b, 0), all b, result Ur has trace .. math:

```python
|Tr(Ur.Utarget^dag)| = 4cos(z)
```

which is the optimal approximation for basis of CNOT-class `~Ud(pi/4, 0, 0)` or DCNOT-class `~Ud(pi/4, pi/4, 0)` and any target. May be sub-optimal for b!=0 (e.g. there exists exact decomposition for any target using B `B~Ud(pi/4, pi/8, 0)`, but not this decomposition.) This is an exact decomposition for supercontrolled basis and target `~Ud(x, y, 0)`. No guarantees for non-supercontrolled basis.

### decomp3\_supercontrolled

<span id="qiskit.synthesis.TwoQubitBasisDecomposer.decomp3_supercontrolled" />

`decomp3_supercontrolled(target)`

Decompose target with 3 uses of the basis. This is an exact decomposition for supercontrolled basis \~Ud(pi/4, b, 0), all b, and any target. No guarantees for non-supercontrolled basis.

### num\_basis\_gates

<span id="qiskit.synthesis.TwoQubitBasisDecomposer.num_basis_gates" />

`num_basis_gates(unitary)`

Computes the number of basis gates needed in a decomposition of input unitary

### traces

<span id="qiskit.synthesis.TwoQubitBasisDecomposer.traces" />

`traces(target)`

Give the expected traces $|Tr(U \cdot Utarget^dag)|$ for different number of basis gates.
