# Qiskit Experiments and Case Study

Arranged in source-file order: Experiments 2–9, Case Study 10, then the separate environment and simulator checks from `test.ipynb`. Each independently runnable code listing is kept separate. The notebook comments and authorship labels are retained where present.

## Experiment 2 — Statevectors and sampling (`exp02.ipynb`)

```python
#Experiment 2

from qiskit.quantum_info import Statevector
from numpy import sqrt

u = Statevector([1 / sqrt(2), 1 / sqrt(2)])
v = Statevector([(1 + 2.0j) / 3, -2 / 3])
# Normalized version of the source vector [1/3, 2/3].
w = Statevector([1 / sqrt(5), 2 / sqrt(5)])

print("State vectors u, v, and w have been defined.")
display(u.draw("latex"))
display(v.draw("text"))

from qiskit.visualization import plot_histogram

statistics = v.sample_counts(1000)
display(statistics)
plot_histogram(statistics)
```

**Correction:** the original `w = Statevector([1 / 3, 2 / 3])` was not normalized (its squared norm is `5/9`). It is normalized here while preserving the same amplitude ratio.

## Experiment 3 — Identity matrices (`exp03.ipynb`)

```python
#Experiment 3

from qiskit import QuantumCircuit
from qiskit.quantum_info import Operator

# Function to create identity matrix for n qubits.
def identity_matrix(n_qubits):
    if n_qubits < 0:
        raise ValueError("n_qubits must be non-negative")

    # Create a quantum circuit with n qubits.
    qc = QuantumCircuit(n_qubits)

    # Apply the identity gate to all qubits using the id() method.
    for i in range(n_qubits):
        qc.id(i)

    # Convert the quantum circuit to an operator (matrix).
    return Operator(qc).data


# Example: identity matrix for 1, 2, and 3 qubits.
identity_matrix_1q = identity_matrix(1)
identity_matrix_2q = identity_matrix(2)
identity_matrix_3q = identity_matrix(3)

print("Identity matrix for 1 qubit:")
print(identity_matrix_1q)
print("\nIdentity matrix for 2 qubits:")
print(identity_matrix_2q)
print("\nIdentity matrix for 3 qubits:")
print(identity_matrix_3q)
```

**Correction:** added a clear error for a negative qubit count; the circuit and matrix logic is otherwise unchanged.

## Experiment 4 — Pauli gates (`exp04.ipynb`)

### Pauli-X

```python
#Experiment 4

# Pauli-X Gate:
from qiskit import QuantumRegister, ClassicalRegister, QuantumCircuit

qreg = QuantumRegister(1, 'q')
creg = ClassicalRegister(1, 'c')
qc = QuantumCircuit(qreg, creg)

qc.x(qreg[0])
qc.measure(qreg[0], creg[0])

print(qc)
```

### Pauli-Y

```python
# Pauli-Y Gate:
from qiskit import QuantumRegister, ClassicalRegister, QuantumCircuit

qreg = QuantumRegister(1, 'q')
creg = ClassicalRegister(1, 'c')
qc = QuantumCircuit(qreg, creg)

qc.y(qreg[0])
qc.measure(qreg[0], creg[0])

print("Quantum circuit of Pauli-Y Gate:")
print(qc.draw())
```

### Pauli-Z

```python
# Pauli-Z Gate:
from qiskit import QuantumRegister, ClassicalRegister, QuantumCircuit

qreg = QuantumRegister(1, 'q')
creg = ClassicalRegister(1, 'c')
qc = QuantumCircuit(qreg, creg)

qc.z(qreg[0])
qc.measure(qreg[0], creg[0])

print("Quantum circuit of Pauli-Z gate:")
print(qc.draw())
```

## Experiment 5 — Hadamard gate (`exp05.ipynb`)

```python
#Experiment 5

from qiskit import QuantumCircuit

qc = QuantumCircuit(1, 1)
qc.h(0)
qc.measure(0, 0)

print("Circuit diagram:")
print(qc.draw())
```

## Experiment 6 — SWAP and CNOT gates (`exp06.ipynb`)

### SWAP

```python
#Experiment 6

# SWAP Gate
from qiskit import QuantumCircuit

qc = QuantumCircuit(2, 2)
qc.swap(0, 1)
qc.measure([0, 1], [0, 1])

print("Circuit diagram:")
print(qc.draw())
```

### CNOT

```python
# CNOT Gate
from qiskit import QuantumCircuit

qc = QuantumCircuit(2, 2)
qc.cx(0, 1)
qc.measure([0, 1], [0, 1])

print("Circuit diagram:")
print(qc.draw())
```

## Experiment 7 — Toffoli / CCX gate (`exp07.ipynb`)

```python
#Experiment 7

from qiskit import QuantumCircuit

qc = QuantumCircuit(3, 3)
qc.ccx(0, 1, 2)
qc.measure([0, 1, 2], [0, 1, 2])

print("Circuit diagram:")
print(qc.draw())
```

## Experiment 8 — Bell-state circuits (`exp08.ipynb`)

### Hadamard followed by CNOT

```python
#Experiment 8

from qiskit import QuantumCircuit

qc = QuantumCircuit(2, 2)
qc.h(0)
qc.cx(0, 1)
qc.measure([0, 1], [0, 1])

print("Circuit diagram:")
print(qc.draw())
```

### CNOT followed by Hadamard

```python
from qiskit import QuantumCircuit

qc = QuantumCircuit(2, 2)
qc.cx(0, 1)
qc.h(0)
qc.measure([0, 1], [0, 1])

print("Circuit diagram:")
print(qc.draw())
```

## Experiment 9 — CCX with both controls set (`exp09.ipynb`)

```python
#Experiment 9

from qiskit import QuantumCircuit

qc = QuantumCircuit(3, 3)
qc.x(0)
qc.x(1)
qc.ccx(0, 1, 2)
qc.measure([0, 1, 2], [0, 1, 2])

print("Circuit diagram:")
print(qc.draw())
```

## Case Study 10 — Run a Bell circuit on IBM Quantum hardware (`cs10.ipynb`)

The uploaded notebook contained an IBM Quantum API token in plain text. The credential is deliberately not reproduced here. Set the two environment variables locally before running the setup cell. The instance identifier is also kept out of this shared listing.

### Account setup (run once)

```python
import os
from qiskit_ibm_runtime import QiskitRuntimeService

QiskitRuntimeService.save_account(
    channel="ibm_quantum_platform",
    token=os.environ["QISKIT_IBM_TOKEN"],
    instance=os.environ["QISKIT_IBM_INSTANCE"],
    overwrite=True,
)
```

### Transpile and run the Bell circuit

```python
# pip install qiskit-ibm-runtime
from qiskit import QuantumCircuit
from qiskit.transpiler.preset_passmanagers import generate_preset_pass_manager
from qiskit_ibm_runtime import QiskitRuntimeService, SamplerV2 as Sampler
from qiskit.visualization import plot_histogram

service = QiskitRuntimeService()
backend = service.least_busy(operational=True, simulator=False)
print("Using backend:", backend.name)

# Bell-state circuit
qc = QuantumCircuit(2, 2)
qc.h(0)
qc.cx(0, 1)
qc.measure([0, 1], [0, 1])

# Transpile for the hardware
pm = generate_preset_pass_manager(optimization_level=1, backend=backend)
isa_circuit = pm.run(qc)

# Run with Sampler
sampler = Sampler(mode=backend)
job = sampler.run([isa_circuit], shots=1024)
print("Job ID:", job.job_id())

result = job.result()
counts = result[0].data.c.get_counts()  # 'c' is the classical register name.
print(counts)
plot_histogram(counts)
```

**Credential safety:** revoke or rotate the API token that was embedded in the uploaded notebook, then set the replacement in `QISKIT_IBM_TOKEN`. Set `QISKIT_IBM_INSTANCE` to the instance identifier in your own environment. Do not paste either value into a notebook or shared document.

## Environment and simulator checks (`test.ipynb`)

These are setup checks from the separate `test.ipynb`; they are not numbered experiments.

### Print installed package versions

```python
import sys
import qiskit
import qiskit_aer
import qiskit_ibm_runtime
import IPython
import ipykernel

print("Python version:", sys.version)
print("Python executable:", sys.executable)
print("Qiskit version:", qiskit.__version__)
print("Qiskit Aer version:", qiskit_aer.__version__)
print("Qiskit IBM Runtime version:", qiskit_ibm_runtime.__version__)
print("IPython version:", IPython.__version__)
print("IPykernel version:", ipykernel.__version__)
```

### Build a Bell circuit

```python
from qiskit import QuantumCircuit

qc = QuantumCircuit(2, 2)
qc.h(0)
qc.cx(0, 1)
qc.measure([0, 1], [0, 1])

print(qc)
```

### Simulate and count Bell-state measurements

```python
from qiskit_aer import AerSimulator

simulator = AerSimulator()
result = simulator.run(qc, shots=1024).result()
counts = result.get_counts()

print("Measurement results:")
print(counts)
```

### Draw the circuit

```python
qc.draw("mpl")
```

### Run and plot a Bell-state simulation

```python
from qiskit import QuantumCircuit
from qiskit_aer import AerSimulator
import matplotlib.pyplot as plt

qc = QuantumCircuit(2, 2)
qc.h(0)
qc.cx(0, 1)
qc.measure([0, 1], [0, 1])

print("Circuit:")
display(qc.draw("mpl"))

simulator = AerSimulator()
result = simulator.run(qc, shots=1000).result()
counts = result.get_counts()

print("\nResults:")
print(counts)

plt.bar(counts.keys(), counts.values())
plt.xlabel("Measurement")
plt.ylabel("Counts")
plt.title("Bell State Simulation")
plt.show()
```

### Draw a one-qubit Hadamard circuit

```python
from qiskit import QuantumCircuit

qc = QuantumCircuit(1)
qc.h(0)
qc.draw("mpl")
```

## Corrections and transcription notes

- The source files contained 10 notebooks and 19 code cells. They are organized above as 19 code listings: 1 each for Experiments 2, 3, 5, 7, and 9; 3 for Experiment 4; 2 each for Experiments 6 and 8; 2 for Case Study 10; and 5 grouped setup/simulator listings from `test.ipynb`.
- The uploaded notebooks are Qiskit experiments, so they are kept as a separate set rather than forced into the earlier Data Structures and Algorithms syllabus arrangement.
- `exp02.ipynb`: normalized the `w` statevector so it is a valid quantum state.
- `exp03.ipynb`: added validation for a negative qubit count.
- `cs10.ipynb`: removed the exposed API token and instance value, and changed account setup to read them from environment variables.
- Unused imports were removed from several experiments. No other unreadable code or characters were found.
- These snippets were transcribed and reviewed from the notebook source. They were not executed against a Qiskit installation or IBM Quantum account.

