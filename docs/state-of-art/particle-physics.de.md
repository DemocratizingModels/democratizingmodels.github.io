---
title: Teilchenphysik - Stand der Technik
---

# Teilchenphysik

## Überblick

Die Teilchenphysik hat immens von einem relativ einheitlichen Datenanalyse-Ökosystem profitiert, angeführt von [ROOT](https://root.cern/) – einem umfassenden Framework, das von CERN entwickelt und gepflegt wird.

## Das ROOT-Ökosystem

ROOT beinhaltet **RooFit** und **RooStats**, eine leistungsfähige statistische Modellierungssprache, die in der Lage ist:

- Komplexe Modelle mit Tausenden von Parametern zu aggregieren
- Modelle als sogenannte **Workspaces** zu speichern
- Workspaces als Binärdateien zu sichern

Innerhalb von Analyse-Teams werden Modelle typischerweise von einer Handvoll Statistik-Experten pro Team konstruiert. Diese Workspaces können sogar **auf der Likelihood-Ebene kombiniert** werden, eine Funktion, die bei der Higgs-Boson-Entdeckung[^1][^2] von entscheidender Bedeutung war.

### Einschränkungen von ROOT

ROOT hat jedoch einige signifikante technische Limitierungen:

- **Binäre Workspaces** können nur mit ROOT-Software aufgerufen und bearbeitet werden
- ROOT wird **selten außerhalb der Hochenergiephysik** (HEP) verwendet
- Dies beeinträchtigt die **Interoperabilität** mit Theoretikern oder nicht-LHC-experimentellen Kollaborationen
- **Langfristige Nachhaltigkeit** der Bewahrung von LHC-Ära-Modellen in diesem Format ist ein wachsendes Anliegen (ROOT ist alternde Software)

### Eingeschränktes Teilen

Externes Teilen ist eingeschränkt durch:

- Formale Kollaborationsrichtlinien
- Zusätzliche Arbeitsbelastung bei der Vorbereitung und Verifizierung von Modellen in veröffentlichbaren Formaten

---

## PyHF: Ein Durchbruch

Ein Durchbruch kam mit der Entwicklung von **PyHF**[^3][^4] – einer Python-basierten Neuimplementierung von HistFactory, einem beliebten gebinnten Modellierungswerkzeug innerhalb des RooFit-Ökosystems.

**Leitende Entwickler** von PyHF sind Teil dieses Konsortiums:

- **TUM** (Heinrich)
- **SC** (Stark)

### Hauptmerkmale

Das Python-Paket kam mit einem **Serialisierungsmechanismus**, der ein einfacheres Teilen und Veröffentlichen von Modellen ermöglicht.

**Aktuelle Verbreitung**: Bis heute wurden etwa **40 histogramm-basierte Modelle** im PyHF-Format veröffentlicht.

---

## HS3: HEP Statistics Serialization Standard

Um die Lücke von PyHF zum ROOT-Ökosystem zu überbrücken, wurde der **HEP Statistics Serialization Standard (HS3)**[^5] von **TUDO (Burgard)** entwickelt.

### Vorteile von HS3

HS3 erweitert das Spektrum der Modellbausteine von Histogrammen auf eine Vielzahl kontinuierlicher Verteilungen, während die **vollständige Reproduzierbarkeit** erhalten bleibt.

**Hauptmerkmale**:

- Feature-vollständige, JSON-basierte Serialisierung
- Unterstützung für kontinuierliche Verteilungen über Histogramme hinaus
- Vollständige Reproduzierbarkeit gewährleistet

### Verbreitung

HS3 wurde von der **ATLAS-Kollaboration** als offizieller Standard für die Veröffentlichung von Likelihoods[^6][^7][^8][^9][^10][^11][^12][^13] übernommen.

### Aktuelle Einschränkungen

Die weitverbreitete Verbreitung ist jedoch noch begrenzt durch:

- Fehlende implementierte Engines außerhalb des ROOT-Ökosystems
- Begrenzte Konvertierungswerkzeuge

---

## Zukünftige Anforderungen

In Zukunft ist **zusätzliche Flexibilität** in Modellen über die Fähigkeiten der PyHF-Serialisierung und was derzeit mit HS3 möglich ist, notwendig.

### Beispiel: Belle II Statistical Inference

Referenz [^14] präsentiert eine hochgradig allgemeine Methode für statistische Inferenz auf neue Physik-Parameter unter Verwendung eines Beispiels von Belle II. Die Methode ist breit anwendbar und verwendet Modelle, die als **pyhf** oder **HS3** kodiert sind, sowie zukünftige Weiterentwicklungen davon.

**Vorteile**:

- Präzisere Parameterschätzungen
- Erleichtert die Kombination von Ergebnissen über Experimente hinweg
- Ermöglicht die Kombination über verschiedene Physikdomänen hinweg

---

## Domänenspezifische Sprachen

Umgekehrt gibt es statistische domänenspezifische Sprachen (DSLs) wie **STAN**[^15], die:

- Ziemlich allgemein sind
- Eng mit spezifischen Methoden statistischer Inferenz gekoppelt sind
- In einer einzigen Programmiersprache implementiert sind

### STAN-Beispiel

STAN ist auf **Bayesische Inferenz** via Hybrid-Monte-Carlo-Sampling in C++ fokussiert.

**Einschränkung**: Obwohl viele Modelle in STAN ausgedrückt werden können, ist die Wiederverwendung, Kombination und das Teilen dieser Modelle nicht einfach, was zu **begrenzter Verbreitung** in der Teilchenphysik führt.

---

## Die Gelegenheit

Dieser Vorschlag nutzt die einzigartige Gelegenheit, die Autoren und Maintainer von:

- **PyHF** (ansässig bei TUM, LMU und SC)
- **HS3** ROOT-Engine (bei TUDO)

hinter einem einzigen harmonisierten Ansatz zu vereinen.

---

## Konsortiums-Beiträge

### Statistische Tools Führung

Konsortiumsmitglieder sind führende Entwickler von:

- **PyHF** (TUM, LMU, SC)
- **HS3**-Standard (TUDO)
- **ROOT/RooStats**-Ökosystem (mehrere Institutionen)

### Experimentelle Kollaborations-Führung

Konsortiumsmitglieder haben Führungspositionen in:

- **ATLAS**-Kollaboration (TUDO, LMU, TUM)
- **CMS**-Kollaboration
- **Belle II**-Experiment (LMU, MPP)

Dies positioniert das Konsortium ideal, um die Verbreitung des DEMOS-Standards innerhalb der Teilchenphysik-Community voranzutreiben.

---

## Zusammenfassung

Die Teilchenphysik hat bedeutende Fortschritte bei der Modellserialisierung und dem Teilen gemacht, aber Herausforderungen bleiben:

✅ **Errungenschaften**:

- ROOT/RooFit bietet leistungsfähige statistische Modellierung
- PyHF ermöglicht Python-basierte Modellserialisierung
- HS3 bietet JSON-basierte Serialisierung für ROOT-Workspaces
- Offizielle Übernahme durch die ATLAS-Kollaboration

❌ **Verbleibende Herausforderungen**:

- Begrenzte Interoperabilität zwischen Ökosystemen
- Alternde ROOT-Infrastruktur
- Bedarf an flexibleren Modellstrukturen
- Begrenzte Verbreitung von Sharing-Praktiken

Die DEMOS-Initiative wird auf diesen Errungenschaften aufbauen, um einen wirklich interoperablen Standard zu schaffen, der die gesamte Teilchenphysik-Community bedient und disziplinübergreifende Zusammenarbeit ermöglicht.

---

## Referenzen

[^1]: G. Aad et al., "Observation of a new particle in the search for the Standard Model Higgs boson with the ATLAS detector at the LHC," *Phys. Lett. B*, vol. 716, pp. 1–29, 2012.

[^2]: G. Aad et al., "A particle consistent with the Higgs Boson observed with the ATLAS Detector at the Large Hadron Collider," *Science*, vol. 338, pp. 1576–1582, 2012.

[^3]: L. Heinrich, M. Feickert, and G. Stark, "pyhf: v0.7.6," https://github.com/scikit-hep/pyhf/releases/tag/v0.7.6.

[^4]: L. Heinrich et al., "pyhf: pure-python implementation of histfactory statistical models," *Journal of Open Source Software*, vol. 6, no. 58, p. 2823, 2021.

[^5]: C. Burgard et al., "Hs3 v0.2," 2024.

[^6]: ATLAS collaboration, "Measurement of the charge asymmetry in top-quark pair production in association with a photon with the ATLAS experiment," *Phys. Lett. B*, vol. 843, p. 137848, 2023.

[^7]: ATLAS collaboration, "Inclusive and differential cross-section measurements of ttZ production," *JHEP*, vol. 07, p. 163, 2024.

[^8]: ATLAS collaboration, "Measurement of the tt̄ cross section and its ratio to the Z production cross section," *Phys. Lett. B*, vol. 848, p. 138376, 2024.

[^9]: ATLAS collaboration, "Search for heavy right-handed Majorana neutrinos," *Phys. Rev. D*, vol. 110, no. 11, p. 112004, 2024.

[^10]: ATLAS collaboration, "Measurements of inclusive and differential cross-sections of tt̄γ production," *JHEP*, vol. 10, p. 191, 2024.

[^11]: ATLAS collaboration, "Observation of tt̄ production in the lepton+jets and dilepton channels in p+Pb collisions," *JHEP*, vol. 11, p. 101, 2024.

[^12]: ATLAS collaboration, "Search for same-charge top-quark pair production in pp collisions," Sept. 2024.

[^13]: L. Gärtner et al., "Constructing model-agnostic likelihoods," *Eur. Phys. J. C*, vol. 84, no. 7, p. 693, 2024.

[^14]: L. Gärtner et al., "Constructing model-agnostic likelihoods, a method for the reinterpretation of particle physics results," *Eur. Phys. J. C*, vol. 84, no. 7, p. 693, 2024.

[^15]: Stan Development Team, "Stan: A probabilistic programming language," Version 2.33, 2023.
