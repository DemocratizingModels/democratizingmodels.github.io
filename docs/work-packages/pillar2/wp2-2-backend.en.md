---
title: WP2.2 - Back-end Registry & CI/CD
---

# WP2.2: Back-end: Model Registry and Continuous Integration

**Lead Institution:** HZDR (Helmholtz-Zentrum Dresden-Rossendorf)
**Timeline:** 2026.Q4 - 2028.Q1
**Person-Years:** 0.7

---

## Overview

The back-end of the platform acts as the **connection point between the front-end and the database** storing the model files. It is the central backbone, performing actions on newly included models and providing access points for requesting models from the database.

The back-end infrastructure ensures:

- **Quality control** through automated validation
- **Reproducibility** through versioning and checksums
- **Accessibility** through well-defined APIs
- **Sustainability** through CI/CD automation
- **Scalability** through enterprise-level technologies

---

## Core Components

### 1. Model Registry (2026.Q4)

A repository for dedicated metadata of each model, connecting the model identifier with the actual model file.

**Purpose:**
- Central management of included models
- Metadata storage and indexing
- Version tracking
- DOI and UUID mapping
- Search index generation

**Data Structure:**

```json
{
  "model_id": "uuid-string",
  "name": "B+ → K+ νν̄ BELLE II 2024",
  "doi": "10.1103/PhysRevD.109.112006",
  "version": "1.0.0",
  "domain": "particle_physics",
  "collaboration": "Belle II",
  "file_location": "s3://demos/models/belle2_bknn.json",
  "checksum": "sha256:abc123...",
  "reference_points": "tests/belle2_bknn_refs.json",
  "metadata": {
    "tags": ["B-meson", "rare-decay", "neutrino"],
    "search_keywords": ["..."],
    "citations": ["..."]
  },
  "validation_status": "approved",
  "submission_date": "2024-11-05",
  "last_updated": "2024-11-05"
}
```

**Technology:**
- **GitHub** as hosting platform (version control, issues, pull requests)
- Alternative: **Invenio** framework (being evaluated)
- JSON-based registry files
- Git history for versioning

### 2. Three-Step Model Inclusion Process

#### Step 1: Validation (2028.Q1)

**Automated Checks:**

1. **Integrity Validation**
   - Checksum verification (SHA-256)
   - JSON schema validation
   - File format compliance
   - Dependency checking

2. **Correctness Validation**
   - Reference point testing
   - Expected outputs verification
   - Numerical stability checks
   - Cross-engine consistency (optional)

**Manual Review:**

1. **Relevance Assessment**
   - Scientific significance
   - Appropriate for DEMOS scope
   - Proper documentation
   - Citation completeness

2. **Safety Review**
   - No malicious code
   - No sensitive data
   - No copyright violations
   - Compliance with licenses

#### Step 2: Pre-processing

**Metadata Enrichment:**

- Extract metadata from model file (if available)
- Add storage-specific information
- Generate search indices and keywords
- Link DOI references
- Assign UUID if not present

**Automated Tasks:**

- Generate model visualizations
- Create thumbnail images
- Extract parameter lists
- Compute model statistics
- Build documentation links

#### Step 3: Insertion

**Registry Update:**

- Add model entry to registry
- Update search indices
- Link to existing resources (HEPData, Zenodo)
- Trigger front-end deployment

**Storage:**

- Copy model file to database (or)
- Create reference to external storage
- Update CDN/cache if applicable

### 3. Application Programming Interface (API) (2028.Q1)

RESTful API for services to communicate with the model registry and interact with model files.

**Endpoints:**

```
GET    /api/models              # List all models
GET    /api/models/{id}         # Get specific model
POST   /api/models              # Submit new model (authenticated)
PUT    /api/models/{id}         # Update model metadata
DELETE /api/models/{id}         # Remove model (admin only)

GET    /api/models/search?q={query}  # Search models
GET    /api/models/filter?domain=particle_physics&tag=rare-decay

GET    /api/models/{id}/file    # Download model file
GET    /api/models/{id}/metadata  # Get metadata only
GET    /api/models/{id}/validate  # Trigger validation
GET    /api/models/{id}/visualize # Get visualization
```

**Authentication:**
- API keys for authenticated operations
- OAuth integration for user accounts
- Rate limiting for public access
- Admin privileges for moderation

**Documentation:**
- OpenAPI/Swagger specification
- Interactive API explorer
- Code examples in multiple languages
- Client libraries (Python, Julia, C++)

---

## CI/CD Infrastructure

### GitHub Actions Based Pipeline (2028.Q1)

**Triggers:**

- Pull request opened/updated
- Merge to main branch
- Manual workflow dispatch
- Scheduled validation runs

**Workflow Steps:**

```yaml
name: Model Validation Pipeline

on:
  pull_request:
    paths:
      - 'models/**'

jobs:
  validate:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v3

      - name: Validate JSON schema
        run: python scripts/validate_schema.py

      - name: Check integrity
        run: python scripts/check_checksums.py

      - name: Run reference tests
        run: python scripts/test_references.py

      - name: Generate visualizations
        run: python scripts/generate_viz.py

      - name: Report results
        run: python scripts/report_to_frontend.py
```

**Validation Tools:**

- **Schema Validator:** Ensures JSON conforms to DEMOS standard
- **Checksum Verifier:** Validates file integrity
- **Reference Tester:** Runs model with known inputs, checks outputs
- **Visualization Generator:** Creates plots and diagrams
- **Coverage Reporter:** Tracks which models have been validated

**Status Reporting:**

- CI/CD results posted to pull request
- Status badges generated
- Validation reports stored
- Front-end notified of results

### Continuous Deployment

**Automated Deployment:**

- Approved models → Registry update
- Registry update → Database sync
- Database sync → Cache invalidation
- Cache invalidation → Front-end refresh

**Rollback Capability:**

- Git history enables version rollback
- Failed deployments auto-revert
- Manual override for emergencies

---

## Technical Stack

### Backend Technologies

```
┌──────────────────────────────────────────┐
│         GitHub/GitLab                    │
│  • Model registry (JSON files)          │
│  • Pull request workflows               │
│  • GitHub Actions (CI/CD)               │
└──────────────────────────────────────────┘
              ↓
┌──────────────────────────────────────────┐
│      Validation Services                 │
│  • Schema validators                     │
│  • Reference test runners               │
│  • Checksum verifiers                   │
│  • Visualization generators             │
└──────────────────────────────────────────┘
              ↓
┌──────────────────────────────────────────┐
│         Database/Storage                 │
│  • Model files (JSON)                    │
│  • Metadata (indexed)                    │
│  • Visualizations (generated)            │
│  • Test results (cached)                 │
└──────────────────────────────────────────┘
              ↓
┌──────────────────────────────────────────┐
│           API Layer                      │
│  • REST endpoints                        │
│  • Authentication                        │
│  • Rate limiting                         │
│  • CDN integration                       │
└──────────────────────────────────────────┘
```

### Programming Languages

- **Python:** Validation scripts, API server, automation
- **Bash/Shell:** GitHub Actions workflows
- **YAML:** Configuration files
- **JSON:** Registry and model files

---

## HZDR Experience

### Existing Infrastructure

**QEDjl-project:**
- Small-scale version of CI/CD system already operational at HZDR
- Automated testing and validation pipelines
- Continuous deployment workflows
- Provides foundation for DEMOS backend

**Expertise:**
- Enterprise-level software development
- High-performance computing infrastructure
- Data management and archiving
- Automated testing frameworks

---

## Model Storage Options

### Option 1: GitHub-based Storage

**Advantages:**
- Integrated with registry
- Built-in version control
- Free for public repositories
- Familiar to developers

**Disadvantages:**
- File size limits (100 MB per file)
- Large binary files problematic
- Bandwidth limitations

**Best for:** Text-based JSON models, small datasets

### Option 2: Dedicated Database

**Advantages:**
- No file size limits
- Optimized for queries
- Better scalability
- CDN integration

**Disadvantages:**
- Additional infrastructure cost
- More complex setup
- Maintenance overhead

**Best for:** Large models, high-traffic scenarios

### Option 3: Hybrid Approach

**Registry on GitHub + Files in Object Storage**

- Registry metadata in GitHub
- Large model files in S3/MinIO
- Best of both worlds
- Links in registry point to storage

**Recommended approach**

---

## Validation Tool Development (2028.Q1)

### Validation Script Suite

**1. Schema Validator**
```python
def validate_schema(model_file):
    """Validate model against DEMOS JSON schema"""
    schema = load_demos_schema()
    model = load_json(model_file)
    validate(model, schema)  # Raises error if invalid
```

**2. Integrity Checker**
```python
def verify_integrity(model_file, expected_checksum):
    """Verify file has not been corrupted"""
    actual = compute_sha256(model_file)
    assert actual == expected_checksum
```

**3. Reference Tester**
```python
def test_references(model_file, reference_file):
    """Run model with known inputs, check outputs"""
    model = load_model(model_file)
    refs = load_references(reference_file)

    for ref in refs:
        result = model.evaluate(ref.inputs)
        assert_close(result, ref.expected, rtol=1e-5)
```

**4. Visualization Generator**
```python
def generate_visualizations(model_file):
    """Create plots for model gallery"""
    model = load_model(model_file)

    # Structure diagram
    generate_structure_plot(model)

    # Parameter distributions
    generate_parameter_plot(model)

    # Output predictions (if applicable)
    generate_output_plot(model)
```

### Test Coverage Tracking

**Goal:** 70%+ test coverage for engine implementations

**Metrics:**
- Percentage of building blocks tested
- Percentage of models validated
- Reference point coverage
- Cross-engine consistency rate

**Reporting:**
- Coverage badges in repository
- Trend analysis over time
- Per-domain coverage breakdown

---

## Timeline & Milestones

| Date | Milestone | Description |
|------|-----------|-------------|
| **2026.Q4** | Registry established | Model registry operational on GitHub |
| **2027.Q4** | CI/CD basic | Automated validation pipelines functional |
| **2028.Q1** | Validation complete | Full validation tool suite operational |
| **2028.Q1** | API deployed | REST API publicly accessible |
| **2028.Q1** | 70% coverage | Engine tests cover 70%+ of functionality |

---

## Deliverables

### Software

- [ ] Model registry infrastructure (GitHub-based)
- [ ] CI/CD pipeline configurations (GitHub Actions)
- [ ] Validation tool suite (Python)
- [ ] REST API server (Python/FastAPI)
- [ ] API client libraries (Python, Julia, C++)

### Documentation

- [ ] Backend architecture documentation
- [ ] API reference (OpenAPI)
- [ ] Validation criteria guide
- [ ] CI/CD workflow documentation
- [ ] Model submission guidelines

### Infrastructure

- [ ] GitHub organization and repositories
- [ ] Automated testing environment
- [ ] API hosting (cloud deployment)
- [ ] Monitoring and logging
- [ ] Backup and disaster recovery

---

## Success Metrics

✅ Model registry contains 3+ models per ErUM domain (18+ total)
✅ CI/CD validates 90%+ of submissions without manual intervention
✅ API uptime >99%
✅ API response time <500ms (p95)
✅ Validation suite covers 70%+ of engine functionality
✅ Zero critical security vulnerabilities
✅ Comprehensive documentation (>90% coverage)

---

## Collaboration Points

### Internal (DEMOS Project)

- **WP2.1 (RUB-H):** API specification for front-end integration
- **WP2.3 (TUDO):** Metadata standards, DOI handling
- **WP1.2:** Engine validation interfaces
- **WP3.2:** Model submission from showcases

### External

- **GitHub:** Platform provider, Actions infrastructure
- **QEDjl-project:** Existing CI/CD patterns at HZDR
- **HEPData/Zenodo:** Metadata exchange standards

---

## Risk Mitigation

| Risk | Impact | Mitigation |
|------|--------|------------|
| GitHub limitations | Medium | Evaluate Invenio alternative, hybrid storage |
| CI/CD resource costs | Medium | Optimize workflows, cache results, prioritize tests |
| API scaling issues | High | Load balancing, CDN, rate limiting |
| Validation false negatives | High | Multiple validation methods, manual review |
| Security vulnerabilities | Critical | Regular audits, automated scanning, responsible disclosure |

---

## Evaluation: GitHub vs Invenio

### GitHub (Current Choice)

**Pros:**
- Familiar to developers
- Free for open source
- Built-in CI/CD (Actions)
- Excellent version control
- Community features (issues, PRs)

**Cons:**
- File size limits
- Less flexible for complex metadata
- Limited query capabilities

### Invenio (Alternative)

**Pros:**
- Purpose-built for research data
- Flexible metadata handling
- Advanced search capabilities
- DOI integration built-in
- Used by Zenodo

**Cons:**
- More complex setup
- Hosting costs
- Maintenance overhead
- Learning curve

**Decision:** Start with GitHub, evaluate Invenio if limitations arise

---

## Connection to Project Goals

This work package directly supports the DEMOS mission by:

1. **Ensuring quality** - Automated validation maintains standard compliance
2. **Enabling trust** - Checksums and reference tests ensure reproducibility
3. **Facilitating access** - RESTful API enables programmatic model retrieval
4. **Supporting sustainability** - CI/CD automation reduces maintenance burden
5. **Promoting transparency** - Open registry and validation results

---

## Next Steps

After exploring WP2.2, continue to:

- [WP2.3: Interoperability →](wp2-3-interoperability.md)
- [Return to Pillar 2 Overview →](index.md)
- [WP2.1: Front-end Portal ←](wp2-1-frontend.md)
