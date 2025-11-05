---
title: Neutrino Physics - State of the Art
---

# Neutrino Physics

## Overview

In neutrino oscillation physics, a model typically has **three main components**:

1. **Initial neutrino flux**
2. **Flavor transition** given assumptions
3. **Detector response**

## Flux Description

Description of the un-oscillated flux can be:

- **Theoretical** (e.g., for solar neutrino)
- **Data-driven** (e.g., atmospheric neutrino, nuclear reactors)

## Oscillation Calculations

The code for computing flavor transition probabilities ranges from:

- Simple **two-flavor vacuum oscillation** probability calculations
- More computationally-intensive scenarios, such as **Beyond the Standard Model (BSM) n-flavor oscillations**

## Detector Response

The response of the neutrino detector translates the **oscillated spectrum** into the **space of observables**.

---

## Experimental Collaborations

Experimental collaborations develop sophisticated models for analyzing their data:

- **Super-K** (Super-Kamiokande)
- **Borexino**
- **IceCube**
- **T2K**
- **NOvA**
- **Daya Bay**

### Sharing Practices

These models are:

- **Rarely shared** with the public
- Often remain **proprietary**

---

## Global Fitter Efforts

There are several global-fitter efforts that aim to reproduce official results:

- **NuFit**[^1]
- **Bari**[^2]
- **Valencia**[^3]

Other groups use these data to explore **BSM physics**.

---

## Current Standards Situation

To date, **no common standard** for these purposes exists.

### Varied Practices

Practices vary significantly between collaborations:

- The **GLoBES**[^4] software package once aimed to unify simulation and analysis pipelines for reactor and beam neutrino oscillation experiments
- However, GLoBES has largely **fallen out of use**

---

## TUM Group Contributions

### IceCube Data Releases

The **TUM group (Eller)** has prepared and publicized a data release for **IceCube's oscillation analyses**.

**Challenge**: Since no predefined format existed, decisions on the structure were made **ad hoc**.

The process, while straightforward, required navigating:

- Internal approval processes
- Reflecting the PI's established position within the collaboration

### Global Fits

Furthermore, the TUM group has run **global neutrino oscillation fits** based on public data and re-implemented likelihoods[^5][^6][^7].

---

## MPP Group Contributions

### GERDA and MAJORANA

The **MPP group (Schulz)** has been deeply involved in the physics analysis of **GERDA** and **MAJORANA** experiments, focusing on:

- Statistical modeling
- Background suppression techniques
- **Neutrinoless double-beta decay** studies

### LEGEND Transition

Their contributions have supported the transition to **LEGEND** by:

- Refining data analysis methods
- Ensuring robust interpretation of experimental results
- Aligning with broader efforts in advancing precision neutrino physics

---

## Showcase Models

### Combined Analysis

MPP (Schulz) will add a **combined neutrinoless double decay analysis**[^8] to the DEMOS model gallery, based on:

- Data releases of the GERDA and MAJORANA experiments
- Published likelihoods from cosmology
- Neutrino oscillation experiments

**Significance**: This model will be a good showcase for how the DEMOS standard can be used to **express and combine** statistical models from different domains.

### Neutrino Oscillation Models

The TUM group (Eller) will work on containerizing neutrino oscillation models and equipping them with the **MaaS protocol** for seamless deployment and integration into diverse infrastructures.

---

## Summary

Neutrino physics presents unique challenges for model sharing:

❌ **Current Challenges**:

- No common standard exists
- Models rarely shared publicly
- GLoBES has fallen out of use
- Ad-hoc formats when data is released
- Proprietary collaboration practices

✅ **Opportunities**:

- TUM group experience with IceCube data releases
- MPP expertise in double-beta decay analysis
- Global fit experience and likelihood reconstruction
- Clear need for standardization recognized

🎯 **DEMOS Benefits**:

- Standardized format for oscillation parameters
- Combining models from different experiments
- Cross-domain integration (cosmology + oscillations)
- MaaS protocol for complex detector response models
- Enhanced reproducibility for global fits

The neutrino physics community will benefit significantly from the DEMOS standard, enabling better comparison of results across experiments and facilitating the combination of data from different sources for precision physics.

---

## References

[^1]: I. Esteban et al., "NuFit-6.0: Updated global analysis of three-flavor neutrino oscillations," Oct. 2024.

[^2]: A. Marrone et al., "Global fits to neutrino oscillations: status and prospects," *PoS*, EPS-HEP2015, p. 093, 2015.

[^3]: P. F. de Salas et al., "2020 global reassessment of the neutrino oscillation picture," *JHEP*, vol. 02, p. 071, 2021.

[^4]: P. Huber et al., "New features in the simulation of neutrino oscillation experiments with GLoBES 3.0: General Long Baseline Experiment Simulator," *Comput. Phys. Commun.*, vol. 177, pp. 432–438, 2007.

[^5]: M. Ettengruber et al., "Testing the number of neutrino species with a global fit of neutrino data," *Phys. Rev. D*, vol. 109, no. 9, p. 095016, 2024.

[^6]: T. Kozynets et al., "Constraints on non-unitary neutrino mixing in light of atmospheric and reactor neutrino data," July 2024.

[^7]: M. Ettengruber et al., "Discovering neutrinoless double-beta decay in the era of precision neutrino cosmology," *Phys. Rev. D*, vol. 106, no. 7, p. 073004, 2022.

[^8]: M. Ettengruber et al., "Discovering neutrinoless double-beta decay in the era of precision neutrino cosmology," *Phys. Rev. D*, vol. 106, no. 7, p. 073004, 2022.
