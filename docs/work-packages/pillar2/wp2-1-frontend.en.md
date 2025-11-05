---
title: WP2.1 - Front-end Portal
---

# WP2.1: Front-end Portal, Model Gallery, and Language Interface

**Lead Institution:** RUB-H (Ruhr University Bochum - Hadron Physics)
**Timeline:** 2026.Q2 - 2028.Q2
**Person-Years:** 1.0

---

## Overview

The front-end of the proposed portal plays a central role in **democratizing access** to research models within the ErUM domain by providing an intuitive and accessible interface for exploring, discovering, and documenting physics models. This interface will integrate seamlessly with back-end systems, showcasing both individual models and curated examples, and providing advanced LLM-powered search capabilities.

---

## Key Features

### 1. Model Portal (2026.Q2)

A responsive, user-friendly web application that consolidates critical resources:

- **Comprehensive Model View**
  - Extended metadata display
  - Model structure visualization
  - Documentation and references
  - DOI links for citations
  - Related models and building blocks

- **Technical Implementation**
  - Built with **React.js** framework for modularity and scalability
  - REST API integration with back-end systems
  - Real-time retrieval of model metadata
  - Dynamic visualization updates
  - Mobile-responsive design

- **User Experience**
  - Accessible interface for diverse backgrounds
  - Clear navigation and search functionality
  - Filtering by domain, complexity, tags
  - Model comparison capabilities

### 2. Model Gallery (2026.Q3)

A curated showcase of exemplary models with rich visualizations:

- **Visual Presentations**
  - Performance metrics visualization
  - Computed outputs and predictions
  - Model structure diagrams
  - Parameter sensitivity plots
  - Uncertainty quantification displays

- **Dynamic Content**
  - Back-end generated visualizations
  - Interactive plots and figures
  - Execution statistics
  - Validation results

- **Curation**
  - Featured models from each domain
  - High-impact research examples
  - Educational demonstrations
  - Complex model showcases

### 3. JavaScript Visualization Engine (2026.Q2)

An interactive tool for exploring model structure:

- **Capabilities**
  - Parse DEMOS JSON format
  - Display nested model syntax graphically
  - Show dataflow graph structure
  - Highlight building blocks and connections
  - Export visualizations

- **Interactive Features**
  - Zoom and pan functionality
  - Node expansion/collapse
  - Hover tooltips with details
  - Parameter inspection
  - Dependency tracking

### 4. LLM-Powered Discovery Tool (2028.Q2)

Natural language search functionality powered by large language models:

- **Technology**
  - **Retrieval Augmented Generation (RAG)** mechanism
  - AI agents for metadata analysis
  - Automatic tag generation
  - Summary creation
  - Similarity matching

- **User Capabilities**
  - Natural language queries (e.g., "Find models for B meson decays with charm quarks")
  - Semantic search beyond keywords
  - Context-aware recommendations
  - Cross-domain discovery

- **Infrastructure**
  - Cooperation with **GWDG/KISSKI consortium**
  - Access to **Llama 3.1 70B** model
  - API cost budget allocation for development
  - Experience from RUB GPT@RUB project (serving thousands of users)

### 5. Interactive Execution - Binder Integration (2027.Q3)

Enable users to execute models in live computational environments:

- **mybinder.org Integration**
  - "Run in Binder" button for each model
  - Automatic notebook generation
  - Lightweight computation support

- **FAIRUM Collaboration**
  - Connection to national federated resources (collaboration with ErUM-Data FAIRUM project)
  - Large-scale computation support
  - Greatly reduced latency
  - Enhanced computational capacity
  - Joint development between RUB-H and TUM teams

- **User Experience**
  - One-click execution environment
  - Pre-configured dependencies
  - Example notebooks
  - Interactive parameter exploration
  - Result visualization

---

## Technical Architecture

### Front-end Stack

```
┌─────────────────────────────────────────────┐
│          React.js Application               │
├─────────────────────────────────────────────┤
│  Components:                                │
│  • Search Interface (keyword + LLM)         │
│  • Model Gallery                            │
│  • Model Detail Pages                       │
│  • JavaScript Visualization Engine          │
│  • Binder Integration                       │
└─────────────────────────────────────────────┘
              │
              ↓ REST API
┌─────────────────────────────────────────────┐
│         Back-end Services                   │
├─────────────────────────────────────────────┤
│  • Model Registry                           │
│  • Metadata Database                        │
│  • Visualization Generator                  │
│  • LLM Service (RAG)                        │
└─────────────────────────────────────────────┘
              │
              ↓
┌─────────────────────────────────────────────┐
│      External Integrations                  │
├─────────────────────────────────────────────┤
│  • GitHub/GitLab (submissions)              │
│  • mybinder.org (execution)                 │
│  • FAIRUM (compute resources)               │
│  • GWDG/KISSKI (LLM API)                    │
└─────────────────────────────────────────────┘
```

### Data Flow

1. **Model Discovery**
   - User query → Front-end → LLM service → Model registry → Results
   - Metadata + visualizations returned to front-end

2. **Model Exploration**
   - User selects model → Front-end fetches details
   - JavaScript engine parses JSON → Renders structure
   - Visualization API provides computed outputs

3. **Interactive Execution**
   - User clicks "Run in Binder"
   - Front-end generates Binder link
   - Session launches on mybinder.org or FAIRUM
   - User interacts with live notebook

---

## GitHub/GitLab Integration

### Submission Workflow

The front-end provides **links and status updates** while GitHub/GitLab handles the actual submission process:

1. User prepares model in DEMOS format
2. Portal provides submission guidelines and template
3. User submits via **GitHub pull request** or **GitLab merge request**
4. CI/CD pipelines trigger automatically (WP2.2)
5. Front-end displays submission status and validation results
6. Approved models appear in gallery

**Key Point:** No bespoke review interface needed - leverages existing GitHub/GitLab workflows

### Status Tracking

- Link to submission PR/MR
- CI/CD pipeline status badges
- Validation results display
- Review comments integration
- Merge/approval notifications

---

## LLM-Powered Search Implementation

### Automatic Enrichment

When new models are submitted, AI agents:

1. Analyze model metadata and documentation
2. Generate descriptive tags automatically
3. Create human-readable summaries
4. Identify related models
5. Extract key features and parameters

### Search Capabilities

**Keyword Search:**
```
Input: "Higgs boson discovery"
Output: Models tagged with Higgs, LHC, 2012, discovery
```

**Semantic Search:**
```
Input: "How do neutrinos change flavor as they travel?"
Output: Neutrino oscillation models, mixing matrices,
        matter effects, MSW effect
```

**Cross-domain Discovery:**
```
Input: "Statistical methods for rare event searches"
Output: Models from particle physics, neutrino physics,
        dark matter searches
```

### Technology Stack

- **RAG Framework:** Retrieval from model metadata + LLM generation
- **LLM Model:** Llama 3.1 70B (via GWDG/KISSKI)
- **Vector Database:** For efficient similarity search
- **Embeddings:** Model descriptions and metadata vectorized
- **API:** Integration with front-end search interface

---

## Scalability Considerations

### Critical Concerns

**Validation Feedback Loop:**
- CI/CD execution for visualization generation
- Potential resource bottleneck
- Requires careful resource allocation

**Solutions:**
- Prioritized testing (fast tests first)
- Caching of visualization results
- Incremental validation
- Resource quotas per submission
- Queue management for CI/CD jobs

---

## Development Experience

### RUB-H Team Expertise

**Previous Work:**
- **amplitude-serialization project:** Prototype for hadron three-body decay models
  - Demonstrates technical capacity
  - Explores feasibility of different solutions
  - Provides foundation for DEMOS portal

**GPT@RUB Project:**
- Experience providing frontier LLM access
- Serves thousands of RUB students and employees
- Infrastructure and scaling knowledge
- User interface design experience

**Collaboration:**
- GWDG/KISSKI consortium partnership investigated
- Access to Llama 3.1 70B via API
- Budget for development and testing phase

---

## Timeline & Milestones

| Date | Milestone | Description |
|------|-----------|-------------|
| **2026.Q2** | Portal deployed | Public web interface accessible |
| **2026.Q2** | JS visualization | Model structure visualization working |
| **2026.Q3** | Model gallery | 10+ curated examples displayed |
| **2027.Q3** | Binder integration | Interactive execution operational |
| **2028.Q2** | LLM search | Natural language model discovery |

---

## Deliverables

### Software Components

- [ ] React.js web application (open source)
- [ ] JavaScript visualization engine
- [ ] LLM search interface
- [ ] Binder integration module
- [ ] API client libraries

### Documentation

- [ ] User guide for portal navigation
- [ ] Model submission guidelines
- [ ] Visualization engine API docs
- [ ] Search query examples
- [ ] Binder usage instructions

### Content

- [ ] Model gallery with 10+ examples by 2027.Q3
- [ ] Documentation for domain-specific building blocks
- [ ] Tutorial notebooks
- [ ] Video demonstrations

---

## Success Metrics

✅ Portal receives 100+ unique visitors per month
✅ Model gallery features 10+ diverse examples
✅ LLM search returns relevant results (>80% user satisfaction)
✅ Binder sessions launch successfully (>90% success rate)
✅ User feedback surveys show positive experience (>4/5 average rating)
✅ JavaScript visualization renders complex models correctly
✅ Response time <2 seconds for search queries

---

## Collaboration Points

### Internal (DEMOS Project)

- **WP2.2 (HZDR):** REST API specification, CI/CD status integration
- **WP2.3 (TUDO):** HEPData/Zenodo links, metadata standards
- **WP3.1:** Documentation content, tutorials
- **WP3.2:** Showcase models for gallery

### External

- **FAIRUM Project:** Federated compute resources for Binder
- **GWDG/KISSKI:** LLM API access
- **mybinder.org:** Execution environment infrastructure
- **GitHub/GitLab:** Submission and review workflows

---

## Risk Mitigation

| Risk | Impact | Mitigation |
|------|--------|------------|
| LLM API costs exceed budget | Medium | Partnership with GWDG/KISSKI, open-source model fallback |
| Binder resource limitations | Medium | FAIRUM collaboration, resource quotas |
| CI/CD overload | High | Prioritized testing, caching, queue management |
| User adoption slow | Medium | Pillar 3 outreach, workshops, documentation |
| Technical debt accumulation | Medium | Code reviews, refactoring sprints, CI testing |

---

## Connection to Project Goals

This work package directly supports the DEMOS mission to **democratize models** by:

1. **Lowering barriers** - Intuitive interface accessible to all researchers
2. **Enabling discovery** - LLM search helps users find relevant models
3. **Facilitating exploration** - Interactive visualization and Binder execution
4. **Promoting transparency** - Open display of model structure and metadata
5. **Encouraging collaboration** - GitHub/GitLab workflows foster community contribution

---

## Next Steps

After exploring WP2.1, continue to:

- [WP2.2: Back-end Registry & CI/CD →](wp2-2-backend.md)
- [WP2.3: Interoperability →](wp2-3-interoperability.md)
- [Return to Pillar 2 Overview →](index.md)
