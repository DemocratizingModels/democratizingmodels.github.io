# WP 3.2: Showcasing

## Overview

The adoption and success of the modeling standard heavily rely on the availability of clear, practical examples that demonstrate its versatility and usability. Showcasing representative models from a broad range of fields, experiments, and theory serves multiple critical purposes:

- **Identifies standard features:** Use cases drive the development of necessary primitives and structures
- **Demonstrates scientific capacity:** Shows how the standard addresses specific research challenges
- **Provides serialization templates:** Examples serve as blueprints for future model encoding
- **Establishes collaboration standards:** Creates patterns for interdisciplinary model exchange

Providing these examples and curating them into a central gallery is a highly important task contributed by all consortium groups alongside their technical duties.

## Consortium Leadership Positions

Consortium members hold strategic leadership positions in major experimental collaborations, enabling effective promotion and adoption of the DEMOS standard:

- **ATLAS and CMS:** TUDO, LMU, TUM
- **LHCb and COMPASS:** RUB-H
- **BES III:** JGU
- **Belle II:** MPP
- **Neutrino Experiments:** TUM, RUB-A (KamLAND, MINOS, Daya Bay, IceCube)
- **Condensed Matter and Strong-Field QED:** HZDR

## Showcase Models by Domain

### Hadron Physics

Hadron physics provides a rich testing ground for the DEMOS standard and will benefit enormously from the common language it provides.

#### LHCb Collaboration (RUB-H)

**Scope:** As of 2024, LHCb has published 750 papers with ~20% performing partial-wave analysis. Of these analyses, 20% are of high interest to the community and should be included in the database.

**Priority Models (2027.Q3):**

1. **Pentaquark Discovery - Pcc̄**
   - Analysis: Λ⁰ᵦ → J/ψK⁻p cascade decays [Phys. Rev. Lett. 115, 072001 (2015)]
   - Significance: Discovery of iconic pentaquarks
   - Complexity: Cascade decay structures, exotic hadron states

2. **Λ⁺c → pK⁻π⁺ Decays**
   - Analysis: Amplitude analysis with modeling uncertainty quantification [Phys. Rev. D 108, 012023 (2023)]
   - Significance: Demonstrates proper reporting of modeling uncertainty with 18 alternative models
   - Complexity: Multiple systematic variations, uncertainty propagation

3. **χc1(3872) Lineshape**
   - Analysis: Detailed lineshape study [Phys. Rev. D 102, 092005 (2020)]
   - Significance: Exotic meson structure analysis
   - Complexity: Complicated lineshape parameterizations

4. **T⁺cc Tetraquark**
   - Analysis: Doubly charmed tetraquark study [Nature Commun. 13, 3351 (2022)]
   - Significance: Discovery of tetraquark state
   - Complexity: Novel lineshape encoding for exotic states

5. **Tetraquark States Tcs and Tc̄s̄**
   - Analysis: B → DDπ and B → DDK amplitude models [Phys. Rev. D 102, 112003 (2020); Phys. Rev. D 108, 012017 (2023)]
   - Significance: Observation of tetraquark states, led by IHEP (China) - increases stakeholder buy-in
   - Complexity: Multi-body decay chains with exotic resonances

#### COMPASS Experiment (RUB-H, MPP)

**Priority Models (2027.Q4):**

**Light Meson Production:** Flagship analyses for diffractively produced final states where COMPASS provides world-leading results:

1. **π⁻p → π⁻π⁻π⁺p at 190 GeV/c**
   - Reference: [Phys. Rev. D 98, 092003 (2018)]
   - Significance: Light isovector resonances
   - Cross-experiment applicability: Same final states studied at GlueX (photoproduction) and in heavy-meson/τ decays at BES III and Belle II

2. **ηπ⁻ and η'π⁻ Partial Waves**
   - Reference: [Phys. Lett. B 740, 303 (2015)]
   - Significance: Odd and even partial wave decomposition
   - Complexity: Multi-channel analysis

3. **Strange-Meson Spectroscopy**
   - Reference: [Nuovo Cim. C 47, 149 (2024)]
   - Significance: K-meson resonance structure

4. **Advanced Partial-Wave Methods**
   - Reference: [Nuovo Cim. C 47, 204 (2024)]
   - Significance: Methodological advances in PWA

**Impact:** Providing COMPASS models in DEMOS standard will foster easy comparison and exchange among GlueX, BES III, and Belle II experiments.

#### Belle II (MPP)

**τ⁻ → π⁻π⁻π⁺ντ Partial-Wave Model (2028.Q1):**

- Analysis: Ongoing study using covariant tensor formalism
- Reference: [17th International Workshop on Tau Lepton Physics, 2024]
- Significance:
  - Uses unusual partial-wave formalism implemented in limited frameworks
  - Ideal testbed for containerized MaaS format
- Strategy: Initial containerization with delayed native implementation, enabling cross-validation

**B Meson Decay Models:**

1. **B⁺ → K⁺νν̄ Decays**
   - Reference: [Phys. Rev. D 109, 112006 (2024)]
   - Significance: Flavor physics at precision frontier
   - Complexity: Simple parametric distributions with binned histogram structure
   - Format: Currently in HistFactory JSON, will be transformed using LMU conversion tools

2. **B → J/ψKπ Amplitude Model (MPP)**
   - Significance: Analytic parameterization with rich resonance structure
   - Application: Important input for Wilson coefficients C₉ and C₁₀ in B⁰ → K*⁰μ⁺μ⁻ decays
   - Cross-experiment: Connects to LHCb B⁰ → K*⁰μ⁺μ⁻ analysis

#### BES III (JGU)

**Priority Models:**

1. **Zc(3900) Spin-Parity Determination (First Priority)**
   - Reference: [Phys. Rev. Lett. 110, 252001 (2013)] - Most cited BES III analysis
   - Process: e⁺e⁻ → J/ψπ⁺π⁻ with J/ψ → ℓ⁺ℓ⁻
   - Significance:
     - High-profile example for model preservation
     - Exotic hadron Zc(3900) missing from LHCb and Belle II B → KJ/ψπ analyses
     - Demonstrates potential for cross-experiment collaboration
   - Complexity: Sufficiently complex to serve as ideal showcase

2. **Vector Charmonium Resonances**
   - References: World-leading datasets and advanced modeling [multiple papers]
   - Applications:
     - Event generation for γp → Zc(3900)p at Jefferson Lab energy upgrade
     - Precise lineshapes for weak b → sℓ⁺ℓ⁻ decay studies
   - Cross-experiment: D-meson decay measurements crucial for CKM matrix studies at LHCb and Belle II

**AmpTools Integration (JGU):**
- Pioneer C++ implementation of DEMOS standard engine using AmpTools framework
- **AmpTools:** Cross-experiment library for unbinned maximum likelihood fits developed at Indiana University
- **Used by:** BES III, GlueX collaborations
- **Impact:** Integration facilitates inter-experiment collaboration and ensures hadron physics models are readily available for GlueX and upcoming GSI projects

#### B-Factory Models (LMU, RUB-H)

**B → K(*)ℓℓ̄ Transitions:**

Major class of models in flavor physics, flagship efforts at Belle II, LHCb, and BaBar:

1. **B⁰ → K*⁰μ⁺μ⁻ Full Amplitude Model**
   - Reference: [JHEP 09, 026 (2024)] - LHCb comprehensive analysis
   - Significance: Most complex end of spectrum with local and nonlocal amplitudes
   - Personnel: LMU domain expertise in statistical modeling + RUB-H amplitude constructions
   - Demonstrates: Flexibility and extensibility of DEMOS standard

### Particle Physics

#### ATLAS Higgs Discovery Models (TUDO)

**Priority Model (2026.Q3):**

**Higgs Boson Discovery Models (2012):**
- References: [Phys. Lett. B 716, 1 (2012); Science 338, 1576 (2012)]
- Purpose:
  - Education and historical documentation
  - Testament to power and longevity of the standard
  - Document of the history of science
- Significance: Models that facilitated one of the most important discoveries in particle physics

### Nuclear Physics

#### Two-Nucleon (NN) Interactions (RUB-N)

**Focus:** NN interactions providing dominant contributions to nuclear structure and low-energy reactions

**Model Development Process:**
1. Derive NN potentials from effective chiral Lagrangian up to specified EFT expansion order
2. Introduce suitable ultraviolet regulator
3. Determine low-energy constants through global partial-wave analysis of np and pp scattering data
4. Perform error analysis and quantify truncation uncertainty

**Available Models:**
- Reference: [Eur. Phys. J. A 54, 86 (2018); Phys. Rev. Lett. 126, 092501 (2021)]
- **Five EFT expansion orders** at various cutoff values
- **Isospin-breaking corrections** from QED contributions and quark mass differences
- **First statistically perfect description** of NN scattering data within chiral EFT framework

**Deliverables:**

Comprehensive package including:
- **Model files:** NN potentials at different orders and cutoffs
- **Documentation:** Detailed theoretical background and usage guides
- **Application examples:** Benchmark results
- **Uncertainty quantification resources:**
  - Covariance matrices for low-energy constants (LECs)
  - Samples of models with randomly chosen higher-order interactions for truncation error quantification
- **Database:** Up-to-date, mutually consistent NN scattering data

**Matrix Elements:**
- **NN forces:** Codes generate matrix elements dynamically ("on-the-fly") in Fortran or Python
- **3N forces:** Significantly more complex, data files can exceed tens of gigabytes
- **Sharing mechanism:** Currently via direct requests; DEMOS will standardize access

### Neutrino Physics

#### IceCube Oscillation Models (TUM)

**Data Release:**
- Led by TUM (Eller)
- Process: Prepared and publicized data releases for IceCube's oscillation analyses
- Challenge: No predefined format existed; decisions made ad hoc
- Required: Navigation of internal approval process, facilitated by PI's established position

**Containerized Oscillation Models (2027.Q2):**
- Models equipped with MaaS protocol
- Enables seamless deployment and integration into diverse infrastructures
- Format: Containerization for models requiring specialized code or resources

#### Global Neutrino Oscillation Fits (TUM)

**Re-implemented Likelihoods:**
- References: [Phys. Rev. D 109, 095016 (2024); arXiv:2407.xxxxx (2024)]
- Based on public data from multiple experiments
- Demonstrates: Model combination across different experiments

#### Neutrinoless Double-Beta Decay (MPP)

**Combined Analysis Model (2027.Q3):**
- Reference: [Phys. Rev. D 106, 073004 (2022)]
- Data sources: GERDA and MAJORANA experiment data releases
- Additional inputs: Published likelihoods from cosmology and neutrino oscillation experiments
- Significance: Showcase for DEMOS standard expressing and combining statistical models from different domains

### Astroparticle Physics

#### Cosmic Ray and Multi-Messenger Models (RUB-A)

**Focus:** Particle propagation and observable spectra under specific assumptions

**Model Variety:** Diverse sources, particle types, and representations (parametric histograms to analytic formulations)

**Priority Models:**

1. **γ-rays from Jets (NGC 1068)**
   - Reference: [Astron. Astrophys. 687, A139 (2024)]
   - Type: Seyfert II galaxy emission

2. **Cosmic-Ray Transport in Central Molecular Zone**
   - Reference: [Astrophys. J. 965, 180 (2024)]
   - Features: Anisotropic diffusion modeling

3. **Cosmic-Ray Electrons in M51**
   - Reference: [Astron. Astrophys. 669, A111 (2023)]
   - Method: Synchrotron radiation analysis in face-on galaxy

4. **AGN Corona and Starburst Emissions**
   - Reference: [Astrophys. J. 939, 43 (2022)]
   - Type: Multimessenger model of non-thermal emission

5. **Galactic Center Magnetic Field**
   - Reference: [Astron. Astrophys. 644, A71 (2020)]
   - Features: Analytical model linking cosmic-ray propagation to γ-ray observations

**CRPropa Models:**
- Code maintained by international collaboration (~20 researchers)
- User base: 100+ researchers
- Applications: Theoretical studies and observational analyses with Auger and IceCube
- Similar codes: GALPROP, DRAGON, CORSIKA
- Complexity: Single runs can require 10⁴ to 10⁶ CPU hours

### Laser Physics and Warm Dense Matter

#### Strong-Field QED Models (HZDR)

**Differential Cross-Section Models (2027.Q3):**

At least three models for fundamental scattering processes:
- Electron beams with high-intensity lasers
- Reference: [Phys. Rev. D 60, 092004 (1999)]
- Framework: Feynman diagram approach with laser field effects

**Vacuum Birefringence Models (2028.Q3):**

Two models demonstrating vacuum birefringence:
- References: [Opt. Commun. 267, 318 (2006); arXiv:2405.18063 (2024)]
- Validation: Through Monte Carlo simulations
- Development: Interdisciplinary conjunction with MPP decay-chain models

#### Warm-Dense-Matter Structure Factors (HZDR)

**Priority Models (2028.Q3):**

At least three structure-factor-based models for X-ray probing:

1. **Chihara Decomposition Model**
   - Reference: [Nature 618, 270 (2023)]
   - Application: Pressure-driven K-shell delocalization

2. **Path-Integral Monte Carlo Derived Models**
   - Reference: [arXiv:2402.19113 (2024), submitted to Nature Comm.]
   - Focus: Electronic correlations in warm dense quantum plasmas

3. **TDDFT Simulation Models**
   - Reference: [Phys. Rev. Lett. 116, 115004 (2016)]
   - Method: Time-dependent density-functional theory without Chihara decomposition

**Domain-Specific Interface (2028.Q3):**
- Automated addition and serving of structure-factor models
- **Requirement:** Mandatory for extensive analyses involving many models simultaneously
- **Application:** Foundation for research on inertial confinement fusion
- **Integration:** With platforms at HZDR and HiBEF

**Model Templates Include:**
- Detailed mathematical formulations
- Kinematic mappings
- Input-output configurations
- Merging procedures for multiple models

## Success Metrics

By 2028.Q3, the gallery will contain:

- **At least 3 models per domain** (7 domains × 3 = 21+ models minimum)
- **Diversity:** Simple parametric to complex cascade decays
- **Coverage:** Experimental and theoretical models
- **Documentation:** Each model with detailed metadata, references, and usage examples
- **Validation:** Reference points and benchmark results
- **Accessibility:** Interactive exploration through portal

## Personnel Effort

Showcasing is a major collaborative effort:

| Group | Domain | Effort (FTE) |
|-------|--------|--------------|
| HZDR | Laser Physics | 0.37 |
| JGU | Hadron Physics | 0.27 |
| LMU | Particle Physics | 0.2 |
| MPP | Neutrino/Hadron | 0.35 |
| RUB-A | Astroparticle | 0.37 |
| RUB-N | Nuclear | 0.37 |
| RUB-H | Hadron Physics | 0.37 |
| TUM | Neutrino/Particle | 0.3 |
| TUDO | Particle | 0.15 |

## Impact

The showcase models will:

1. **Drive standard development:** Real use cases identify needed features
2. **Demonstrate capabilities:** Show DEMOS can handle diverse, complex models
3. **Enable cross-domain collaboration:** Common format allows unprecedented model comparison
4. **Preserve scientific heritage:** Higgs discovery models as historical record
5. **Facilitate replication:** Templates enable reproduction and validation
6. **Promote adoption:** Visible examples encourage community participation
7. **Support education:** Models serve as teaching tools at all levels

## Cross-Experiment and Cross-Domain Benefits

Several showcase examples explicitly demonstrate interdisciplinary value:

- **COMPASS → GlueX, BES III, Belle II:** Light meson production models
- **BES III → LHCb, Belle II:** Exotic hadron states (Zc) and D-meson decays
- **Belle II → LHCb:** B decay models and Wilson coefficients
- **Neutrino experiments → Cosmology:** Combined statistical models
- **Nuclear → Hadron → Astro:** NN interactions impact multiple domains
- **HZDR models → NIF, HIBEF:** Laser-matter interaction for fusion research

Through this comprehensive showcasing effort, WP 3.2 demonstrates the transformative potential of the DEMOS standard for enabling seamless knowledge transfer across the entire ErUM community.
