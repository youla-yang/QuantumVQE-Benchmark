# Quantum VQE Benchmark Dataset

This dataset contains experimental logs of **Variational Quantum Eigensolver (VQE)** runs.  
It provides structured SQLite databases for reproducible benchmarking of optimization strategies, ansatz choices, and molecular Hamiltonians.

- Format: SQLite (`results.sqlite`, `runs.sqlite`)
- Molecules: H₂, LiH, BeH₂, H₂O
- Basis sets: STO-3G, 6-31G
- Circuit depths: 2–12
- Optimizers: Adam, PPO, COBYLA, etc.
- Total runs: ~380 (v1.0.0)

## Usage
```python
import sqlite3, pandas as pd
conn = sqlite3.connect("results.sqlite")
df = pd.read_sql("SELECT * FROM runs LIMIT 5;", conn)
print(df.head())
