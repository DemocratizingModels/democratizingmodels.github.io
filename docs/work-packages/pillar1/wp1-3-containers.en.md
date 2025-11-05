---
title: WP1.3 - Containers (Models as a Service)
---

# WP1.3: Containers - Models as a Service (MaaS)

Even with a thorough and wide model standard, there will be limits to its capacity across complexity, languages, and operating systems. This work package addresses models that require **specialized code, data, or computational resources** through a containerization and service-oriented approach.

---

## Overview: The MaaS Concept

**Models as a Service (MaaS)** enables models that cannot be directly serialized to participate in the DEMOS ecosystem by:

- Running them in separate processes
- Communicating through a standard protocol
- Keeping model code independent from analysis code
- Combining multiple models with varied software requirements

This approach leverages two proven technologies:

1. **Well-defined communication protocols** - For long-term systems compatibility
2. **Software containerization** - For portability and reproducibility

---

## When to Use MaaS

### Models Requiring MaaS

MaaS is appropriate for models that:

- **Use complex custom code** not easily serializable
- **Depend on legacy software** with specific version requirements
- **Require specialized data** not easily distributed
- **Need specific computational resources** (GPUs, large memory, clusters)
- **Have intricate machine learning components** with framework dependencies
- **Access proprietary or licensed software**
- **Use unusual programming languages** not covered by core engines

### Native vs. MaaS Decision

The decision tree:

1. **Can the model be expressed in DEMOS primitives?** → Use native serialization
2. **Is it simple custom code in C++/Fortran?** → Use lightweight MaaS wrapper
3. **Is it complex with many dependencies?** → Use full containerization
4. **Does it need specific infrastructure?** → Use remote MaaS hosting

---

## Communication Protocols

### Communication Modes

MaaS supports multiple communication patterns:

#### Local Communication (Inter-Process)

- Same machine, different processes
- Low latency
- No network overhead
- Easy debugging

#### Distributed Communication

- **MPI**: Message Passing Interface for HPC clusters
- **IP Network**: Standard TCP/IP for remote services
- **HTTP/REST**: For web-accessible services

### Protocol Requirements

The MaaS protocol must support:

- **Density calculations**: P(x|parameters)
- **Random data generation**: Sampling from distributions
- **Data access**: Retrieve pre-computed datasets
- **Metadata queries**: Model information and capabilities
- **Parameter updates**: Modify model parameters
- **Gradient computation**: Where applicable

---

## Protocol Definition (2026.Q4)

**Lead**: MPP

### Survey of Existing Standards

A comprehensive survey will evaluate:

- **Data serialization formats**: Protocol Buffers, MessagePack, FlatBuffers, Cap'n Proto
- **RPC frameworks**: gRPC, Apache Thrift, ZeroMQ
- **Requirements**: Minimal dependencies, cross-language compatibility, low overhead

### Selected Approach

Criteria for selection:

1. **Minimal dependencies**: Easy to implement in any language
2. **Binary efficiency**: Low overhead for numerical data
3. **Cross-language support**: Works with C++, Python, Julia, Fortran
4. **Mature and stable**: Battle-tested in production
5. **Open source**: Free to use and modify

### Protocol Specification

The formal definition will include:

- **Message formats**: Binary structure specifications
- **Communication patterns**: Request-response, streaming
- **Error handling**: Standardized error codes and messages
- **Versioning**: Protocol evolution strategy
- **Authentication**: Security considerations (optional)

---

## UUID-Based Referencing Scheme

### Motivation

Models hosted via MaaS need unique, persistent identifiers:

- **Universally Unique**: No central coordination required
- **Persistent**: Stable across model versions
- **Resolvable**: Can locate the service endpoint
- **Citable**: Enable proper attribution

### UUID Structure

**Format**: Standard UUID v4 with extensions

```json
{
  "type": "maas_reference",
  "uuid": "550e8400-e29b-41d4-a716-446655440000",
  "endpoint": "https://models.example.org/uuid",
  "version": "1.2.3",
  "checksum": "sha256:...",
  "metadata": {
    "doi": "10.1234/example",
    "description": "...",
    "authors": ["..."]
  }
}
```

### Registry Integration

MaaS models will be registered in the DEMOS registry with:

- UUID as primary identifier
- Endpoint URLs for access
- Metadata for discovery
- Health status monitoring
- Version history

---

## Implementation in Engines

### Client and Server Functionality

**Each DEMOS engine** (C++, Python, Julia) will include:

#### Client Side

- Connect to MaaS services
- Send requests following protocol
- Receive and process responses
- Handle errors and retries
- Cache results when appropriate

#### Server Side

- Wrap custom models for MaaS
- Listen for requests
- Execute model calculations
- Return formatted responses
- Log usage and errors

This bidirectional support means:

- Any engine can **access** MaaS models
- Any engine can **wrap custom models** as MaaS services

---

## Lightweight C/C++ MaaS-Server Library (2027.Q1)

**Leads**: MPP and TUDO

### Motivation

Legacy C/C++ and Fortran models represent a significant portion of existing research code. A lightweight library enables their integration with minimal modification.

### Design Principles

- **Minimal dependencies**: Standard C/C++ library only
- **Simple API**: Few functions to implement
- **Clear documentation**: Easy for non-experts
- **Example templates**: Copy-paste starting points
- **Fortran bindings**: Via ISO C binding

### Example Usage

```cpp
#include "demos_maas.h"

// User implements these functions
double my_model_density(const double* x, const double* params);
void my_model_sample(double* x, const double* params);

int main() {
    DemosMaaSServer server;
    server.register_density(my_model_density);
    server.register_sampler(my_model_sample);
    server.serve(); // Listen for requests
}
```

### Features

- Automatic protocol handling
- Multi-threading support
- Basic error handling
- Logging capabilities
- Configuration via JSON

---

## Containerization Strategy

### Why Containers?

Containers provide:

- **Isolation**: No conflicts with host environment
- **Reproducibility**: Exact software environment preserved
- **Portability**: Run anywhere containers are supported
- **Versioning**: Immutable images with version tags
- **Distribution**: Standard registries (Docker Hub, etc.)

### Container Technologies

**Primary**: Docker/Podman

- Industry standard
- Excellent tooling
- Large ecosystem
- Good documentation

**Alternative**: Singularity/Apptainer

- Popular in HPC environments
- Better for multi-user systems
- Compatible with Docker images

### Container Best Practices

1. **Minimal base images**: Reduce size and attack surface
2. **Multi-stage builds**: Separate build and runtime environments
3. **Version pinning**: Explicit dependency versions
4. **Security scanning**: Identify vulnerabilities
5. **Documentation**: Clear README and usage instructions

---

## Use Cases

### Neutrino Oscillation Models (TUM Lead)

**Challenge**: Complex detector response, varied flux models

**Approach**:

- Containerize neutrino oscillation calculators
- Equip with MaaS protocol
- Deploy to computing infrastructure
- Enable seamless integration in analyses

**Benefits**:

- Consistent environment across institutions
- Easy updates and versioning
- Reduced local setup burden
- Reproducible results

### Astroparticle Models (RUB-A)

**Challenge**: Large-scale Monte Carlo simulations, 3D propagation

**Models to Containerize**:

- CRPropa cosmic ray propagation
- Source distribution models
- Particle interaction codes

**Scale**: 10^4 to 10^6 CPU hours per simulation

**MaaS Advantages**:

- Run on appropriate infrastructure
- Cache expensive computations
- Share results across collaborations
- Preserve exact software versions

### Nuclear Physics Models (RUB-N)

**Challenge**: Multi-gigabyte data files, complex matrix element generation

**Models to Containerize**:

- Three-nucleon force calculations
- Matrix element generators
- Basis transformation codes

**MaaS Benefits**:

- Centralized data management
- Computational resources co-located with data
- Consistent numerical precision
- Reduced local storage requirements

---

## Domain-Specific Adaptations

### MPP Contributions (Decay Chains)

The MPP group will pioneer MaaS adaptation for:

- Hadron decay chain models
- Complex partial-wave formalisms
- Covariant tensor formalism implementations

**Specific Example**: τ⁻ → π⁻π⁻π⁺ντ decay model (Belle II)

- Uses unusual covariant tensor formalism
- Limited framework support
- Ideal MaaS candidate (2028.Q1)
- Native implementation delayed
- Containerized version enables immediate use
- Cross-validation when native version ready

### Warm-Dense-Matter Models (HZDR)

**Domain-Specific Interface** (2028.Q3):

Challenge: Extensive analyses require many structure-factor models simultaneously

Solution: Automated model serving infrastructure

- Upload new structure-factor calculations
- Automatic containerization
- Registry integration
- Immediate availability via MaaS

Applications:

- Inertial confinement fusion studies
- XFEL experiments at HiBEF
- Path-integral Monte Carlo results
- TDDFT simulation outputs

---

## Infrastructure Requirements

### Hosting Infrastructure

Models may be hosted:

1. **Locally**: User's machine via container
2. **Institutionally**: Department/lab servers
3. **Nationally**: Federated computing resources
4. **Internationally**: Collaboration-wide services

### Resource Management

Considerations:

- **Load balancing**: Distribute requests
- **Scaling**: Add capacity as needed
- **Monitoring**: Track usage and health
- **Costs**: Who pays for compute/storage?

### Governance

Questions to address:

- Who can register MaaS models?
- Quality assurance process?
- Resource allocation policies?
- Long-term hosting commitments?

---

## Performance Considerations

### Latency vs. Execution Time

MaaS introduces communication overhead:

- **Acceptable**: When execution time >> latency (typically > 100ms)
- **Problematic**: For very fast models (< 10ms execution)
- **Mitigation**: Batch requests, local caching

### Optimization Strategies

1. **Binary I/O**: Efficient serialization
2. **Compression**: For large data transfers
3. **Caching**: Store repeated calculations
4. **Batching**: Send multiple evaluations at once
5. **Parallel execution**: Multiple workers

### Benchmarking

Performance will be measured:

- Round-trip latency
- Throughput (requests/second)
- Scalability (vs. number of workers)
- Comparison with native implementations

---

## Security and Privacy

### Security Considerations

For public-facing MaaS services:

- **Authentication**: Who can access?
- **Authorization**: What operations allowed?
- **Rate limiting**: Prevent abuse
- **Input validation**: Sanitize requests
- **Audit logging**: Track usage

### Privacy Considerations

Models may contain:

- Proprietary algorithms
- Unpublished data
- Competitive research
- Privacy-sensitive information

**Solutions**:

- Private container registries
- Access control lists
- Institutional hosting
- Confidentiality agreements

---

## Development Timeline

### Phase 1: Protocol Definition (2026.Q4)

- Survey existing standards
- Design MaaS protocol
- Write specification document
- Implement reference library

### Phase 2: Engine Integration (2027.Q1)

- Add MaaS client to all engines
- Add MaaS server to all engines
- Develop C/C++ lightweight library
- Create example implementations

### Phase 3: Use Case Development (2027-2028)

- **TUM**: Neutrino oscillation models
- **RUB-A**: Cosmic ray propagation
- **RUB-N**: Nuclear force models
- **MPP**: Decay chain models
- **HZDR**: Structure-factor interface

### Phase 4: Production Deployment (2028)

- Operational hosting infrastructure
- Monitoring and maintenance
- Documentation complete
- Community training

---

## Milestones

### M4: MaaS Protocol Working (2027.Q2)

- Protocol formally defined
- UUIDs generated
- Basic client/server functional
- Example containers available

### M7: Integration Complete (2028.Q1)

- All engines support MaaS
- Lightweight C/C++ library ready
- First production services deployed
- Validation against native implementations

### M10: Production Services (2028.Q3)

- At least 3 containerized models per domain
- Robust hosting infrastructure
- Usage monitoring operational
- Community adoption demonstrated

---

## Personnel Allocation

**Total**: 0.65 person-years

### By Institution

- **MPP**: 0.35 py (lead, protocol, decay models)
- **TUM**: 0.1 py (neutrino models)
- **RUB-A**: 0.1 py (astroparticle models)
- **RUB-N**: 0.1 py (nuclear models)

---

## Deliverables Summary

### Technical Deliverables

1. **MaaS Protocol Specification**
   - Binary message formats
   - Communication patterns
   - Error handling
   - Versioning strategy

2. **Reference Implementations**
   - Python client/server
   - C++ client/server
   - Julia client/server
   - Lightweight C/C++ library

3. **Container Templates**
   - Dockerfile examples
   - Configuration templates
   - Deployment scripts
   - Health check utilities

4. **Documentation**
   - Protocol specification
   - User guides
   - Developer guides
   - Best practices

5. **Example Models**
   - Neutrino oscillations (TUM)
   - Cosmic ray propagation (RUB-A)
   - Nuclear forces (RUB-N)
   - Decay chains (MPP)
   - Structure factors (HZDR)

---

## Integration with Other Work Packages

### Dependencies

- **WP1.1**: Standard must describe MaaS referencing
- **WP1.2**: Engines must implement client/server
- **WP2.2**: Registry must support MaaS models

### Contributions To

- **WP2.1**: MaaS models in gallery
- **WP2.2**: Validation of containerized models
- **WP3.1**: Documentation and tutorials
- **WP3.2**: Showcase complex domain models

---

## Success Criteria

WP1.3 will be successful when:

✅ MaaS protocol formally defined and documented
✅ All three engines support MaaS client and server
✅ Lightweight C/C++ library enables easy wrapping
✅ At least 5 production MaaS services operational
✅ Performance overhead acceptable (< 2x vs. native)
✅ Container templates available for common scenarios
✅ Community members deploy their own MaaS models
✅ Cross-validation with native implementations successful

---

## Long-Term Vision

The MaaS approach ensures:

### Preservation

Legacy models remain accessible even as:

- Programming languages evolve
- Dependencies become obsolete
- Operating systems change
- Hardware architectures shift

### Flexibility

Researchers can:

- Use best tool for each component
- Combine models across languages
- Leverage specialized infrastructure
- Update models independently

### Scalability

The system supports:

- Simple models to complex simulations
- Local execution to distributed computing
- Single users to large collaborations
- Current and future computational paradigms

### Sustainability

Long-term maintenance is feasible:

- Clear interface boundaries
- Isolated dependencies
- Independent versioning
- Documented protocols

---

## Risks and Mitigation

| Risk | Impact | Mitigation |
|------|--------|-----------|
| Network latency too high | Poor user experience | Caching, batching, local containers |
| Container security vulnerabilities | Potential exploits | Scanning, updates, access controls |
| Hosting infrastructure costs | Unsustainable operation | Shared resources, institutional support |
| Protocol evolution issues | Compatibility breaks | Careful versioning, deprecation policies |
| Complex setup burden | Low adoption | Templates, automation, documentation |

---

## Conclusion

WP1.3 - MaaS extends the reach of DEMOS beyond what can be natively serialized, ensuring that:

- **Complex models** are not excluded
- **Legacy code** remains valuable
- **Specialized infrastructure** can be leveraged
- **Future technologies** can be accommodated

By combining containerization with a well-defined protocol, MaaS provides a **sustainable, flexible, and powerful** mechanism for including the full diversity of research models in the DEMOS ecosystem.

---

## Next Steps

- Review [WP1.1: Harmonizing →](wp1-1-harmonizing.md) to see how the standard is defined
- Explore [WP1.2: Engines →](wp1-2-engines.md) to understand native implementations
- Return to [Pillar 1 Overview →](index.md)
