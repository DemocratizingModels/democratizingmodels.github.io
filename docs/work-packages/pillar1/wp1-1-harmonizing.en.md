---
title: WP1.1 - Harmonizing Diverse Models
---

# WP1.1: Harmonizing Diverse Models

The objective of this work package is to define the **building blocks and elementary operations** required for creating a wide range of models across the diverse ErUM research domains.

---

## Overview

Drawing on techniques from RooFit/HS3, the central element of the DEMOS standard will be a **dataflow-like graph**: each building block can feed its output as input to another block. This flexible chain of computations allows the construction of complex probability distributions, likelihood functions, as well as priors and posteriors for Bayesian inference.

---

## Key Technical Requirements

### Structural Flexibility

The DEMOS standard must be sufficiently flexible to support the needs of different fields:

- **Complex Numbers**: Essential in multiple areas including hadron physics and quantum mechanics
- **Vectors and Matrices**: Regular primitives for transition amplitudes in hadron and nuclear physics
- **Dataflow Graphs**: Enable construction of complex objects from simpler ones through mathematical operations
- **Lazy Evaluation**: Memory occupation and computations must be deducible at parsing time

### Static Compilation Compatibility

An important requirement lies in the static properties of models:

- Memory occupation must be determinable at parsing time
- Lazy computations must be compatible with statically typed languages like C++
- Previous TUDO experience with the HS3 ROOT engine will help tackle these challenges

---

## Major Milestones

### M1: Fixing Structural Freedom (2026.Q1)

**Priority Task**: Guided by careful evaluation of consortium-provided use cases

**Approach**:
- Each research domain develops a summary of model features
- Domain-specific model-format proposals created by 2025.Q4
- Workshop held in 2026.Q1 to review and finalize design

**Responsibilities**:
- **HZDR**: Laser Physics (LP)
- **RUB-A**: Astroparticle Physics (AP)
- **RUB-N**: Nuclear Physics (NP)
- **RUB-H**: Hadron Physics (HP)
- **TUDO**: Particle Physics (PP)
- **TUM**: Neutrino Physics (NuP)

### Catalog of Basic Primitives

Shaping the DEMOS standard will be driven by use cases: groups will begin adapting significant models from their domain as soon as the project starts. Section 3.3.2 of the proposal details the models that will define:

- Structural features
- Catalog of basic primitives
- Domain-specific computational blocks

---

## Domain-Specific Proposals

### Workshop (2026.Q1)

A comprehensive workshop will be held to:

- Review domain-specific proposals
- Finalize the design of the DEMOS standard
- Identify first-priority domain-specific components
- Establish consensus on structural features

The workshop will bring together representatives from all ErUM domains to ensure the standard meets diverse needs while maintaining consistency.

---

## Extensibility Mechanism

### Coherent Mechanism for Adding Primitives (2028.Q3)

A key feature of the DEMOS standard will be a **coherent mechanism for adding new primitives** that ensures:

- Adaptability to evolving needs of various fields
- Support for domain-specific extensions
- Ability to reference user-defined distributions and functions
- Framework for testing and future extensions

This mechanism is critical for long-term sustainability and community adoption.

---

## Metadata and Attribution

### Publication Linking via DOIs

The standard will include comprehensive metadata:

- **DOIs**: Link to publications for provenance and attribution
- **Version Information**: Track model evolution over time
- **Model-Specific Metadata**: Accommodate domain-specific needs

Examples of domain-specific metadata:
- Lattice spacing for Lattice QCD models
- Quark masses for nuclear physics
- Detector configuration for experimental models
- Cutoff parameters for effective field theories

### Versioning Strategy

The DEMOS standard will implement a robust versioning system:

- Semantic versioning (MAJOR.MINOR.PATCH)
- Backward compatibility guarantees
- Migration guides between versions
- Deprecation policies

---

## Non-Serializable Models

### MaaS Protocol Integration

The standard will describe how non-serializable blocks are registered:

- Container-oriented work by MPP (WP1.3)
- MaaS protocol thoroughly outlined within the standard (2027.Q2)
- UUID-based referencing scheme
- Communication protocol specifications

---

## Documentation Deliverables

### Web-Based Documentation (2026.Q2)

Comprehensive documentation with versioning aligned to the format:

- **Standard Specification**: Complete technical reference
- **Building Block Catalog**: All primitive operations
- **Domain-Specific Guides**: Field-specific conventions
- **Examples and Tutorials**: Practical serialization guides
- **API Reference**: For all three engines
- **Best Practices**: Community guidelines

### Format and Structure

Documentation will be:

- **Machine-Readable**: JSON schema and formal specifications
- **Human-Readable**: Clear explanations with examples
- **Interactive**: Live examples where possible
- **Versioned**: Aligned with standard releases

---

## Use Case Validation

### Driving Development Through Real Models

The standard development will be continuously validated against real-world use cases:

1. **Early Adoption**: Groups begin serializing models immediately
2. **Feedback Loop**: Issues identified and addressed iteratively
3. **Cross-Domain Testing**: Ensure compatibility across fields
4. **Community Input**: Regular solicitation of user feedback

### Showcase Models

Significant models from each domain will test the standard:

- **Particle Physics**: Higgs discovery models, HistFactory likelihoods
- **Hadron Physics**: Partial-wave decompositions, cascade decays
- **Nuclear Physics**: Two-nucleon and three-nucleon potentials
- **Neutrino Physics**: Oscillation models with detector response
- **Astroparticle Physics**: Cosmic ray propagation, source models
- **Laser Physics**: Scattering cross-sections, structure factors

---

## Technical Challenges

### Complex Number Support

Implementing complex numbers requires:

- Native support in C++ (std::complex)
- Efficient representation in Python (complex type)
- Julia's native complex number support
- Consistent serialization format (real/imaginary pairs)

### Matrix Operations

Challenges for matrix/vector primitives:

- **Memory Layout**: Row-major vs. column-major
- **Sparse vs. Dense**: Optimization for different use cases
- **Dimensionality**: Support for N-dimensional arrays
- **Broadcasting**: Consistent rules across languages

### Static Typing Constraints

C++ static typing poses challenges:

- Type resolution at parse time
- Template instantiation strategies
- Runtime polymorphism where needed
- Compilation overhead management

---

## Collaboration and Communication

### Inter-Group Coordination

Regular coordination mechanisms:

- **Monthly Meetings**: Progress updates and issue resolution
- **GitHub Issues**: Technical discussions and decisions
- **Mailing List**: Announcements and general communication
- **Slack/Mattermost**: Real-time collaboration

### Community Engagement

Broader community involvement:

- **User Surveys**: Gather requirements and feedback
- **Beta Testing**: Early adopter program
- **Hackathons**: Intensive development sprints
- **Conference Presentations**: Raise awareness

---

## Risk Mitigation

### Identified Risks

| Risk | Mitigation Strategy |
|------|-------------------|
| Scope creep from diverse requirements | Clear prioritization framework, phased implementation |
| Incompatible domain needs | Early identification through workshops, extensibility mechanisms |
| Static typing limitations in C++ | Leverage TUDO expertise, prototype testing |
| Lack of community buy-in | Continuous engagement, leadership positions in collaborations |

---

## Success Metrics

WP1.1 will be evaluated on:

✅ **Structural Freedom Fixed** (2026.Q1): Clear specification of model structure
✅ **Domain Proposals Complete** (2025.Q4): All domains submit proposals
✅ **Workshop Success** (2026.Q1): Consensus achieved on core features
✅ **Primitives Catalog** (2026.Q2): Comprehensive list documented
✅ **Extensibility Mechanism** (2028.Q3): Framework for adding primitives operational
✅ **Documentation Live** (2026.Q2): Web-based docs available
✅ **10+ Models Serialized**: Diverse examples demonstrating flexibility

---

## Deliverables Summary

### By 2026.Q2

- ✓ Structural freedom fixed
- ✓ Domain-specific proposals reviewed
- ✓ Workshop completed with design consensus
- ✓ Catalog of basic primitives defined
- ✓ Web-based documentation published
- ✓ Metadata schema specified

### By 2027.Q2

- ✓ MaaS protocol outlined in standard
- ✓ First batch of domain-specific models serialized
- ✓ Validation framework operational

### By 2028.Q3

- ✓ Coherent mechanism for adding primitives complete
- ✓ Comprehensive set of showcase models available
- ✓ Standard versioning system established
- ✓ Community adoption demonstrated

---

## Personnel Allocation

**Total**: 0.7 person-years

### Distribution by Domain

- HZDR (LP): 0.1 py
- RUB-A (AP): 0.1 py
- RUB-N (NP): 0.1 py
- RUB-H (HP): 0.1 py
- TUDO (PP): 0.2 py
- TUM (NuP): 0.1 py

---

## Integration with Other Work Packages

### Dependencies

- **WP1.2 (Engines)**: Standard must be implementable in all three languages
- **WP1.3 (MaaS)**: Protocol for non-serializable models
- **WP2.1 (Front-end)**: Documentation portal integration
- **WP3.2 (Showcasing)**: Use cases drive requirements

### Outputs Used By

- All engine implementations (WP1.2)
- Model validation tools (WP2.2)
- Community documentation (WP3.1)
- Model gallery examples (WP2.1)

---

## Long-Term Vision

The harmonization work establishes the foundation for:

- **Cross-Disciplinary Collaboration**: Shared language for models
- **Reproducibility**: Complete model specifications
- **Preservation**: Long-term accessibility of research models
- **Education**: Accessible examples for students
- **Innovation**: Easy combination and extension of models

By carefully designing a flexible yet structured standard, WP1.1 enables the entire DEMOS ecosystem to flourish and serve the ErUM community for decades to come.

---

## Next Steps

- Explore [WP1.2: Engines →](wp1-2-engines.md) to see how the standard is implemented
- Learn about [WP1.3: Containers (MaaS) →](wp1-3-containers.md) for complex models
- Return to [Pillar 1 Overview →](index.md)
