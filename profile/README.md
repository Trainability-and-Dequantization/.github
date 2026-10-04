# Trainability and Dequantization

> **Can the geometric structure of a learning problem predict, before training, whether a structure-preserving quantum model of it will be trainable and resist dequantization?**

We study when quantum machine learning models are worth building. Two failure modes limit them:

- **Barren plateaus:** the training landscape becomes flat and gradients vanish exponentially with the number of qubits.
- **Dequantization:** a classical method reproduces the model's behaviour cheaply, so the quantum model offers no advantage.

Our approach is empirical and reproducible. We generate learning problems, extract their structure, build quantum circuits from that structure automatically, and record two kinds of numbers for every circuit:

- **Fingerprints**, computed from the circuit's description alone, before any training.
- **Measurements**, obtained by running the circuit.

A **predictor** then learns to recover the measurements from the fingerprints and is tested on problem families it has never seen.

## Project Organization

**Phase A: the dataset.** Every problem goes through the same pipeline:

```
problem → structure → encoding → move pool → twirling → circuit → comparison circuits → fingerprint → prediction → measurement → database
```

**Phase B: the predictor.** A statistical model maps fingerprints to trainability and simulability. It is validated by holding out whole problem families and compared with existing theoretical formulas.

## Stack

| Tool | Role |
| --- | --- |
| [PennyLane](https://pennylane.ai/) | Quantum circuits, Lie-algebra tooling, cross-checks of our own simulator |
| [NumPy](https://numpy.org/) | Linear algebra, statevector simulation, data generation |
| [PyTorch](https://pytorch.org/) | Automatic differentiation and optimisation for training runs and the predictor |
| [Pytest](https://docs.pytest.org/en/stable/) | Building automatic testing |
| [matplotlib](https://docs.pytest.org/en/stable/) | Generating graphs and figures |

## Timeline

| Date | Checkpoint | Decision |
| --- | --- | --- |
| 11 Oct 2026 | Setup done | — |
| 25 Oct 2026 | Specification accepted | Freeze the definitions |
| 15 Nov 2026 | Library release, tests green | Start the pilot |
| 22 Nov 2026 | Pilot review | Go, fix, or redesign the data harvest |
| 13 Dec 2026 | Dataset complete | Freeze the data |
| 3 Jan 2027 | Analysis done | Decide what the paper claims |
| 17 Jan 2027 | Preprint drafted, code and data released | — |

## Team

- Charbel Dargham 
- Júlia Santos 
- Kamaal
- Kauê Miziara
