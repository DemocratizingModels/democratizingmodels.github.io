---
title: Astroparticle Physics - State of the Art
---

# Astro- and Astroparticle Physics

## Overview

In astro- and astroparticle physics, modeling astrophysical sources across a wide range of detection channels is a central aspect of research.

### Detection Channels

- **Electromagnetic radiation** (radio to TeV energies)
- **Neutrinos**
- **Cosmic rays**
- **Gravitational waves**

### Dual Purposes

These models serve dual purposes:

1. Help scientists understand how **observables at Earth** are related in momentum, space, and time
2. Provide **predictions** that guide the technical design of instruments and the development of analysis methods

---

## Model Structure

A typical model in this domain uses **probability distribution functions as inputs**—representing sources and targets—and propagates these to create **output probability distributions in phase space**.

---

## Model Complexity

Theoretical models in this field can be classified by their complexity.

### Analytical Models

**Analytical models** are often used, but they typically involve significant **simplifications** of the underlying physics.

### Numerical Models

These models are complemented and validated by more complex **numerical models**, which can account for:

- **Three-dimensional distributions** of the source environment
- More realistic physics

Numerical models frequently rely on:

- **Solvers for partial differential equations** (both linear and nonlinear)
- **Monte Carlo approaches**

### Statistical Fitting

Fitting theoretical models to data is commonly performed using statistical methods, with **MCMC approaches** being particularly prevalent.

---

## Serialization Challenges

The serialization of models in astro- and astroparticle physics can present challenges, particularly with **numerical solvers**.

### Parallelization

- **Monte Carlo codes** are trivially parallelized by distributing individual particle trajectories to separate nodes
- **Numerical solvers** for partial differential equations require more sophisticated parallelization techniques

---

## CRPropa: A Leading Code

**CRPropa**, a propagation and interaction code primarily developed by **RUB-A**, is an example of a modular code written in **C++ with a Python wrapper**.

### Design Features

Its design allows for easy adjustment of:

- Source environments
- 3D distribution functions that serve as model inputs

### Computational Requirements

Depending on the complexity of the model, a single run can require between:

- **10⁴ CPU hours** (simpler models)
- **10⁶ CPU hours** (complex models)

Simpler models, often created for testing, can be executed on significantly shorter timescales.

---

## Model Production and Consumption

### Development Scale

Model production and consumption in this domain involve both small and large-scale efforts.

### CRPropa Collaboration

**CRPropa** is maintained by an international collaboration of around **20 researchers**.

The code is **public**, complete with:

- Examples
- Manuals
- **Help desk** operated by the developers on a rotating basis

### User Base

Its user base includes **over 100 researchers**, and the code is employed for:

- Theoretical studies
- Observational analyses with instruments such as **Auger** and **IceCube**

---

## Similar Public Codes

Similar public codes have comparable levels of development and user engagement:

### GALPROP and DRAGON

- Focus on modeling the propagation and interaction of cosmic rays **in the Milky Way**
- Use **numerical solutions to the transport equation**

### CRPropa Distinction

- **CRPropa**, in contrast, is tailored to **galactic and extragalactic propagation**
- Employs a **Monte Carlo approach**

### CORSIKA

- **CORSIKA** simulates the development of **cosmic ray showers in Earth's atmosphere**
- Also uses a **Monte Carlo framework**

---

## Showcase Models

The astroparticle models chosen by **RUB-A** for the project focus on:

- **Particle propagation**
- **Observable spectra under specific assumptions**

Providing templates for broader adoption of the DEMOS standard in the field.

### Model Diversity

The models cover diverse sources and particle types, offering varied representations:

- **Parametric distributions** in histogram format
- **Analytic formulations**

### Specific Models

1. **γ-rays from jets** of the Seyfert II galaxy NGC 1068[^1]
2. **Cosmic-ray transport** in the Central Molecular Zone with anisotropic diffusion[^2]
3. **Cosmic-ray electrons** in the face-on galaxy M51 through synchrotron radiation[^3]
4. **Multi-messenger model** integrating active-galactic-nuclei corona and starburst emissions[^4]
5. **Analytical Galactic center magnetic field model** linking cosmic-ray propagation to γ-ray observations[^5]

---

## Summary

Astroparticle physics presents unique model sharing opportunities:

✅ **Current Strengths**:

- Well-established public codes (CRPropa, GALPROP, CORSIKA)
- International collaborations (CRPropa: ~20 developers, 100+ users)
- Public documentation and help desks
- Multi-messenger approach
- Broad user base across theory and experiment

❌ **Current Challenges**:

- Diverse computational requirements (10⁴ to 10⁶ CPU hours)
- Complex numerical solvers require sophisticated parallelization
- Models range from simple analytical to complex 3D numerical
- No standardized format for model exchange
- Difficult to combine models from different codes

🎯 **DEMOS Benefits**:

- Standardized format for both analytical and histogram-based models
- Enable comparison between different propagation codes
- Facilitate multi-messenger analysis
- Better integration between galactic and extragalactic studies
- Enhanced reproducibility for theoretical predictions
- Easier combination of models for instrument design

The astroparticle physics community will benefit from the DEMOS standard by enabling better comparison of results from different codes and facilitating the integration of models across the full range of cosmic messengers and energy scales.

---

## References

[^1]: S. Salvatore et al., "Possible jet contribution to the γ-ray luminosity in NGC 1068," *Astron. Astrophys.*, vol. 687, p. A139, July 2024.

[^2]: J. Dörner et al., "Impact of Anisotropic Cosmic-Ray Transport on the Gamma-Ray Signatures in the Galactic Center," *Astrophys. J.*, vol. 965, no. 2, p. 180, April 2024.

[^3]: J. Dörner et al., "Cosmic-ray electron transport in the galaxy M 51," *Astron. Astrophys.*, vol. 669, p. A111, January 2023.

[^4]: B. Eichmann et al., "Solving the Multimessenger Puzzle of the AGN-starburst Composite Galaxy NGC 1068," *Astrophys. J.*, vol. 939, no. 1, p. 43, November 2022.

[^5]: M. Guenduez et al., "A novel analytical model of the magnetic field configuration in the Galactic center," *Astron. Astrophys.*, vol. 644, p. A71, December 2020.
