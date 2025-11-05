---
title: Hadron Physics - State of the Art
---

# Hadron Physics

## Overview

In the domain of hadron physics, particularly within the subfield of **hadron spectroscopy**, models serve as mathematical frameworks to describe the properties and interactions of hadrons and the hadronic environment.

**Scattering amplitudes** between hadrons are modeled using a partial-wave expansion to constrain properties of hadronic resonances and fit to measured differential spectra.

## Data Sources

Hadron-physics data come mostly from:

### Collider Experiments

- **LHCb** - Large Hadron Collider beauty experiment
- **Belle II** - B-factory experiment
- **BESIII** - Beijing Spectrometer
- **COMPASS** - COmmon Muon and Proton Apparatus for Structure and Spectroscopy
- **GlueX** - Photoproduction experiment

### Lattice Simulations

Complementary information has been obtained recently from **lattice simulations of Quantum Chromodynamics (Lattice QCD)**.

---

## Consortium Representation

### Experimental Side

Represented here by:

- **RUB-H** (Mikhasenko, Fritsch) - LHCb, COMPASS
- **MPP** (Wallner) - Belle II, COMPASS
- **JGU** (Hüsken) - BESIII

### Lattice QCD

- **RUB-H** (J. Bulava) - Develops and utilizes hadronic models to connect finite-volume spectra to hadron scattering amplitudes. Has published a comprehensive collection of these relations as well as a corresponding C++ implementation[^1].

---

## Research Focus

The field is driven by studies of **exotic configurations of quark matter**:

- **Tetraquarks** (four-quark states)
- **Pentaquarks** (five-quark states)
- **Hybrids** (quark-antiquark with excited glue)
- **Glueballs** (bound states of gluons)

### Broader Impact

Hadron physics also contributes seminally to other domains:

- Precision measurements of Standard Model observables
- Search for physics beyond the Standard Model
- Hunt for Dark Matter
- Study of neutron stars

---

## LHCb Leadership

The **LHCb collaboration**, represented by RUB-H group, leads the field with:

- Discovery of **more than 70 new composite particles**, many of exotic nature
- **~700 publications**, the majority with modeling aspects that will be captured by the DEMOS standard
- **At least 30 complex models** of particular significance for the broader community

---

## Belle II Contributions

Within **Belle II**, the MPP group leads the effort to constrain partial-wave models for the hadronic resonance structure of multi-body hadronic B and τ decays.

This complements measurements by LHCb and BESIII. With this effort, expertise on development of one of the **most complex resonance models from COMPASS**[^2] is being transferred to the Belle II experiment[^3].

---

## BESIII Excellence

Work on vector-charmonium resonances carried out by the **JGU group** benefits from world-leading datasets of the BESIII experiment.

The group leads the global effort on interpreting this data[^4][^5] with an advanced modeling technique.

### Specific Applications

Models extracted using BESIII data include:

- **Event generation** of γp → Zc(3900)p required for CEBAF facility energy upgrade at Jefferson Lab
- **Precise lineshapes** of vector charmonium states needed in studies of weak b → sℓ⁺ℓ⁻ decays
- **D-meson decay** measurements at BESIII providing key input for CKM-matrix parameter measurements at LHCb and Belle II

### Community Position

As a **convener of the charmonium physics group**, the PI is uniquely positioned to lead the community engagement activities within BESIII.

---

## The Challenge: Dramatic Sharing Situation

The situation with sharing models is **dramatic** in the field:

### Reproducibility Crisis

Complex parameterizations of partial waves are **mostly impossible to reproduce** from published information due to:

- Missing details about conventions
- Missing normalization information
- Incomplete descriptions of large parameter sets

### Model Uncertainties

Model uncertainties are **almost never included** in published data.

### Framework Fragmentation

**Dozens of frameworks** exist within the domain of experimental partial-wave analysis, each with an internal memory model for representing partial-wave decompositions.

Most researchers develop their **own framework** during their learning path, which typically takes **multiple years** to accomplish.

There is **no universal standard** for transporting information between frameworks, leading to:

- Challenges in interoperability
- Inconsistency across the field

---

## Standardization Efforts

An effort to standardize partial-wave models has been initiated by the **RUB-H group** with several methodology papers[^6][^7][^8][^9].

### Amplitude Serialization

A prototype for a description of cascade decays developed in recent years is available at [amplitude-serialization](https://github.com/ComPWA/amplitude-serialization).

**Current Limitation**: The model complexity is strongly limited to three-body decays, calling for the inclusion of this class of models in the DEMOS standard.

---

## Consortium Contributions

### Complex Models to be Showcased

RUB-H group will serialize **highly cited examples**:

1. **Pcc̄ pentaquarks** - Discovery in Λ⁰b → J/ψK⁻p decays[^10]
2. **Λ⁺c → pK⁻π⁺** decays - Showcasing proper reporting of modeling uncertainty with 18 alternative models[^11]
3. **χc1(3872) and T⁺cc tetraquark** analyses - Complicated lineshape parameterizations[^12][^13]
4. **Tcs and Tcs̄ states** - Amplitude models of B decay to DDπ and DDK[^14][^15]

---

## Summary

Hadron physics faces unique challenges in model sharing:

❌ **Critical Issues**:

- Complex models impossible to reproduce from publications
- Dozens of incompatible frameworks
- No universal standard for model exchange
- Model uncertainties rarely reported
- Years required to develop analysis expertise

✅ **Opportunities**:

- RUB-H pioneering standardization efforts
- Amplitude serialization prototype exists
- Strong consortium representation in major experiments
- Clear need recognized by community

The DEMOS initiative will address these challenges by providing a comprehensive standard that can capture the complexity of hadron physics models while enabling reproducibility and cross-experiment collaboration.

---

## References

[^1]: C. Morningstar et al., "Estimating the two-particle K-matrix for multiple partial waves," *Nucl. Phys. B*, vol. 924, pp. 477–507, 2017.

[^2]: M. Aghasyan et al., "Light isovector resonances in π⁻p → π⁻π⁻π⁺p at 190 GeV/c," *Phys. Rev. D*, vol. 98, no. 9, p. 092003, 2018.

[^3]: A. Rabusov et al., "Measurement of the presence of a₁(1420) and ω(782) in τ⁻ → π⁻π⁻π⁺ντ at Belle," *17th International Workshop on Tau Lepton Physics*, May 2024.

[^4]: N. Hüsken et al., "Poles and poltergeists in e⁺e⁻ → DD̄ data," *Phys. Rev. D*, vol. 109, no. 11, p. 114010, 2024.

[^5]: N. Hüsken et al., "K-matrix analysis of e+e- annihilation in the bottomonium region," *Phys. Rev. D*, vol. 106, no. 9, p. 094013, 2022.

[^6]: M. Mikhasenko et al., "Dalitz-plot decomposition for three-body decays," *Phys. Rev. D*, vol. 101, no. 3, p. 034033, 2020.

[^7]: K. Habermann and M. Mikhasenko, "Wigner rotations for cascade reactions," Sept. 2024.

[^8]: M. Mikhasenko et al., "What is the right formalism to search for resonances?" *Eur. Phys. J. C*, vol. 78, no. 3, p. 229, 2018.

[^9]: A. Pilloni et al., "What is the right formalism to search for resonances? II. The pentaquark chain," *Eur. Phys. J. C*, vol. 78, no. 9, p. 727, 2018.

[^10]: R. Aaij et al., "Observation of J/ψp Resonances Consistent with Pentaquark States," *Phys. Rev. Lett.*, vol. 115, p. 072001, 2015.

[^11]: R. Aaij et al., "Amplitude analysis of the Λ⁺c → pK⁻π⁺ decay," *Phys. Rev. D*, vol. 108, no. 1, p. 012023, 2023.

[^12]: R. Aaij et al., "Study of the lineshape of the χc1(3872) state," *Phys. Rev. D*, vol. 102, no. 9, p. 092005, 2020.

[^13]: R. Aaij et al., "Study of the doubly charmed tetraquark T⁺cc," *Nature Commun.*, vol. 13, no. 1, p. 3351, 2022.

[^14]: R. Aaij et al., "Amplitude analysis of the B⁺ → D⁺D⁻K⁺ decay," *Phys. Rev. D*, vol. 102, p. 112003, 2020.

[^15]: R. Aaij et al., "Amplitude analysis of B⁰ → D̄⁰D⁺sπ⁻ and B⁺ → D⁻D⁺sπ⁺ decays," *Phys. Rev. D*, vol. 108, no. 1, p. 012017, 2023.
