---
title: WP2.3 - Interoperability
---

# WP2.3: Interoperability with Existing Infrastructure

**Lead Institution:** TUDO (TU Dortmund University)
**Timeline:** 2026.Q2 - 2028.Q1
**Person-Years:** 0.5

---

## Overview

The DEMOS portal **will not operate in isolation** but will build on and extend existing resources such as HEPData, Zenodo, and other domain-specific repositories. This work package ensures seamless integration with established infrastructure, enhancing rather than replacing existing platforms.

**Core Principle:** The DEMOS initiative does not plan to diminish or replace the use of existing infrastructure in any way. Rather, existing resources should be enhanced and leveraged.

---

## Key Objectives

1. **Enhance existing repositories** with standardized model access
2. **Establish machine-readable metadata** standards using DOI and UUID references
3. **Enable bidirectional integration** between DEMOS and external platforms
4. **Provide unified APIs** for black-box interaction with models
5. **Facilitate model discovery** across multiple repositories
6. **Ensure long-term preservation** through integration with archival services

---

## Target Platforms

### 1. HEPData

**Current Status:**
- Hosts particle physics experimental data
- ATLAS collaboration publishes likelihoods using HS3 and pyhf formats
- Multiple published models available (40+ with pyhf format)

**Integration Goals:**

✅ **Standardized Access**
- Provide tools to access HEPData-hosted models using DEMOS standard
- Convert existing HS3/pyhf models to DEMOS format
- Enable direct download and usage in DEMOS engines

✅ **Metadata Linkage**
- Link DEMOS registry entries to HEPData records via DOI
- Bidirectional references between platforms
- Synchronized metadata updates

✅ **Discovery Enhancement**
- HEPData models discoverable through DEMOS portal
- DEMOS LLM search includes HEPData records
- Unified search interface across both platforms

**Implementation Timeline:**
- **2026.Q2:** Machine-readable metadata field established
- **2027.Q1:** Full integration with model gallery and discovery

**Support:**
- Letter of endorsement from HEPData team (Dr. Graeme Watt, Durham University)
- Collaboration on tool development for HS3 standard integration

### 2. Zenodo

**Current Status:**
- General-purpose research data repository
- DOI assignment for datasets and code
- Long-term preservation commitment
- Used increasingly for model and code sharing

**Integration Goals:**

✅ **DOI-Based References**
- Every DEMOS model linked to Zenodo DOI (if available)
- Bidirectional citation linkage
- Credit assignment for model authors

✅ **Long-term Preservation**
- Models uploaded to both DEMOS and Zenodo
- Zenodo provides archival guarantee
- DEMOS registry points to Zenodo records

✅ **Automatic Synchronization**
- DEMOS submission triggers Zenodo upload (optional)
- Zenodo metadata synchronized to DEMOS
- Version tracking across both platforms

**Implementation Timeline:**
- **2026.Q2:** DOI linkage established
- **2027.Q1:** Full integration with automatic synchronization

**Support:**
- Letter of endorsement from Zenodo team (Lars Holm Nielsen, CERN IT Department)
- Collaboration on enhancing HS3 standard usability with Zenodo

### 3. Domain-Specific Repositories

**Additional Platforms:**

- **RODARE** (HZDR): Self-hosted platform for warm dense matter and laser physics models
- **GitHub/GitLab:** Code and model repositories from individual research groups
- **arXiv:** Pre-prints with supplementary model files
- **Collaboration websites:** ATLAS, CMS, LHCb, Belle II, BESIII, etc.

**Integration Approach:**
- Metadata harvesting where possible
- Manual curation for significant models
- Links from DEMOS to original sources
- Citation tracking

---

## Technical Implementation

### Machine-Readable Metadata Field (2026.Q2)

**Standard Metadata Schema:**

```json
{
  "demos_id": "uuid-12345",
  "external_references": {
    "hepdata": {
      "record_id": "ins2765432",
      "doi": "10.17182/hepdata.12345",
      "url": "https://hepdata.net/record/ins2765432"
    },
    "zenodo": {
      "record_id": "7654321",
      "doi": "10.5281/zenodo.7654321",
      "url": "https://zenodo.org/record/7654321"
    },
    "github": {
      "repo": "owner/repository",
      "commit": "abc123def456",
      "url": "https://github.com/owner/repository/tree/abc123"
    }
  },
  "publication": {
    "doi": "10.1103/PhysRevD.109.112006",
    "arxiv": "2401.12345",
    "inspire_id": "2750000"
  },
  "container": {
    "uuid": "container-uuid-67890",
    "registry": "docker.io",
    "image": "demos/model-12345:v1.0"
  }
}
```

**Key Features:**

- **DOI references** for publications and datasets
- **UUID references** for containerized models (MaaS)
- **Repository links** for code and supplementary materials
- **Version tracking** across platforms
- **Machine-readable** for automated tools
- **Human-readable** for documentation

### Unified API Architecture

**Goal:** Black-box interaction with MaaS container infrastructure regardless of hosting location.

**API Endpoints:**

```
# DEMOS Registry
GET /api/models/{id}
GET /api/models/{id}/file
GET /api/models/{id}/execute

# HEPData Integration
GET /api/hepdata/{record_id}
GET /api/hepdata/{record_id}/convert

# Zenodo Integration
GET /api/zenodo/{record_id}
GET /api/zenodo/{record_id}/download

# Container Execution
POST /api/models/{id}/run
  {
    "inputs": {...},
    "parameters": {...}
  }
```

**Capabilities:**

- **Discover models** across multiple repositories
- **Download models** from any platform
- **Execute models** via MaaS protocol
- **Combine models** from different sources
- **Track provenance** through metadata

### Conversion Tools

**Format Conversion:**

```python
# HS3 → DEMOS
convert_hs3_to_demos(hs3_file) → demos_file

# pyhf → DEMOS
convert_pyhf_to_demos(pyhf_json) → demos_file

# DEMOS → HS3 (where applicable)
convert_demos_to_hs3(demos_file) → hs3_file
```

**Use Cases:**

1. **Import existing models** from HEPData to DEMOS registry
2. **Export DEMOS models** to legacy formats for compatibility
3. **Cross-validate** models between formats
4. **Demonstrate equivalence** of different representations

---

## Collaboration Strategy

### HEPData Team

**Activities:**

- Regular meetings to coordinate integration
- Joint development of conversion tools
- Testing with existing ATLAS/CMS likelihoods
- Documentation of best practices
- Feedback on DEMOS standard improvements

**Benefits to HEPData:**

- Enhanced discoverability via LLM search
- Standardized model format reduces fragmentation
- Interactive exploration through Binder integration
- Broader community engagement

### Zenodo Team

**Activities:**

- Define DOI assignment workflow
- Implement metadata synchronization
- Test automatic upload functionality
- Ensure long-term preservation compliance
- Community outreach for adoption

**Benefits to Zenodo:**

- Structured models with rich metadata
- Increased usage for scientific models
- Integration with domain-specific portal
- Citation tracking and impact metrics

### Domain Communities

**Engagement:**

- Present DEMOS at collaboration meetings
- Offer training on model submission
- Provide support for model conversion
- Collect feedback on requirements
- Showcase successful examples

---

## Implementation Phases

### Phase 1: Foundation (2026.Q2 - 2026.Q4)

**Deliverables:**

- [ ] Machine-readable metadata schema finalized
- [ ] DOI linkage implemented in DEMOS registry
- [ ] Basic HEPData record lookup functional
- [ ] Zenodo API integration prototype

### Phase 2: Integration (2027.Q1 - 2027.Q2)

**Deliverables:**

- [ ] HEPData models integrated into gallery
- [ ] DEMOS discovery tool searches HEPData
- [ ] Zenodo automatic upload working
- [ ] Conversion tools for HS3/pyhf operational

### Phase 3: Enhancement (2027.Q3 - 2028.Q1)

**Deliverables:**

- [ ] Unified API for cross-repository access
- [ ] MaaS protocol supports external containers
- [ ] Bidirectional synchronization complete
- [ ] Documentation and training materials

---

## Coordination Role (TUDO)

TUDO will coordinate interoperability efforts by:

**1. Interface Design**
- Define common API specifications
- Establish metadata standards
- Create conversion tool requirements

**2. Community Engagement**
- Liaise with HEPData and Zenodo teams
- Coordinate with domain-specific repositories
- Facilitate collaboration across institutions

**3. Implementation Support**
- Provide technical guidance to partners
- Review and test integration code
- Ensure consistency across platforms

**4. Documentation**
- Write integration guides
- Create usage examples
- Maintain compatibility matrix

**5. Quality Assurance**
- Test cross-repository workflows
- Verify metadata consistency
- Monitor integration health

---

## ATLAS Collaboration Example

**Context:**

- ATLAS publishes likelihoods on HEPData using HS3 format
- Multiple analyses use sophisticated statistical models
- Models used for Higgs discovery, top quark measurements, BSM searches

**DEMOS Integration:**

1. **Discovery of Higgs Models (2026.Q3)**
   - Import 2012 Higgs discovery models from HEPData
   - Convert to DEMOS standard
   - Feature in model gallery as historical showcase
   - Enable interactive exploration

2. **Recent Analyses**
   - ttZ production measurements
   - Charge asymmetry studies
   - Same-charge top-quark pair searches
   - Import and standardize all published HS3 models

3. **Future Submissions**
   - Encourage ATLAS to publish directly in DEMOS format
   - Provide automatic HEPData submission from DEMOS
   - Ensure backward compatibility with existing tools

**Benefits to ATLAS:**

- Easier model sharing within collaboration
- Better visibility of published results
- Interactive exploration for education
- Long-term preservation and accessibility

---

## Timeline & Milestones

| Date | Milestone | Description |
|------|-----------|-------------|
| **2026.Q2** | Metadata standard | Machine-readable metadata field established |
| **2027.Q1** | Gallery integration | HEPData models in DEMOS gallery |
| **2027.Q1** | Discovery integration | DEMOS search includes external repositories |
| **2028.Q1** | Full API | Unified APIs for cross-repository access |

---

## Deliverables

### Software

- [ ] Metadata schema specification
- [ ] HEPData integration API
- [ ] Zenodo integration API
- [ ] Conversion tools (HS3, pyhf)
- [ ] Cross-repository search indexer

### Documentation

- [ ] Integration architecture guide
- [ ] API usage documentation
- [ ] Model submission workflow (multi-repository)
- [ ] Conversion tool documentation
- [ ] Best practices guide

### Partnerships

- [ ] Formal agreements with HEPData and Zenodo
- [ ] Regular coordination meetings
- [ ] Joint development sprints
- [ ] Shared roadmap

---

## Success Metrics

✅ 10+ models imported from HEPData to DEMOS
✅ All DEMOS models have DOI references (where applicable)
✅ Zenodo automatic upload functional
✅ DEMOS search returns HEPData results
✅ Conversion tools validated on 20+ models
✅ API response time <1 second for external queries
✅ Zero metadata inconsistencies between platforms

---

## Letters of Endorsement

### HEPData (Dr. Graeme Watt, Durham University)

> "On behalf of the HEPData team, we are pleased to support the 'DEMOS – Democratizing MOdelS' proposal submitted to the ErUM Data call of BMBF. We believe the proposed integration of the HS3 standard into HEPData strongly aligns with our shared goal of improving the accessibility and usability of public likelihoods for the high-energy physics community."

> "If this proposal is successfully funded, we look forward to collaborating with the DEMOS team to develop tools that enhance the integration and usability of the HS3 standard within HEPData."

### Zenodo (Lars Holm Nielsen, CERN IT Department)

> "On behalf of the Zenodo team, we are pleased to support the 'DEMOS - DEmocratizing MOdelS' proposal submitted to the ErUM Data call of BMBF. We believe the proposed integration of the HS3 standard with Zenodo strongly aligns with our shared goal of improving the accessibility and usability of public likelihoods in the Open Science community."

> "If this proposal is successfully funded, we look forward to collaborating with the DEMOS team to develop tools that enhance the integration and usability of the HS3 standard with Zenodo."

---

## Risk Mitigation

| Risk | Impact | Mitigation |
|------|--------|------------|
| API changes at external platforms | Medium | Version pinning, deprecation monitoring, fallback methods |
| Metadata schema divergence | High | Regular coordination meetings, shared specification |
| Legal/licensing conflicts | Medium | Clear attribution, open licenses, legal review |
| Platform availability issues | Low | Caching, local copies, graceful degradation |
| Community resistance | Medium | Early engagement, demonstrate benefits, gradual adoption |

---

## Connection to Project Goals

This work package directly supports the DEMOS mission by:

1. **Leveraging existing infrastructure** - Builds on established platforms
2. **Ensuring longevity** - Integration with archival services (Zenodo)
3. **Maximizing reach** - Models discoverable across multiple portals
4. **Respecting community practices** - Works with existing workflows
5. **Enhancing impact** - Broader visibility and citation tracking

---

## Next Steps

After exploring WP2.3:

- [Return to Pillar 2 Overview →](index.md)
- [WP2.1: Front-end Portal ←](wp2-1-frontend.md)
- [WP2.2: Back-end Registry & CI/CD ←](wp2-2-backend.md)
- [Explore Pillar 3: Community Engagement →](../pillar3/index.md)
