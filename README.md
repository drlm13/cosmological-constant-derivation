# CSU Framework — Complete Computational Validation Suite
# ======================================================

## Overview

This repository contains **two independent computational validations** of
predictions made by the Categorical Spectral Unification (CSU) framework.
Every result is **computed** by SymPy's symbolic mathematics engine — no
result is merely printed as a string. Every result uses `assert` — the
scripts **fail** if any computation produces an incorrect result.

## Validation 1: Cosmological Constant

**Files:**
- `CSU_Cosmological_Constant_Validation.ipynb` (Jupyter notebook)
- `CSU_Cosmological_Constant_Validation.py` (standalone script)

**What it computes:**

| Quantity | CSU Value | Observed | Deviation |
|----------|-----------|----------|-----------|
| Ω_Λ | 25/36 ≈ 0.6944 | 0.6847 ± 0.0073 | 1.4% |
| Ξ_Λ | ≈ 2.87×10⁻¹²² | ≈ 2.89×10⁻¹²² | 0.7% |

**Derivation chain (all computed):**
```
χ(S²) = 2          ← Gauss-Bonnet integration (diff + integrate)
ζ(−1) = −1/12      ← SymPy zeta()
c = 1               ← Sugawara construction, U(1) at k=1
w_vac = 25/12       ← superselection theorem
Ω_Λ = 25/36        ← Friedmann equation
k = 57              ← SM field count: 66 − 9
Ξ_Λ ≈ 2.87×10⁻¹²² ← e^γ · α^57
```

## Validation 2: Fine Structure Constant (α⁻¹ = 137)

**Files:**
- `CSU_Fine_Structure_Constant_Validation.ipynb` (Jupyter notebook)
- `CSU_Fine_Structure_Constant_Validation.py` (standalone script)

**What it computes:**

| Step | Result | Method |
|------|--------|--------|
| UV generators | 66 | Explicit enumeration of every SM field |
| Phase space doubling | 132 | Canonical conjugates (required by unitarity) |
| Algebraic constraint | p ≥ 133 | Wedderburn's theorem → Galois field F_p |
| Primality of 133 | COMPOSITE (7×19) | SymPy `factorint()` |
| Primality of 134 | COMPOSITE (2×67) | SymPy `factorint()` |
| Primality of 135 | COMPOSITE (3³×5) | SymPy `factorint()` |
| Primality of 136 | COMPOSITE (2³×17) | SymPy `factorint()` |
| Primality of 137 | **PRIME** | SymPy `isprime()` |
| **Result** | **α₀⁻¹ = 137** | Zero free parameters, zero skipped primes |

**Cross-checks included:**
- Removing ν_R → wrong answer (proves ν_R required)
- Removing graviton → wrong answer (proves graviton required)
- Skipping phase space doubling → wrong answer (proves doubling required)
- The result is **fragile to omissions** — every piece is necessary

## Requirements

```bash
pip install sympy
```

Python 3.8+ required. SymPy ≥ 1.12 recommended.

## Running

```bash
# Run both validations:
python CSU_Cosmological_Constant_Validation.py
python CSU_Fine_Structure_Constant_Validation.py

# Or in Jupyter:
jupyter notebook
# Then open either .ipynb file

# Or in Google Colab:
# Upload the .ipynb files directly
```

## What Makes These Validations Real

Previous validation scripts used `TensorHead()` to create blank symbols and
`print()` to display pre-written equation strings. **These scripts actually compute:**

- Christoffel symbols via `diff()`
- Riemann curvature tensor via `diff()` of Christoffel symbols
- Gauss-Bonnet integral via `integrate()`
- Zeta function via `zeta()`
- Bernoulli numbers via `bernoulli()`
- Harmonic number convergence via `harmonic()`
- Primality testing via `isprime()`
- Prime factorisation via `factorint()`

Every result uses `assert` — the scripts **crash** if any computation is wrong.

## Repository Structure

```
CSU_Computational_Validation/
├── README.md                                        # This file
├── requirements.txt
├── LICENSE
├── CSU_Cosmological_Constant_Validation.ipynb       # Notebook: Λ validation
├── CSU_Cosmological_Constant_Validation.py          # Script: Λ validation
├── CSU_Fine_Structure_Constant_Validation.ipynb     # Notebook: α validation
└── CSU_Fine_Structure_Constant_Validation.py        # Script: α validation
```

## License

MIT License — see LICENSE file.

## Citation

If you use these validations in academic work, please cite the CSU framework papers.
