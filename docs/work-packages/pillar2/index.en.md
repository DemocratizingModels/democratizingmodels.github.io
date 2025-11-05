---
title: Pillar 2 - Portal & Infrastructure
---

# Pillar 2: Portal & Infrastructure

The second key component of the initiative is the development of a **robust and scalable digital infrastructure** to facilitate the discovery, validation, and sharing of models across disciplines. This portal will act as a centralized hub where researchers can access models, contribute new ones, and interact with tools and resources that support interdisciplinary collaboration.

---

## Overview

Pillar 2 focuses on creating a comprehensive digital ecosystem comprising:

1. **Front-end Portal** - User-facing interface for model discovery and exploration
2. **Back-end Registry** - Model management, validation, and CI/CD infrastructure
3. **Interoperability** - Integration with existing research data platforms (HEPData, Zenodo)

The portal will provide researchers easy access to computational models, enabling simple integration into their workflows. Furthermore, the infrastructure will leverage existing research data platforms and repositories, integrating into the scientific ecosystem without duplicating hardware investments.

---

## Work Packages

### WP2.1: Front-end Portal

The front-end provides an intuitive interface for exploring, discovering, and documenting physics models. Features include a model gallery, LLM-powered discovery, interactive JavaScript visualization, and Binder integration for live execution.

**Lead:** RUB-H

[Learn more →](wp2-1-frontend.md)

### WP2.2: Back-end Registry & CI/CD

The back-end acts as the connection between the front-end and the model database. It provides a model registry, automated validation pipelines using GitHub Actions, and RESTful APIs for model access.

**Lead:** HZDR

[Learn more →](wp2-2-backend.md)

### WP2.3: Interoperability

Integration with existing infrastructure including HEPData, Zenodo, and domain-specific repositories. Establishment of machine-readable metadata standards with DOI and container UUID references.

**Lead:** TUDO

[Learn more →](wp2-3-interoperability.md)

---

## Key Objectives

The objectives of Pillar 2 are to:

1. **Democratize access** to research models through an intuitive web portal
2. **Automate validation** using CI/CD pipelines
3. **Enable discovery** through LLM-powered search capabilities
4. **Ensure interoperability** with existing data repositories
5. **Support live interaction** via Binder and federated compute resources
6. **Maintain quality** through automated testing and review workflows

---

## Timeline

| Milestone | Quarter | Description |
|-----------|---------|-------------|
| **M2** | 2026.Q4 | Portal deployed, model registry established, basic constructions documented |
| **M5** | 2027.Q3 | Domain-specific building blocks documented, gallery features 10+ examples |
| **M7** | 2028.Q1 | Uploading/validation working with CI tools, engine tests at 70%+ |
| **M8** | 2028.Q2 | Language model determines tags, LLM search operational |

---

## Personnel Allocation

Total person-years for Pillar 2: **2.5 years**

| Work Package | Person-Years | Lead Institution |
|--------------|--------------|------------------|
| WP2.1 Front-end | 1.0 | RUB-H |
| WP2.2 Back-end | 0.7 | HZDR |
| WP2.3 Interoperability | 0.5 | TUDO |
| Project Management | 0.3 | Distributed |

---

## Technical Architecture

### Front-end Stack

- **Framework:** React.js for modularity and scalability
- **Visualization:** JavaScript engine for parsing nested models
- **Search:** LLM-powered discovery using RAG (Retrieval Augmented Generation)
- **Execution:** Binder integration with mybinder.org and FAIRUM resources
- **API:** REST APIs for real-time metadata retrieval

### Back-end Stack

- **Version Control:** GitHub/GitLab for model registry
- **CI/CD:** GitHub Actions for automated validation
- **Database:** Model files linked to or stored in dedicated database
- **API:** RESTful interfaces for model access and operations
- **Validation:** Automated integrity (checksum) and correctness (reference points) checks

### Integration Points

- **HEPData:** Direct linkage for particle physics likelihoods
- **Zenodo:** DOI-based references and long-term preservation
- **GitHub/GitLab:** Pull/merge request workflows for submissions
- **FAIRUM:** Federated compute resources for interactive sessions

---

## Expected Outcomes

### Platform Deliverables

1. **Public Web Portal**
   - Responsive, user-friendly interface
   - Model gallery with curated examples
   - Search functionality (keyword + LLM-powered)
   - Interactive visualization of model structure
   - Link to GitHub/GitLab for submissions

2. **Model Registry**
   - Centralized metadata repository
   - UUID-based model identification
   - DOI integration for citations
   - Version tracking
   - Search indices

3. **CI/CD Infrastructure**
   - Automated validation pipelines
   - Checksum verification
   - Reference point testing
   - Performance visualization generation
   - Status reporting to front-end

4. **Integration Tools**
   - HEPData connector
   - Zenodo linker
   - GitHub Actions workflows
   - API documentation

### Documentation

- Platform user guide
- Model submission guidelines
- API reference documentation
- Integration examples
- Best practices for model preparation

---

## Consortium Contributions

### Leading Roles

- **RUB-H** - Front-end development, portal design, LLM integration
- **HZDR** - Back-end infrastructure, CI/CD pipelines, registry
- **TUDO** - Interoperability, HEPData/Zenodo integration, coordination

### Supporting Roles

- **TUM** - Binder integration, FAIRUM collaboration
- **LMU, SC** - Model validation examples
- **MPP** - Containerization support
- **JGU** - AmpTools integration testing

---

## Integration with Existing Infrastructure

The portal **does not replace** existing infrastructure. Instead, it:

✅ **Enhances** HEPData with standardized model access
✅ **Leverages** Zenodo for long-term preservation
✅ **Extends** GitHub/GitLab workflows for submissions
✅ **Connects** existing repositories through unified APIs
✅ **Enriches** metadata through machine-readable standards

Letters of endorsement from HEPData and Zenodo teams confirm support for this integration approach.

---

## User Journey

### Model Discovery

1. User visits portal and searches for models (keyword or natural language)
2. LLM-powered search returns relevant models with summaries
3. User browses model gallery with visualizations
4. User views detailed metadata, DOI, and documentation

### Model Exploration

1. User selects a model of interest
2. JavaScript visualization displays model structure
3. User clicks "Run in Binder" for interactive exploration
4. Session connects to mybinder.org or FAIRUM resources
5. User executes and modifies model in live notebook

### Model Submission

1. User prepares model in DEMOS format
2. User submits via GitHub/GitLab pull/merge request
3. CI/CD pipeline validates submission automatically
4. Manual review addresses relevance and safety
5. Approved model appears in portal with generated metadata

---

## Technical Challenges & Solutions

### Scalability

**Challenge:** Validation feedback loop resource consumption
**Solution:** Careful resource allocation, prioritized testing, caching strategies

### LLM Costs

**Challenge:** API costs for language model queries during development
**Solution:** Budget allocation (requested), exploration of GWDG/KISSKI consortium partnership for Llama 3.1 70B access

### Latency

**Challenge:** Interactive session startup time
**Solution:** FAIRUM collaboration for federated resources with reduced latency

### Maintenance

**Challenge:** Long-term platform sustainability
**Solution:** CI-based maintenance pipelines, community governance (Pillar 3)

---

## Success Criteria

Pillar 2 will be considered successful when:

✅ Portal is publicly accessible and responsive
✅ Model registry contains 3+ models per ErUM domain
✅ LLM-powered search delivers relevant results
✅ CI/CD validates models automatically (70%+ test coverage)
✅ Interactive Binder sessions launch successfully
✅ HEPData and Zenodo integration operational
✅ API documentation complete and usable
✅ User feedback surveys show positive satisfaction

---

## Connection to Other Pillars

**Pillar 1 (Format)** → Provides the DEMOS standard that the infrastructure implements
**Pillar 2 (Infrastructure)** → Provides the platform for sharing and discovery
**Pillar 3 (Community)** → Drives adoption and populates the registry with models

---

## Next Steps

Explore the detailed work packages:

- [WP2.1: Front-end Portal →](wp2-1-frontend.md)
- [WP2.2: Back-end Registry & CI/CD →](wp2-2-backend.md)
- [WP2.3: Interoperability →](wp2-3-interoperability.md)
