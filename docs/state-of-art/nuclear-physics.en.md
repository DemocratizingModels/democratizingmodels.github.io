---
title: Nuclear Physics - State of the Art
---

# Nuclear Physics

## Overview

In the domain of nuclear physics, the **ab-initio framework** provides a foundational approach for studying nuclear structure and dynamics.

This computational framework involves solving the **N-body Schrödinger equation**, with relativistic corrections incorporated via a one-over-mass expansion. This now enables the reliable description of properties of light and medium-mass nuclei for specific nuclear Hamiltonians.

## Sources of Uncertainty

For these nuclei, the dominant source of uncertainty arises not from the computational frameworks, but from the **nuclear Hamiltonian itself**, particularly the poorly understood **three-nucleon forces**.

---

## Chiral Effective Field Theory (EFT)

Over the past two decades, **chiral effective field theory (EFT)** has largely replaced the traditional phenomenological approaches to nuclear interactions in these contexts.

### RUB-N Leadership

**RUB-N** is among **worldwide leading groups** that develop models for:

- Nuclear forces
- Nuclear interactions with external electroweak probes
- All within the framework of chiral EFT

See references [^1] and [^2] for comprehensive reviews.

---

## Model Components

### Nuclear Interaction Models

Nuclear models correspond to mathematical expressions describing:

1. **Two-nucleon (NN) potentials**
2. **Three-nucleon (3N) potentials**
3. **Associated current operators**

These potentials are offered at:

- Different **orders** of the EFT expansion
- Various values of the **cutoff parameter**
- Different **bases**

### Low-Energy Constants (LECs)

**Correlated uncertainties** for the low-energy constants (LECs) are also available.

### Marginalization Over Truncation

Work on generating **large samples of potentials** (ranging from hundreds to thousands) with randomly chosen higher-order terms is in progress to enable **marginalization** over contributions from truncated corrections beyond the considered accuracy level.

---

## Computational Aspects

### NN Forces

For **NN forces**, existing codes in **Fortran** or **Python** are capable of generating the NN matrix elements **dynamically ("on-the-fly")**.

### 3N Forces

However, the generation of matrix elements for **3N forces** is significantly more complex, often resulting in data files that can exceed **several tens of gigabytes**.

---

## Community Structure

### Model Developers

Several research groups are actively engaged in modeling nuclear interactions, with **RUB-N** recognized as one of the **most prominent contributors**.

### User Community

On the user side, there are:

- **Several dozen established** few- and many-body groups worldwide
- A **much larger number of individual researchers** who rely on these interactions

Collections of articles[^3][^4][^5] provide an indication of the widespread use of these models across the community.

---

## Current Sharing Practices

### NN Interactions

For **NN interactions**, matrix elements are typically:

- Published
- Codes to generate them are provided **upon request**

### Analytical Expressions

Analytical expressions for various contributions are often shared as **Mathematica notebooks**.

### Limitations

However, these sharing mechanisms of models are **not standardized**, and informal mechanisms such as **direct requests to authors** remain common.

---

## Opportunities for Improvement

Efforts to develop and disseminate **standards and workflows** could significantly improve:

- **Accessibility** of nuclear interaction models
- **Reproducibility** of calculations
- **Collaboration** within the nuclear physics community

---

## DEMOS Contributions

### Showcase Models

Within this funding period, **RUB-N** will focus on serializing models for **NN interactions**, which provide dominant contributions to nuclear structure and low-energy reactions.

Model development includes:

1. Deriving NN potentials from the effective chiral Lagrangian up to a specified order
2. Introducing a suitable ultraviolet regulator
3. Determining NN low-energy constants through global partial-wave analysis (PWA)
4. Error analysis and quantification of truncation uncertainty

### Comprehensive Model Collection

The NN potential models developed in [^6] are available at:

- **Five EFT expansion orders**
- **Various cutoff values**

These interactions were extended in [^7] to include **isospin-breaking corrections** from:

- QED contributions
- Differences in quark masses

### Achievement

The resulting models were used to perform a comprehensive PWA of all available NN scattering data up to the pion production threshold, including:

- Determination of a consistent database of NN data
- Uncertainty quantification

**Result**: For the first time, a **statistically perfect description** of NN data was achieved within the chiral EFT framework.

---

## Resources to be Shared

We will establish a mechanism for sharing these models along with:

- **Detailed documentation**
- **Examples of applications**
- **Benchmark results**
- **Resources for performing uncertainty propagation**:
    - Covariance matrices for LECs
    - Samples of models with randomly chosen higher-order interactions
    - For quantifying truncation errors
- **Documented up-to-date database** of mutually consistent NN scattering data

---

## Summary

Nuclear physics model sharing presents both challenges and opportunities:

✅ **Current Practices**:

- NN matrix elements typically published
- Code provided upon request
- Mathematica notebooks for analytical expressions
- Strong theoretical framework (chiral EFT)

❌ **Limitations**:

- No standardized sharing mechanisms
- Informal request-based system
- 3N forces particularly challenging (tens of GB files)
- Limited automation and accessibility

🎯 **DEMOS Benefits**:

- Standardized model serialization
- Comprehensive documentation
- Uncertainty quantification tools
- Accessible database of interactions
- Enhanced collaboration across few- and many-body communities

The nuclear physics community will greatly benefit from the DEMOS standard, enabling more efficient sharing of complex nuclear interaction models and fostering broader collaboration in ab-initio nuclear structure calculations.

---

## References

[^1]: E. Epelbaum et al., "Modern Theory of Nuclear Forces," *Rev. Mod. Phys.*, vol. 81, pp. 1773–1825, 2009.

[^2]: E. Epelbaum et al., "High-precision nuclear forces from chiral EFT: State-of-the-art, challenges and outlook," *Front. in Phys.*, vol. 8, p. 98, 2020.

[^3]: M. Piarulli et al., "Editorial: Uncertainty quantification in nuclear physics," *Front. in Phys.*, vol. 11, p. 1270577, 2023.

[^4]: L. Marcucci, "Editorial: The Long-Lasting Quest for Nuclear Interactions: The Past, the Present and the Future," *Front. in Phys.*, vol. 8, p. 609907, 2020.

[^5]: I. Tews et al., "Nuclear Forces for Precision Nuclear Physics: A Collection of Perspectives," *Few Body Syst.*, vol. 63, no. 4, p. 67, 2022.

[^6]: P. Reinert et al., "Semilocal momentum-space regularized chiral two-nucleon potentials up to fifth order," *Eur. Phys. J. A*, vol. 54, no. 5, p. 86, 2018.

[^7]: P. Reinert et al., "Precision determination of pion-nucleon coupling constants using effective field theory," *Phys. Rev. Lett.*, vol. 126, no. 9, p. 092501, 2021.
