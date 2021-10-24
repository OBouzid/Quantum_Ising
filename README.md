# Quantum_Ising
Quiskit implementation of a Metropolis algorithm applied to an Ising chain. We generalize an existing model and propose a way to perform a genuine quantum simulation. 
Developped for [*Hackathon Cuántico Madrid*][gitQH] (22-24 Oct 2021).

## Overview

The Metropolis(-Hastings) algorithm is a method to generate samples of certain distributions, with a wide range of applications in statistical problems. It makes an intense use of random numbers to generate some probabilities inherent to the algorithm, but some approaches particularly suffer from the absence of an efficient method to handle them [[1][1], [2][2]]. That is why some proposals have explored how the use of quantum computing may be useful, focusing on exploiting its probabilistic nature to introduce the probabilistic features of the method in an alternative manner [[2][2]]. 

Specifically, we follow this reference [[2][2]] to analyse the statistical properties of a 1D Ising chain, a typical model to study magnetism in materials. This quantum implementation of the Metropolis algorithm encodes the probabilities related to the physical parameters of the simulation by employing superpositions of states, and it is devised to lie into the applicability range of quantum computers with a small number of qubits (~10). The method consists in associating one qubit for a site of the Ising chain in a Metropolis step, and operating it with the help of ancillary qubits to introduce the required probability relations and enable the computation. This procedure is then iterated as in a classical Metropolis algorithm.

The particular structure of the associated quantum circuit strongly depends on the Hamiltonian of the system, and the optimal choices for the ancillary qubits and for the sequence of gates are not trivial. In our project, we reproduce the circuit for an Ising chain without magnetic field (only interaction parameter \(J\) and temperature \(T\), and implement a new one that is capable of simulating the effect of a magnetic field \(h\), which is a key feature not only in the study of materials but also in the numerous applications of this model, such as in finance [[3][3]] or ecology [[4][4]], where the parameters \(h,J,T\) are mapped to the relevant variables in each situation. We further check whether our circuit provides the correct Metropolis probabilities by analising the statistics of measurements.

Finally, it must be noticed that even if this is a quantum implementation, the algorithm is still devised to produce a classical simulation. That is why we have been intended to explore if it could be possible to include further quantum features such as superposition and entanglement in the *physical* qubits (not the ancillary ones). There are different precedents [[5][5],[6][6]] that also address how to perform *genuine* quantum Metropolis sampling. In our approach, we remove the early measurement of the *physical* qubits and extend the Metropolis evolution, implicitly allowing the generation of entanglement between sites, until a measurement is performed after a given number of cycles. For this task, we make use of aditional storage qubits that permit the application of (quantum) Metropolis steps in each site while maintaining the global superposition


## Implementation


 
## Dependencies
This code makes use of the following libraries:
* Quiskit
* Numpy 
* Matplotlib 

[gitQH]: https://github.com/QuantumMadrid/HackathonCuanticoMadrid
[1]: https://doi.org/10.1016/s0003-4916(86)80006-9
[2]: https://arxiv.org/abs/quant-ph/0404143
[3]: https://doi.org/10.1088/1742-6596/1113/1/012009
[4]: https://doi.org/10.1098/rsif.2020.0571
[5]: https://arxiv.org/pdf/0911.3635.pdf
[6]: https://arxiv.org/pdf/1011.1468.pdf

## References

[[1]] https://doi.org/10.1016/s0003-4916(86)80006-9

[[2]] https://arxiv.org/abs/quant-ph/0404143

[[3]] https://doi.org/10.1088/1742-6596/1113/1/012009

[[4]] https://doi.org/10.1098/rsif.2020.0571

[[5]] https://arxiv.org/pdf/0911.3635.pdf

[[6]] https://arxiv.org/pdf/1011.1468.pdf
