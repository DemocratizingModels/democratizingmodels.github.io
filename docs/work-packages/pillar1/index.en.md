---
title: Pillar 1 - Model Format Standardization
---

# Pillar 1: Model Format Standardization

The first key pillar of this initiative is the creation of a **unified, standardized model format** that addresses the diverse needs of the ErUM research community.

---

## Overview

This pillar focuses on three major work packages:

### WP1.1: Harmonizing Diverse Models

Identification of key common features across ErUM research domains and standard computational primitives for each domain that will structure the DEMOS standard.

[Learn more →](wp1-1-harmonizing.md)

### WP1.2: Engines

Implementation of the DEMOS standard computation engines in **C++**, **Python**, and **Julia** to ensure broad accessibility and performance.

[Learn more →](wp1-2-engines.md)

### WP1.3: Containers (Models as a Service)

For models using custom complex code or legacy systems, implementation of a **Models as a Service (MaaS)** approach using containerization and well-defined communication protocols.

[Learn more →](wp1-3-containers.md)

---

## Key Objectives

The objectives of Pillar 1 are to:

1. **Define a common standard** that respects the diversity of existing ecosystems
2. **Implement computational engines** in multiple languages for broad adoption
3. **Enable complex model sharing** through containerization (MaaS)
4. **Ensure static type compatibility** for languages like C++
5. **Provide interactive exploration** capabilities for models

---

## Timeline

| Milestone | Quarter | Description |
|-----------|---------|-------------|
| **M1** | 2026.Q2 | Modeling standard defined: structural freedom constrained, native primitives identified |
| **M3** | 2027.Q1 | Engines in Python, Julia, and C++ support nested model constructions |
| **M4** | 2027.Q2 | Model as a Service protocol working, UUIDs generated |
| **M7** | 2028.Q1 | Validation tools working, engine tests cover 70%+ |

---

## Personnel Allocation

Total person-years for Pillar 1: **3.4 years**

| Work Package | Person-Years |
|--------------|--------------|
| WP1.1 Harmonizing | 0.7 |
| WP1.2 Engines | 2.05 |
| WP1.3 Containers | 0.65 |

---

## Expected Outcomes

### Technical Deliverables

1. **DEMOS Standard Specification**
   - JSON-based serialization format
   - Dataflow graph structure
   - Computational primitives catalog
   - Metadata schema
   - Versioning mechanism

2. **Computational Engines**
   - C++ engine (ROOT/RooFit integration)
   - Python engine (JAX/Numba backend)
   - Julia engine (symbolic + numerical)
   - Cross-language validation tests

3. **MaaS Infrastructure**
   - Communication protocol specification
   - Container templates
   - Client/server libraries for all engines
   - UUID-based model referencing

### Documentation

- Standard specification documentation
- Engine implementation guides
- Domain-specific serialization examples
- MaaS protocol documentation

---

## Consortium Contributions

### Leading Institutions

- **TUDO** - C++ engine, HS3 expertise
- **LMU** - Python engine, PyHF expertise
- **TUM** - Python engine development
- **SC** - PyHF maintenance
- **HZDR** - Julia engine, computational graphs
- **RUB-H** - Julia engine prototype
- **MPP** - MaaS implementation, containers
- **JGU** - C++ implementation (AmpTools)

---

## Integration with Existing Tools

The DEMOS standard will integrate with and extend:

- **ROOT/RooFit/RooStats** - Via C++ engine and HS3 compatibility
- **PyHF** - Via Python engine
- **HS3** - As foundation and extension
- **Domain-specific frameworks** - Via MaaS protocol

---

## Success Criteria

Pillar 1 will be considered successful when:

✅ DEMOS standard specification is complete and versioned
✅ All three engines (C++, Python, Julia) support core primitives
✅ Cross-language tests demonstrate consistency
✅ At least 10 diverse models serialized using the standard
✅ MaaS protocol enables containerized model integration
✅ 70%+ test coverage for engine implementations
✅ Community feedback incorporated into specification

---

## Next Steps

Explore the detailed work packages:

- [WP1.1: Harmonizing Diverse Models →](wp1-1-harmonizing.md)
- [WP1.2: Engines →](wp1-2-engines.md)
- [WP1.3: Containers (MaaS) →](wp1-3-containers.md)
