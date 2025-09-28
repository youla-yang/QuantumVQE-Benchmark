# Quantum VQE Benchmark Dataset

Quantum Circuit Parameter Initialization Database for VQE Energy Solutions and GNN-based Machine Learning

This database contains data from 380 VQE experiments conducted on quantum chemistry calculations involving molecules such as H2, LiH, and BeH2. The focus of this database is to record optimal quantum circuit parameters and the VQE-solved energy for each molecule. This data can be used for parameter initialization in future quantum optimization tasks and for training Graph Neural Networks (GNNs) to predict optimal quantum circuit parameters more efficiently.

Key Features

Molecule Type: Information about the molecule being studied:

H2 (Hydrogen molecule)

LiH (Lithium Hydride)

BeH2 (Beryllium Hydride)

Optimizers: The optimization algorithms used in the VQE process:

COBYLA (Constrained Optimization BY Linear Approximations): A commonly used gradient-free optimizer.

L-BFGS-B (Limited-memory Broyden-Fletcher-Goldfarb-Shanno with Box constraints): A quasi-Newton optimization algorithm that is efficient for larger problems with constraints.

VQE-Solved Energy: The energy obtained from solving the molecule's Hamiltonian using VQE, recorded for each experiment.

Quantum Circuit Parameters: The optimal quantum circuit parameters after the optimization process, stored as final_params and best_params.

Energy Values: Includes initial energy, final energy, and the best energy found during the optimization.

Optimization Process: Records details about the number of optimization steps and speedup achieved during the optimization process.

Seed: The random seed used in the optimization for reproducibility.

Additional Metadata: Other relevant details like molecule basis set, tapering, and the experimental timestamp.

Data Structure

The main table in the database, runs, includes the following columns:

id: Unique identifier for each run.

ts: Timestamp of the experiment.

molecule: The molecule used in the experiment (e.g., 'H2', 'LiH', 'BeH2').

basis: The basis set used for the calculations (e.g., 'STO-3G').

mapper: The qubit mapping strategy used (e.g., 'parity').

tapering: Whether tapering was used in the optimization.

reps: Number of repetitions for the experiment.

optimizer: The optimizer used in the VQE algorithm (e.g., 'COBYLA', 'L-BFGS-B').

seed: The random seed used for the experiment.

n_qubits: The number of qubits used in the simulation.

bond_length: The bond length for the molecule.

energy_init: The initial energy before optimization.

energy_final: The final energy after optimization.

energy_total: The total energy calculated (sum of energies or other relevant aggregation).

steps: Number of optimization steps taken.

de_init: The initial derivative of energy.

de_final: The final derivative of energy.

speedup: The speedup factor compared to a baseline.

note: Any additional remarks related to the run.

final_params: The final optimized parameters for the quantum circuit.

best_energy: The best energy obtained during the optimization.

best_params: The parameters associated with the best energy found.

vqe_energy: The energy solution obtained by the VQE method, specifically for each molecule. This is the key result of the VQE optimization process and is essential for validating the effectiveness of the quantum circuit parameters.

Purpose and Innovation

This database is designed to record both the optimal quantum circuit parameters and the VQE-solved energy for each molecule (H2, LiH, BeH2). The data can then be leveraged to initialize parameters for future quantum optimizations and to train machine learning models, particularly Graph Neural Networks (GNNs). These models can predict optimal quantum circuit parameters more efficiently, reducing the computational cost and improving the precision of quantum simulations.

Key Innovations:

Comprehensive Energy and Parameter Recording:

Unlike existing datasets, this database not only records quantum circuit parameters (final_params and best_params) but also stores the VQE-solved energy (vqe_energy) for each experiment. This allows for deeper analysis into how specific parameters affect energy convergence and the quality of the quantum circuit solutions.

Optimizing Quantum Circuit Initialization with GNN:

The database provides valuable data for training GNN models to predict the optimal quantum circuit parameters based on different experimental conditions (such as molecule type, optimizer, and energy). GNN models can use this data to learn how to initialize quantum circuits more effectively, speeding up the optimization process.

Reproducibility and Transparency:

Every experiment is documented with crucial information such as the random seed, optimization steps, and parameter values, ensuring the reproducibility of the results. This is essential for machine learning model training, where reproducibility is a key requirement.

Diverse Experiment Configurations:

The database includes a wide range of experiments (a total of 380 experiments) with different molecule types, optimizers (COBYLA, L-BFGS-B), and quantum circuit configurations. This diversity allows researchers to analyze how quantum circuit parameters influence energy solutions, providing insights into better initialization strategies for quantum optimization.

Applications

Training GNNs for Parameter Initialization:

By using this database, researchers can train GNN models to predict the best initial parameters for quantum circuit optimizations. GNNs can capture the relationships between different quantum circuit configurations and their optimized parameters, automating the initialization process for future VQE experiments.

Quantum Circuit Design Optimization:

The data stored in this database can be used to explore new quantum circuit designs by training machine learning models to predict optimal parameters based on different experimental conditions. This can help in designing more efficient quantum circuits for solving complex quantum chemistry problems.

Improving VQE Efficiency:

With accurate parameter initialization, the VQE algorithm can converge faster and more efficiently, which is crucial for scaling quantum chemistry simulations. This database provides the necessary data to optimize VQE and other quantum optimization algorithms.

How to Use

Accessing the Database:

The database can be accessed and queried to analyze the results of various quantum circuit optimizations. Researchers can extract data about different optimizers, molecule types, and parameters to explore the effects of various settings on VQE performance.

Integrating with Machine Learning Models:

The data, particularly the quantum circuit parameters (final_params and best_params) and the vqe_energy, can be used as input for machine learning models, such as GNNs, to predict optimal initialization parameters for future experiments.

Visualizing Optimization Results:

The data can be used to create visualizations that track the energy convergence over time, showing how different optimization methods and parameters affect the energy optimization process.

Conclusion

This Quantum Circuit Parameter Initialization Database offers valuable data for improving VQE optimization and initializing quantum circuits. By recording detailed quantum circuit parameters and the energy solutions obtained through VQE, it provides essential data for training machine learning models like GNNs to optimize quantum circuit parameters for future experiments. This can significantly improve the efficiency and scalability of quantum chemistry simulations.

## Usage
```python
import sqlite3, pandas as pd
conn = sqlite3.connect("results.sqlite")
df = pd.read_sql("SELECT * FROM runs LIMIT 5;", conn)
print(df.head())

@dataset{yang2025vqebench,
  author       = {Youla Yang},
  title        = {Quantum VQE Benchmark Dataset},
  year         = {2025},
  publisher    = {Zenodo},
  doi          = {10.5281/zenodo.xxxxxxx}
}
