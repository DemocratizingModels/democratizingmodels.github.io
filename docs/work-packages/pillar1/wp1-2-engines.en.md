---
title: WP1.2 - Engines
---

# WP1.2: Engines

The implementation of the DEMOS standard involves developing **practical computational tools** to translate the standard into engines capable of processing and evaluating models effectively. This work package is crucial for maintaining the overall coherence of the project.

---

## Overview

Any new feature introduced into the modeling language standard will be accompanied by:

- Implementation in all three engines (C++, Python, Julia)
- Unit tests to validate properties
- Cross-language consistency checks
- Performance benchmarks

The engines ensure that the DEMOS standard is not just a specification on paper, but a living, usable tool for the research community.

---

## Why Three Languages?

The choice of **C++**, **Python**, and **Julia** reflects our expectations for the ErUM field's long-term trajectory:

### C++ Engine

**Rationale**:
- Integral role in frameworks like ROOT
- Performance advantages for computationally intensive tasks
- Strong presence in established research environments
- Essential for backward compatibility

**Key Users**: ATLAS, CMS, LHCb, Belle II, legacy analysis frameworks

### Python Engine

**Rationale**:
- Most widely used language in scientific computing today
- Extensive libraries prevalent in industry and academia
- Accessibility for diverse user backgrounds
- Easy prototyping and interactive exploration

**Key Users**: Modern analysis frameworks, machine learning pipelines, new users

### Julia Engine

**Rationale**:
- Forward-looking features (multiple dispatch, efficient numerics)
- Well-positioned for future research-oriented development
- Combines performance with ease of use
- Growing adoption in scientific computing

**Key Users**: Next-generation frameworks, performance-critical applications

---

## Unified Engine Structure

All three engines will follow a **common architectural pattern** with three main components:

### 1. Parsing and In-Memory Representation (2026.Q3)

**Functionality**:
- Read JSON files conforming to DEMOS standard
- Identify computational building blocks
- Detail their relationships and parameters
- Construct relational map of the model

**Technical Requirements**:
- Efficient JSON parsing
- Validation against schema
- Error handling and diagnostics
- Memory-efficient representation

### 2. Computational Building Blocks (2027.Q1)

**Implementation as Pluggable Modules**:
- Domain-specific extensions supported
- Consistent interface across blocks
- Type safety where applicable
- Performance optimization

**Categories of Blocks**:
- Probability distributions
- Mathematical operations
- Special functions
- Matrix/vector operations
- Complex number arithmetic
- Domain-specific functions

### 3. Materialization (2027.Q1)

**Translation of Lazy Computation Graph**:
- Instantiate correct building blocks
- Resolve dependencies
- Optimize execution paths
- Handle different computational backends

**Backend Support**:
- Native implementations
- Just-in-time compilation (where available)
- GPU acceleration (future consideration)
- Automatic differentiation support

---

## C++ Engine

**Lead**: TUDO
**Timeline**: 2027.Q1
**Base**: ROOT/RooFit HS3 framework

### Technical Approach

Building on the existing HS3 framework to minimize duplication while extending functionality:

- **JSON Parsing**: Already available via `RooJSONFactoryWSTool` (integrated into ROOT by TUDO)
- **RooFit Integration**: Leverage existing building blocks
- **Extension**: Add new structural components

### Key Challenges

#### Static Typing and Compilation

Supporting new structural components poses challenges due to:

- Strict typing requirements
- Compilation-time resolution
- Template instantiation complexity

**Examples of New Components**:
- Complex interfering amplitudes
- Matrix operations on arbitrary-sized matrices
- Vector-valued functions

#### Building Block Expansion

Numerous computational elements must be added:

- Functions beyond current RooFit set
- Distributions for specific domains
- Matrix/vector operations
- Complex number support

### JGU Contributions

**Responsibility**: Adding computational building blocks to ROOT/RooFit

**Specific Tasks**:
- Implement domain-specific functions
- Add new distribution types
- Extend RooFit functionality
- Test and validate implementations

### MaaS Protocol Support

Native support for communication protocol with containerized models:

- Client implementation for accessing remote models
- Server implementation for exposing C++ models
- Low-overhead binary I/O
- Cross-platform compatibility

---

## Python Engine

**Lead**: LMU (with TUM and SC)
**Timeline**: 2027.Q1
**Base**: PyHF expertise

### Technical Approach

#### In-Memory Representation

Managed in Python, leveraging its dynamic capabilities:

- Flexible data structures
- Easy introspection
- Interactive development
- Dynamic type system advantages

#### Building Blocks as Plugins

Using multiple computational backends:

- **JAX**: For just-in-time compilation and automatic differentiation
- **Numba**: For JIT compilation of numerical code
- **SymPy**: For symbolic computations

This multi-backend approach ensures:

- Performance optimization
- Flexibility in computation style
- Gradient computation for inference
- Symbolic manipulation when needed

#### Materialization Strategy

Join the lazy computation graph with chosen computational backends:

- Select optimal backend for each operation
- Minimize data movement
- Optimize execution order
- Support different inference methods

### Team Expertise

**Lorentz Gartner** (LMU PhD candidate):

- Perfect fit for the project
- Extensive Python development experience
- Timeline aligns with 3-year project (starting October 2025)
- Expertise in flavor physics and Belle II experiment
- Will pioneer connection between DEMOS standard and b-anomaly models

**TUM and SC Partners**:

- Lukas Heinrich (TUM): PyHF co-creator
- Giordon Stark (SC): PyHF maintenance
- Combined deep expertise in statistical modeling

### Integration with Existing Tools

The Python engine will seamlessly integrate with:

- PyHF models (HistFactory format)
- JAX ecosystem
- scikit-hep tools
- Jupyter notebooks
- Common Python analysis frameworks

---

## Julia Engine

**Leads**: HZDR, RUB-H, TUDO, MPP
**Timeline**: 2027.Q1
**Base**: Multiple pilot projects

### Foundation and Prototypes

#### Existing Work

- **HS3 Engine Prototype**: MSc project at TUDO and MPP (Robin Pelkner)
- **Amplitude Serialization**: Pilot project at RUB-H
- **Computational Graph Optimization**: Extensive work at HZDR (Anton Reinhard Diploma)

These prototypes demonstrate feasibility and inform design decisions.

### Technical Approach

Harness Julia's unique features:

#### Multiple Dispatch

- Natural representation of mathematical operations
- Type-based specialization
- Extensibility without modification
- Clean, readable code

#### Modular Package Ecosystem

**Separate packages for different concerns**:

- JSON parsing package
- In-memory representation package
- Computational building blocks packages (domain-specific)
- Meta-package integrating everything

**Benefits**:
- Independent development and versioning
- Easy extensibility by community
- Minimal dependencies per package
- Clear separation of concerns

#### Symbolic and Numerical Methods

Efficient combination of:

- Symbolic differentiation
- Numerical optimization
- Just-in-time compilation
- Native performance

### Design Priorities

1. **Extensibility**: Easy to add new building blocks
2. **Performance**: Native Julia speed
3. **Type Safety**: Leverage Julia's type system
4. **Interoperability**: Work well with other Julia packages

### Use Cases

Julia engine particularly well-suited for:

- Complex mathematical models
- Performance-critical calculations
- Research-oriented development
- Future framework development

---

## Cross-Language Consistency

### CI/CD-Based Validation (2027.Q4)

Comprehensive continuous integration system:

- **Automated Testing**: Every commit triggers tests
- **Cross-Language Tests**: Same models evaluated in all engines
- **Consistency Checks**: Numerical agreement verified
- **Performance Benchmarks**: Track regression

### Downstream Tests (2028.Q1)

**Test Suite Design**:

- Reference models with known outputs
- Tolerance specifications
- Edge case coverage
- Performance baselines

**Test Categories**:

1. **Parsing Tests**: Valid and invalid JSON
2. **Evaluation Tests**: Numerical accuracy
3. **Gradient Tests**: Automatic differentiation consistency
4. **Integration Tests**: Complete workflow validation

### Test Coverage Target

**Goal**: 70% code coverage by 2028.Q1

**Strategy**:
- Unit tests for individual building blocks
- Integration tests for workflows
- Regression tests for bug fixes
- Domain-specific validation tests

---

## Standard Software Development Practices

All engines will follow:

### Version Control

- Git repositories (GitHub/GitLab)
- Semantic versioning
- Tagged releases
- Changelog maintenance

### Documentation

- API documentation (auto-generated)
- User guides
- Examples and tutorials
- Development guides

### Code Quality

- Linting and formatting tools
- Code review requirements
- Style guide adherence
- Dependency management

### Testing Infrastructure

- Unit test frameworks
- Integration test suites
- Continuous integration
- Coverage reporting

---

## Performance Considerations

### Optimization Strategies

Different engines employ different approaches:

#### C++ Optimization

- Template metaprogramming
- Compile-time optimizations
- SIMD vectorization
- Efficient memory management

#### Python Optimization

- JIT compilation (JAX, Numba)
- Vectorized operations (NumPy)
- Cython for critical paths
- Lazy evaluation

#### Julia Optimization

- Native just-in-time compilation
- Type specialization
- Automatic optimization
- LLVM backend

### Benchmarking

Regular performance monitoring:

- Execution time tracking
- Memory usage profiling
- Comparison across engines
- Regression detection

---

## Interoperability and Conversion

### Cross-Engine Model Transfer

Models serialized in DEMOS standard can be:

- Loaded in any engine
- Evaluated consistently
- Combined across languages
- Extended in any framework

### Conversion Tools

**From Existing Formats**:

- PyHF JSON → DEMOS (LMU)
- HS3 → DEMOS (TUDO)
- ROOT workspaces → DEMOS (TUDO)
- Domain-specific formats → DEMOS (various)

**To Other Formats** (when useful):

- DEMOS → visualization formats
- DEMOS → documentation formats
- DEMOS → legacy formats (for compatibility)

---

## Joint Development Benefits

### Shared Infrastructure

All engine teams benefit from:

- Common test suite
- Shared benchmarks
- Design pattern exchange
- Problem-solving collaboration

### Best Practices Sharing

- Code review across teams
- Architecture discussions
- Performance optimization techniques
- Bug fix propagation

### Consistent Progress

Even distribution of person-power ensures:

- No single point of failure
- Multiple validation sources
- Diverse perspective integration
- Reduced risk of delays

---

## Risk Mitigation

### Identified Risk: Delayed Engine Delivery

**Risk**: Potential delays in delivering fully functional stack for one engine

**Impact Assessment**: Limited - would not significantly affect overall project

**Mitigation**:

1. **Alternative Stacks Available**: Other engines serve as validation
2. **Phased Delivery**: Core functionality prioritized
3. **Cross-Team Support**: Teams assist each other
4. **Regular Progress Reviews**: Early detection of issues

### Other Risks and Mitigations

| Risk | Mitigation |
|------|-----------|
| Incompatible language features | Early prototyping, standard design flexibility |
| Performance bottlenecks | Profiling, optimization, alternative backends |
| Dependency conflicts | Minimal dependencies, version management |
| Maintenance burden | Clear code, documentation, community engagement |

---

## Personnel Allocation

**Total**: 2.05 person-years

### By Engine

- **C++ Engine**: 0.15 py + 0.2 py (JGU) = 0.35 py
- **Python Engine**: 0.7 py
- **Julia Engine**: 0.4 py + 0.2 py + 0.1 py + 0.2 py = 0.9 py

### By Institution

- **TUDO**: 0.15 py (C++ lead)
- **JGU**: 0.2 py (C++ building blocks)
- **LMU**: 0.7 py (Python lead)
- **HZDR**: 0.4 py (Julia contributions)
- **RUB-H**: 0.1 py (Julia prototype)
- **TUDO**: 0.2 py (Julia HS3 prototype)
- **MPP**: 0.2 py (Julia HS3 prototype)
- **TUM**: 0.1 py (Python support)

---

## Milestones

### M3: Engines Support Nested Constructions (2027.Q1)

All three engines can:
- Parse complex DEMOS models
- Instantiate nested structures
- Evaluate probability distributions
- Handle domain-specific primitives

### M7: Validation and Testing Complete (2028.Q1)

- CI/CD pipeline operational
- Cross-language tests passing
- 70%+ test coverage achieved
- Performance benchmarks established

---

## Deliverables Summary

### By 2026.Q3

- ✓ Parsing components implemented
- ✓ In-memory representations designed
- ✓ Basic JSON validation working

### By 2027.Q1

- ✓ All three engines support nested models
- ✓ Core building blocks implemented
- ✓ Materialization working
- ✓ Basic examples functional

### By 2027.Q4

- ✓ CI/CD-based validation operational
- ✓ Comprehensive test suites in place
- ✓ Domain-specific blocks added

### By 2028.Q1

- ✓ Cross-language downstream tests passing
- ✓ 70% test coverage achieved
- ✓ Performance optimization complete
- ✓ Documentation published

---

## Long-Term Maintenance

### Sustainability Strategy

- Clear governance model
- Community contribution guidelines
- Regular release schedule
- Backward compatibility policy
- Deprecation procedures

### Community Engagement

- Developer mailing list
- GitHub/GitLab issue tracking
- Contribution guidelines
- Code of conduct
- Regular developer meetings

---

## Integration with Other Work Packages

### Inputs From

- **WP1.1**: Standard specification, primitives catalog
- **WP3.2**: Real models for testing
- **WP2.2**: Validation requirements

### Outputs To

- **WP1.3**: Engines include MaaS client/server functionality
- **WP2.1**: Engines power interactive exploration
- **WP2.2**: Engines used in validation pipelines
- **WP3.1**: Engines demonstrated in tutorials
- **WP3.2**: Engines evaluate showcase models

---

## Success Criteria

WP1.2 will be successful when:

✅ All three engines fully implement DEMOS standard
✅ Cross-language numerical consistency demonstrated
✅ CI/CD pipeline ensures continued compatibility
✅ Test coverage exceeds 70%
✅ Performance meets or exceeds existing tools
✅ Documentation enables independent use
✅ Community adoption begins
✅ Domain-specific models successfully evaluated

---

## Next Steps

- Learn about [WP1.3: Containers (MaaS) →](wp1-3-containers.md) for complex model support
- Review [WP1.1: Harmonizing →](wp1-1-harmonizing.md) to see how the standard is defined
- Return to [Pillar 1 Overview →](index.md)
