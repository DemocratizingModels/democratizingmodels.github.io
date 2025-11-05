---
title: Particle Physics - State of the Art
---

# Particle Physics

## Overview

Particle physics has benefited immensely from a relatively unified data analysis ecosystem, spearheaded by [ROOT](https://root.cern/)—a comprehensive framework developed and maintained by CERN.

## The ROOT Ecosystem

ROOT includes **RooFit** and **RooStats**, a powerful statistical modeling language capable of:

- Aggregating complex models with thousands of parameters
- Storing models as so-called **workspaces**
- Saving workspaces as binary files

Within analysis teams, models are typically constructed by a handful of statistics experts per team. These workspaces can even be **combined on the likelihood level**, a feature that was instrumental in the Higgs boson discovery[^1][^2].

### Limitations of ROOT

However, ROOT has some significant technical limitations:

- **Binary workspaces** can only be accessed and edited with ROOT software
- ROOT is **rarely used outside of high-energy physics** (HEP)
- This impedes **interoperability** with theorists or non-LHC experimental collaborations
- **Long-term sustainability** of preserving LHC-era models in this format is a growing concern (ROOT is aging software)

### Restricted Sharing

External sharing is restricted by:

- Formal collaboration policies
- Additional workload of preparing and verifying models in publishable formats

---

## PyHF: A Breakthrough

A breakthrough came with the development of **PyHF**[^3][^4]—a Python-based re-implementation of HistFactory, a popular binned modeling tool within the RooFit ecosystem.

**Lead developers** of PyHF are part of this consortium:

- **TUM** (Heinrich)
- **SC** (Stark)

### Key Features

The Python package came with a **serialization mechanism**, enabling easier sharing and publication of models.

**Current adoption**: To date, about **40 histogram-based models** have been published using PyHF format.

---

## HS3: HEP Statistics Serialization Standard

To bridge the gap from PyHF to the ROOT ecosystem, the **HEP Statistics Serialization Standard (HS3)**[^5] was developed by **TUDO (Burgard)**.

### Advantages of HS3

HS3 extends the range of model building blocks from histograms to a variety of continuous distributions, while maintaining **full reproducibility**.

**Key features**:

- Feature-complete, JSON-based serialization
- Support for continuous distributions beyond histograms
- Full reproducibility maintained

### Adoption

HS3 has been adopted by the **ATLAS collaboration** as an official standard for publishing likelihoods[^6][^7][^8][^9][^10][^11][^12][^13].

### Current Limitations

However, widespread adoption is still limited by:

- Lack of implemented engines outside the ROOT ecosystem
- Limited conversion tools

---

## Future Requirements

Looking forward, **additional flexibility** in models beyond the capabilities of the PyHF serialization and what is currently possible with HS3 is necessary.

### Example: Belle II Statistical Inference

Reference [^14] presents a highly general method for statistical inference on new physics parameters using an example from Belle II. The method is broadly applicable, using models encoded as **pyhf** or **HS3**, as well as future evolutions thereof.

**Benefits**:

- More precise parameter estimates
- Facilitates combination of results across experiments
- Enables combination across different physics domains

---

## Domain-Specific Languages

Conversely, there are statistical domain-specific languages (DSLs) like **STAN**[^15] that are:

- Fairly general
- Tightly coupled to specific ways of statistical inference
- Implemented in a single programming language

### STAN Example

STAN is focused on **Bayesian inference** via Hybrid Monte Carlo sampling in C++.

**Limitation**: While many models can be expressed in STAN, re-using, combining and sharing these models is not easy, leading to **limited adoption** in particle physics.

---

## The Opportunity

This proposal embraces the unique opportunity to **unite** the authors and maintainers of:

- **PyHF** (situated at TUM, LMU and SC)
- **HS3** ROOT engine (at TUDO)

behind a single harmonized approach.

---

## Consortium Contributions

### Statistical Tools Leadership

Consortium members are leading developers of:

- **PyHF** (TUM, LMU, SC)
- **HS3** standard (TUDO)
- **ROOT/RooStats** ecosystem (multiple institutions)

### Experimental Collaboration Leadership

Consortium members hold leadership positions in:

- **ATLAS** collaboration (TUDO, LMU, TUM)
- **CMS** collaboration
- **Belle II** experiment (LMU, MPP)

This positions the consortium ideally to drive adoption of the DEMOS standard within the particle physics community.

---

## Summary

Particle physics has made significant progress in model serialization and sharing, but challenges remain:

✅ **Achievements**:

- ROOT/RooFit provides powerful statistical modeling
- PyHF enables Python-based model serialization
- HS3 provides JSON-based serialization for ROOT workspaces
- Official adoption by ATLAS collaboration

❌ **Remaining Challenges**:

- Limited interoperability between ecosystems
- Aging ROOT infrastructure
- Need for more flexible model structures
- Limited adoption of sharing practices

The DEMOS initiative will build on these achievements to create a truly interoperable standard that serves the entire particle physics community and enables cross-disciplinary collaboration.

---

## References

[^1]: G. Aad et al., "Observation of a new particle in the search for the Standard Model Higgs boson with the ATLAS detector at the LHC," *Phys. Lett. B*, vol. 716, pp. 1–29, 2012.

[^2]: G. Aad et al., "A particle consistent with the Higgs Boson observed with the ATLAS Detector at the Large Hadron Collider," *Science*, vol. 338, pp. 1576–1582, 2012.

[^3]: L. Heinrich, M. Feickert, and G. Stark, "pyhf: v0.7.6," https://github.com/scikit-hep/pyhf/releases/tag/v0.7.6.

[^4]: L. Heinrich et al., "pyhf: pure-python implementation of histfactory statistical models," *Journal of Open Source Software*, vol. 6, no. 58, p. 2823, 2021.

[^5]: C. Burgard et al., "Hs3 v0.2," 2024.

[^6]: ATLAS collaboration, "Measurement of the charge asymmetry in top-quark pair production in association with a photon with the ATLAS experiment," *Phys. Lett. B*, vol. 843, p. 137848, 2023.

[^7]: ATLAS collaboration, "Inclusive and differential cross-section measurements of ttZ production," *JHEP*, vol. 07, p. 163, 2024.

[^8]: ATLAS collaboration, "Measurement of the tt̄ cross section and its ratio to the Z production cross section," *Phys. Lett. B*, vol. 848, p. 138376, 2024.

[^9]: ATLAS collaboration, "Search for heavy right-handed Majorana neutrinos," *Phys. Rev. D*, vol. 110, no. 11, p. 112004, 2024.

[^10]: ATLAS collaboration, "Measurements of inclusive and differential cross-sections of tt̄γ production," *JHEP*, vol. 10, p. 191, 2024.

[^11]: ATLAS collaboration, "Observation of tt̄ production in the lepton+jets and dilepton channels in p+Pb collisions," *JHEP*, vol. 11, p. 101, 2024.

[^12]: ATLAS collaboration, "Search for same-charge top-quark pair production in pp collisions," Sept. 2024.

[^13]: L. Gärtner et al., "Constructing model-agnostic likelihoods," *Eur. Phys. J. C*, vol. 84, no. 7, p. 693, 2024.

[^14]: L. Gärtner et al., "Constructing model-agnostic likelihoods, a method for the reinterpretation of particle physics results," *Eur. Phys. J. C*, vol. 84, no. 7, p. 693, 2024.

[^15]: Stan Development Team, "Stan: A probabilistic programming language," Version 2.33, 2023.
