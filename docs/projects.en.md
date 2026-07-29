# Featured Projects

DEMOS develops and supports an open ecosystem of interoperable tools for statistical modeling, inference, and the long-term preservation of scientific models. The projects featured here cover complementary parts of this ecosystem, from common formats and modeling languages to independent inference engines.

## Standardization, formats and languages

<div class="project-grid" markdown>

<div class="project-card" markdown>

### HS³ — High Energy Physics Statistics Serialization Standard

HS³ is an implementation-independent format for publishing statistical models used in high-energy physics. It represents likelihoods, datasets, functions, and their relationships in a portable, machine-readable form, enabling the same model to be inspected and evaluated with different software stacks.

[:material-book-open-variant: Documentation](https://hep-statistics-serialization-standard.github.io/){ .md-button }
[:fontawesome-brands-github: Source code](https://github.com/hep-statistics-serialization-standard){ .md-button }
[:material-file-document-outline: Paper](https://arxiv.org/abs/2606.01760){ .md-button }

</div>

<div class="project-card" markdown>

### FlatPPL

FlatPPL is a developing probabilistic programming language for expressing statistical models independently of a particular inference implementation. Its flat, explicit model representation is designed to make models easy to exchange, inspect, transform, and execute with different backends, complementing the serialization-oriented approach of HS³.

[:material-file-document-outline: Design](https://github.com/flatppl/flatppl-design){ .md-button }
[:fontawesome-brands-github: Source code](https://github.com/flatppl){ .md-button }
[:material-code-braces: Examples](https://github.com/flatppl/flatppl-examples){ .md-button }

</div>

</div>

## Inference engines

<div class="project-grid" markdown>

<div class="project-card" markdown>

### ROOT / RooFit

RooFit is ROOT's toolkit for constructing and evaluating statistical models and performing likelihood-based inference. Its HS³ integration can import and export RooWorkspaces as portable JSON or YAML documents, providing a bridge between established RooFit analyses and other HS³-compatible software.

[:material-book-open-variant: HS³ documentation](https://root.cern/doc/master/group__roofit__dev__docs__hs3.html){ .md-button }
[:material-code-braces: API reference](https://root.cern/doc/master/classRooJSONFactoryWSTool.html){ .md-button }
[:fontawesome-brands-github: Source code](https://github.com/root-project/root/tree/master/roofit/hs3){ .md-button }

</div>

<div class="project-card" markdown>

### Combine

Combine is the statistical analysis and combination framework widely used by the CMS experiment. Through its RooFit-based model representation and the developing HS³ support for Combine-specific model components, Combine workspaces can participate in standardized model exchange, preservation, and cross-framework validation.

[:material-book-open-variant: Documentation](https://cms-analysis.github.io/HiggsAnalysis-CombinedLimit/){ .md-button }
[:fontawesome-brands-github: Source code](https://github.com/cms-analysis/HiggsAnalysis-CombinedLimit){ .md-button }
[:material-file-document-outline: Paper](https://arxiv.org/abs/2404.06614){ .md-button }

</div>

<div class="project-card" markdown>

### BAT.jl

BAT.jl is a Julia toolkit for Bayesian inference, providing algorithms for posterior sampling, optimization, and numerical integration. Together with the Julia implementation of HS³, it enables portable statistical models to be evaluated in a high-performance Julia environment and compared with results from other inference engines.

[:material-book-open-variant: Documentation](https://bat.github.io/BAT.jl/stable/){ .md-button }
[:fontawesome-brands-github: Source code](https://github.com/bat/BAT.jl){ .md-button }
[:material-swap-horizontal: HS³ integration](https://github.com/JuliaHEP/HS3.jl){ .md-button }

</div>

<div class="project-card" markdown>

### pyHS3

pyHS3 is a pure-Python implementation of HS³ that turns serialized models into executable computational graphs. It uses tensor operations and automatic differentiation to evaluate likelihoods and perform statistical inference, offering an independent Python backend for testing interoperability and working with published HS³ models.

[:material-book-open-variant: Documentation](https://pyhs3.readthedocs.io/){ .md-button }
[:fontawesome-brands-github: Source code](https://github.com/scipp-atlas/pyhs3){ .md-button }
[:material-language-python: Python package](https://pypi.org/project/pyhs3/){ .md-button }

</div>

</div>
