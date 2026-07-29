# Ausgewählte Projekte

DEMOS entwickelt und unterstützt ein offenes Ökosystem interoperabler Werkzeuge für statistische Modellierung, Inferenz und die langfristige Bewahrung wissenschaftlicher Modelle. Die hier vorgestellten Projekte decken komplementäre Teile dieses Ökosystems ab – von gemeinsamen Formaten und Modellierungssprachen bis hin zu unabhängigen Inferenz-Engines.

## Standardisierung, Formate und Sprachen

<div class="project-grid" markdown>

<div class="project-card" markdown>

### HS³ — High Energy Physics Statistics Serialization Standard

HS³ ist ein implementierungsunabhängiges Format zur Veröffentlichung statistischer Modelle aus der Hochenergiephysik. Es beschreibt Likelihoods, Datensätze, Funktionen und ihre Beziehungen in einer portablen, maschinenlesbaren Form. Dadurch kann dasselbe Modell mit unterschiedlichen Software-Stacks untersucht und ausgewertet werden.

[:material-book-open-variant: Dokumentation](https://hep-statistics-serialization-standard.github.io/){ .md-button }
[:fontawesome-brands-github: Quellcode](https://github.com/hep-statistics-serialization-standard){ .md-button }
[:material-file-document-outline: Publikation](https://arxiv.org/abs/2606.01760){ .md-button }

</div>

<div class="project-card" markdown>

### FlatPPL

FlatPPL ist eine probabilistische Programmiersprache in Entwicklung, mit der sich statistische Modelle unabhängig von einer bestimmten Inferenzimplementierung ausdrücken lassen. Ihre flache und explizite Modelldarstellung soll Modelle leicht austauschbar, nachvollziehbar, transformierbar und mit unterschiedlichen Backends ausführbar machen und ergänzt damit den serialisierungsorientierten Ansatz von HS³.

[:material-file-document-outline: Entwurf](https://github.com/flatppl/flatppl-design){ .md-button }
[:fontawesome-brands-github: Quellcode](https://github.com/flatppl){ .md-button }
[:material-code-braces: Beispiele](https://github.com/flatppl/flatppl-examples){ .md-button }

</div>

</div>

## Inferenz-Engines

<div class="project-grid" markdown>

<div class="project-card" markdown>

### ROOT / RooFit

RooFit ist das in ROOT enthaltene Werkzeug zur Konstruktion und Auswertung statistischer Modelle sowie zur likelihoodbasierten Inferenz. Die HS³-Integration kann RooWorkspaces als portable JSON- oder YAML-Dokumente importieren und exportieren und schafft damit eine Brücke zwischen etablierten RooFit-Analysen und anderer HS³-kompatibler Software.

[:material-book-open-variant: HS³-Dokumentation](https://root.cern/doc/master/group__roofit__dev__docs__hs3.html){ .md-button }
[:material-code-braces: API-Referenz](https://root.cern/doc/master/classRooJSONFactoryWSTool.html){ .md-button }
[:fontawesome-brands-github: Quellcode](https://github.com/root-project/root/tree/master/roofit/hs3){ .md-button }

</div>

<div class="project-card" markdown>

### Combine

Combine ist das von der CMS-Kollaboration breit eingesetzte Framework für statistische Analysen und Kombinationen. Über seine RooFit-basierte Modelldarstellung und die in Entwicklung befindliche HS³-Unterstützung für Combine-spezifische Modellkomponenten können Combine-Workspaces in den standardisierten Modellaustausch, die langfristige Bewahrung und die frameworkübergreifende Validierung einbezogen werden.

[:material-book-open-variant: Dokumentation](https://cms-analysis.github.io/HiggsAnalysis-CombinedLimit/){ .md-button }
[:fontawesome-brands-github: Quellcode](https://github.com/cms-analysis/HiggsAnalysis-CombinedLimit){ .md-button }
[:material-file-document-outline: Publikation](https://arxiv.org/abs/2404.06614){ .md-button }

</div>

<div class="project-card" markdown>

### BAT.jl

BAT.jl ist ein Julia-Werkzeug für Bayessche Inferenz und stellt Algorithmen für Posterior-Sampling, Optimierung und numerische Integration bereit. Gemeinsam mit der Julia-Implementierung von HS³ ermöglicht es, portable statistische Modelle in einer leistungsfähigen Julia-Umgebung auszuwerten und die Ergebnisse mit anderen Inferenz-Engines zu vergleichen.

[:material-book-open-variant: Dokumentation](https://bat.github.io/BAT.jl/stable/){ .md-button }
[:fontawesome-brands-github: Quellcode](https://github.com/bat/BAT.jl){ .md-button }
[:material-swap-horizontal: HS³-Integration](https://github.com/JuliaHEP/HS3.jl){ .md-button }

</div>

<div class="project-card" markdown>

### pyHS3

pyHS3 ist eine reine Python-Implementierung von HS³, die serialisierte Modelle in ausführbare Berechnungsgraphen übersetzt. Die Bibliothek verwendet Tensoroperationen und automatische Differenzierung zur Auswertung von Likelihoods und für statistische Inferenz und bietet damit ein unabhängiges Python-Backend für Interoperabilitätstests und die Arbeit mit veröffentlichten HS³-Modellen.

[:material-book-open-variant: Dokumentation](https://pyhs3.readthedocs.io/){ .md-button }
[:fontawesome-brands-github: Quellcode](https://github.com/scipp-atlas/pyhs3){ .md-button }
[:material-language-python: Python-Paket](https://pypi.org/project/pyhs3/){ .md-button }

</div>

</div>
