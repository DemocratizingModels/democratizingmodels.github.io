---
title: State of the Art
---

# State of the Art

## The Diverse ErUM Software Ecosystem

The ErUM disciplines are supported by an incredibly **diverse and fragmented software ecosystem** where models are implemented and used. Researchers employ a wide range of programming languages, including:

- **C++** - Performance-critical applications
- **Fortran** - Legacy scientific computing
- **Python** - Modern data analysis
- **Julia** - High-performance numerical computing
- **Mathematica** - Symbolic mathematics

Each language is tailored to specific computational needs and community preferences.

## Current Practices

### Custom Implementation

Most of the time, researchers write **custom analysis code** for specific studies, including detailed models for unique use cases. These coded models are often shared through private communication upon request.

### Manual Reproduction

In other cases, **complex analytic expressions** in scientific publications must be manually reproduced—a process that is not only **error-prone** but also frequently **infeasible** due to incomplete information in the publications.

### Legacy Code Reconstruction

Occasionally, researchers must painstakingly **reconstruct model code from decades-old publications** just to incorporate it into modern workflows. Many research models remain **inaccessible** due to:

- Lack of sufficient information in the literature
- Significant effort required to prepare them for reuse
- Complex custom code dependencies
- Outdated or legacy software requirements
- Intricate machine learning techniques

This issue is particularly acute for models reliant on complex custom code, thereby inhibiting broader collaboration.

### Limited Version Control

For code fragments that are shared through direct communication, **version control techniques** and **Zenodo references** are becoming more common. Nevertheless, these practices remain the **exception rather than the rule**.

---

## The Need for Unification

This heterogeneity poses a fundamental challenge to collaboration both across research domains and within individual fields.

!!! note "Respecting Established Tools"
    Established tools, frameworks, and practices cannot simply be discarded—they are time-tested and deeply ingrained in their respective communities.

### The DEMOS Approach

Instead, what is urgently needed is a **unifying standard** that:

- Respects the diversity of existing ecosystems
- Enables seamless collaboration and interoperability
- Acts as a bridge between tools, repositories, and disciplines
- Allows researchers to share, combine, and extend models across disciplines
- Does not disrupt existing workflows

By providing the new DEMOS standard as a communication layer between tools, repositories, and disciplines, DEMOS aims to create a connected and collaborative research environment, unlocking new opportunities for interdisciplinary innovation.

---

## Model Complexity Across Domains

It is important to realize that the **definition of a model** might vary between different fields, ranging from:

- **Simple functions** depending on only a few parameters
- **Complicated, multi-dimensional objects** depending on thousands of parameters
- **Binned models** discretized in some observable
- **Smooth analytical functions**

Nonetheless, many model features and building blocks are **common across the ErUM disciplines**, underscoring the need for a unified model standard to facilitate a model-sharing platform.

---

## Domain-Specific State of the Art

Below, we review the ErUM fields in terms of model complexity, as well as current practices for sharing, reproducing, and extending models.

### [Particle Physics →](particle-physics.md)

Review of ROOT/RooFit ecosystem, PyHF, HS3 standard, and statistical modeling in high-energy physics.

### [Hadron Physics →](hadron-physics.md)

Current practices in hadron spectroscopy, partial-wave analysis, and amplitude models across LHCb, Belle II, BESIII, and COMPASS.

### [Nuclear Physics →](nuclear-physics.md)

Ab-initio nuclear structure calculations, chiral effective field theory, and nucleon-nucleon interactions.

### [Neutrino Physics →](neutrino-physics.md)

Neutrino oscillation models, detector response functions, and global fits across IceCube, Super-K, and other experiments.

### [Laser Physics →](laser-physics.md)

Laser-matter interaction models, warm-dense matter physics, and structure factors for X-ray probing.

### [Astroparticle Physics →](astroparticle-physics.md)

Cosmic ray propagation, multi-messenger models, and source modeling using CRPropa, GALPROP, and CORSIKA.

---

## Summary

In summary, **models represent an invaluable part** of describing physical effects and interpreting experimental data across all domains of the ErUM fields.

Yet, the exchange of models between experiments, across fields, or between experiment and theory is **significantly hindered** by the absence of an established standard.

We therefore aim to establish such a standard—**the DEMOS standard**—alongside a platform that will facilitate the exchange of models across disciplines and provide easy, open access to a broad range of practitioners.

To achieve these goals, our consortium is uniquely positioned, combining a diverse range of expertise from experimental and theoretical physicists across the ErUM disciplines—a solid foundation for the success of our proposal.
