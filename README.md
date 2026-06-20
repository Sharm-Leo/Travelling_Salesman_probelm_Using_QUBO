# Travelling Salesman Problem (TSP) Using QUBO

This project explores solving the **Travelling Salesman Problem (TSP)** using a **QUBO (Quadratic Unconstrained Binary Optimization)** formulation with Qiskit.

The goal was not only to find the optimal route but also to understand the practical challenges of mapping combinatorial optimization problems onto quantum computing frameworks.

---

## Overview

I started from scratch and followed the complete optimization workflow:

- Defined the objective function (**minimize total travel distance**)
- Added problem constraints:
  - Each city must be visited exactly once
  - Each tour position must contain exactly one city
- Converted the constrained optimization problem into a **QUBO formulation**
- Tested the model using both classical and quantum approaches

---

## Results

### Classical Solver

The QUBO formulation was successfully solved using a classical optimizer.

✅ Successfully found valid solutions

### Quantum Solver

When attempting to run the problem on quantum backends, several practical limitations appeared:

❌ Limited cloud credits  
❌ Hardware constraints  
❌ Qubit availability and connectivity challenges  
❌ Scalability issues as problem size increased

---

## Understanding the Scaling Challenge

For a TSP with **n cities**:

### Number of Binary Variables

Each city can appear in each tour position.

\[
\text{Variables} = n^2
\]

Thus:

| Cities (n) | Binary Variables |
|------------|------------------|
| 4 | 16 |
| 5 | 25 |
| 6 | 36 |

In many quantum formulations, these binary variables correspond directly to qubits (subject to hardware embedding requirements).

---

## State Space Explosion

The real challenge appears when simulating quantum systems.

A simulator must represent:

\[
2^n
\]

possible quantum states for **n qubits**.

| Qubits | State Space |
|---------|------------|
| 16 | 65,536 |
| 25 | 33,554,432 |
| 36 | 68,719,476,736 |

As the number of qubits increases, memory and computation requirements grow exponentially.

This makes both simulation and execution increasingly impractical for larger TSP instances.

---

## Key Learnings

### What Went Well

- Built the TSP model from first principles
- Gained a clear understanding of QUBO formulations
- Successfully implemented and solved the problem using classical optimization
- Learned how optimization problems are mapped to quantum computing frameworks

### Main Takeaway

While quantum optimization is promising, current hardware and simulation limitations make scaling difficult even for relatively small TSP instances.

The experience highlighted an important reality of quantum computing:

> The challenge is often not formulating the problem—it is executing it efficiently on today's quantum hardware.

---

## Technologies Used

- Python
- Qiskit
- QUBO Formulation
- Classical Optimization Solvers
- Quantum Optimization Workflows

---

## Conclusion

This project served as a practical introduction to quantum optimization and QUBO modeling. Although large-scale quantum execution was not feasible, the process provided valuable insights into:

- Problem formulation
- Constraint encoding
- QUBO construction
- Quantum hardware limitations
- Exponential scaling challenges

Overall, it was an excellent exercise in understanding both the potential and the current limitations of quantum optimization.

💡 What didn’t:
- Couldn’t fully run on quantum backend (credits + scale limits)
- Simulation becomes too heavy very quickly
