# Estimating DNA Co-Encapsulation in Liposomes

## Description

This JupyterLite notebook models the **probability of DNA co-encapsulation** in liposomes using Poisson statistics. It generates **Figures S5 and S6** from the manuscript entitled "Autocatalytic selection of gene functions in vitro". The notebook also includes a calculator that allows users to specify the input concentrations of two DNA species and directly compute the corresponding probabilities of co-encapsulation. 

---

## Theory

To assess the probability of multiple DNA molecules being encapsulated within the same liposome, the encapsulation process is modeled using **Poisson statistics**.

The expected number of DNA molecules per liposome, **lambda (λ)**, is calculated as:

λ = (π N_A C d³) / 6

where:
- N_A is Avogadro's number
- C is the bulk input DNA concentration
- d is the liposome diameter

The probability of exactly **k DNA molecules** being encapsulated is:

P(k) = (λᵏ e^(−λ)) / k!

---

### Liposome Size Distribution

Liposomes prepared via the swelling method exhibit a **heterogeneous size distribution** and can be fitted to a log-normal function:

ln(d) ~ N(μ_d, σ_d²)

where μ_d and σ_d are the mean and standard deviation of the log-transformed liposome diameter (experimentally, μ_d = 4.5 µm, σ_d = 2.3 µm).

Since encapsulated volume scales with \( d^3 \), **λ also follows a log-normal distribution**. Thus, the population-averaged probability of encapsulating k molecules is:

P(k) = ∫ P(k|d) f_lognormal(d) dd

where:

f_lognormal(d) = [1 / (d σ_d √(2π)) ] * exp(− (ln(d) − μ_d)² / (2σ_d²))



## Generated Figures

### **Figure S5**

Plots the probability of encapsulating **0, 1, 2, 3, or >3 DNA molecules** as a function of input DNA concentration, incorporating the measured liposome size variability.

---

### **Figure S6**

For competition experiments involving two DNA species, the probability of both species coexisting within the same liposome is:

\[
P_{both species} = (1 - e^{-λ_A}) \times (1 - e^{-λ_B})
\]

This probability is plotted as a function of the total DNA concentration for the species ratios used in the manuscript (1:1 and 1:4).
---
## Calculator

In addition to generating Figures S5 and S6, this notebook includes a calculator that allows users to explore co-encapsulation probabilities under custom conditions.
Users can specify the input DNA concentrations of two distinct species, A and B (C_A_pM and C_B_pM, respectively), and compute the probability that both species are co-encapsulated within the same liposome.
---
## Usage

1. **Launch** in JupyterLite or standard JupyterLab.
2. **Run all cells sequentially**.
3. Adjust:
   - `mean_d` and `std_d` for your specific liposome preparations.
   - DNA concentration ranges as needed.

---

## Requirements

- Python ≥ 3.7
- `numpy`
- `matplotlib`

---

## Citation

This code was developed for:

**Autocatalytic selection of gene functions in vitro, 2025**

If used, please cite accordingly. For questions, contact:

- **Author:** Laura Sierra Heras
- **Email:** sierra-heras@insa-toulouse.fr or danelon@insa-toulouse.fr
