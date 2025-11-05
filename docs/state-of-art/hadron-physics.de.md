---
title: Hadronenphysik - Stand der Technik
---

# Hadronenphysik

## Überblick

Im Bereich der Hadronenphysik, insbesondere innerhalb des Teilgebiets der **Hadronenspektroskopie**, dienen Modelle als mathematische Frameworks zur Beschreibung der Eigenschaften und Wechselwirkungen von Hadronen und der hadronischen Umgebung.

**Streuungsamplituden** zwischen Hadronen werden mittels einer Partialwellenentwicklung modelliert, um Eigenschaften hadronischer Resonanzen einzugrenzen und an gemessene Differentialspektren anzupassen.

## Datenquellen

Hadronenphysik-Daten stammen hauptsächlich von:

### Collider-Experimenten

- **LHCb** - Large Hadron Collider beauty experiment
- **Belle II** - B-Factory-Experiment
- **BESIII** - Beijing Spectrometer
- **COMPASS** - COmmon Muon and Proton Apparatus for Structure and Spectroscopy
- **GlueX** - Photoproduktions-Experiment

### Gitter-Simulationen

Komplementäre Informationen wurden kürzlich aus **Gittersimulationen der Quantenchromodynamik (Lattice QCD)** gewonnen.

---

## Konsortiums-Repräsentation

### Experimentelle Seite

Hier vertreten durch:

- **RUB-H** (Mikhasenko, Fritsch) - LHCb, COMPASS
- **MPP** (Wallner) - Belle II, COMPASS
- **JGU** (Hüsken) - BESIII

### Lattice QCD

- **RUB-H** (J. Bulava) - Entwickelt und nutzt hadronische Modelle, um Finite-Volume-Spektren mit Hadronenstreuungsamplituden zu verbinden. Hat eine umfassende Sammlung dieser Beziehungen sowie eine entsprechende C++-Implementierung[^1] veröffentlicht.

---

## Forschungsschwerpunkt

Das Feld wird von Studien zu **exotischen Konfigurationen von Quark-Materie** angetrieben:

- **Tetraquarks** (Vier-Quark-Zustände)
- **Pentaquarks** (Fünf-Quark-Zustände)
- **Hybriden** (Quark-Antiquark mit angeregtem Glue)
- **Glueballs** (gebundene Zustände von Gluonen)

### Weiterreichende Auswirkungen

Hadronenphysik leistet auch wesentliche Beiträge zu anderen Domänen:

- Präzisionsmessungen von Standardmodell-Observablen
- Suche nach Physik jenseits des Standardmodells
- Jagd nach Dunkler Materie
- Untersuchung von Neutronensternen

---

## LHCb-Führung

Die **LHCb-Kollaboration**, vertreten durch die RUB-H-Gruppe, führt das Feld an mit:

- Entdeckung von **mehr als 70 neuen zusammengesetzten Teilchen**, viele exotischer Natur
- **~700 Publikationen**, die Mehrheit mit Modellierungsaspekten, die durch den DEMOS-Standard erfasst werden
- **Mindestens 30 komplexe Modelle** von besonderer Bedeutung für die breitere Community

---

## Belle II Beiträge

Innerhalb von **Belle II** leitet die MPP-Gruppe die Bemühungen, Partialwellenmodelle für die hadronische Resonanzstruktur von Mehrkörper-hadronischen B- und τ-Zerfällen einzugrenzen.

Dies ergänzt Messungen von LHCb und BESIII. Mit diesem Vorhaben wird Expertise zur Entwicklung eines der **komplexesten Resonanzmodelle von COMPASS**[^2] auf das Belle II-Experiment übertragen[^3].

---

## BESIII-Exzellenz

Die Arbeit an Vektor-Charmonium-Resonanzen, die von der **JGU-Gruppe** durchgeführt wird, profitiert von weltführenden Datensätzen des BESIII-Experiments.

Die Gruppe leitet die globale Anstrengung zur Interpretation dieser Daten[^4][^5] mit einer fortschrittlichen Modellierungstechnik.

### Spezifische Anwendungen

Modelle, die unter Verwendung von BESIII-Daten extrahiert wurden, umfassen:

- **Event-Generierung** von γp → Zc(3900)p, erforderlich für das CEBAF-Facility-Energie-Upgrade am Jefferson Lab
- **Präzise Lineshapes** von Vektor-Charmonium-Zuständen, benötigt in Studien schwacher b → sℓ⁺ℓ⁻-Zerfälle
- **D-Meson-Zerfall**-Messungen bei BESIII, die wichtige Eingaben für CKM-Matrix-Parametermessungen bei LHCb und Belle II liefern

### Community-Position

Als **Convenor der Charmonium-Physik-Gruppe** ist der PI einzigartig positioniert, um die Community-Engagement-Aktivitäten innerhalb von BESIII zu leiten.

---

## Die Herausforderung: Dramatische Sharing-Situation

Die Situation beim Teilen von Modellen ist im Feld **dramatisch**:

### Reproduzierbarkeitskrise

Komplexe Parametrisierungen von Partialwellen sind **größtenteils unmöglich zu reproduzieren** aus veröffentlichten Informationen aufgrund von:

- Fehlenden Details zu Konventionen
- Fehlenden Normierungsinformationen
- Unvollständigen Beschreibungen großer Parametersätze

### Modellunsicherheiten

Modellunsicherheiten werden **fast nie** in veröffentlichten Daten eingeschlossen.

### Framework-Fragmentierung

**Dutzende von Frameworks** existieren innerhalb der Domäne der experimentellen Partialwellenanalyse, jedes mit einem internen Speichermodell zur Darstellung von Partialwellenzerlegungen.

Die meisten Forschenden entwickeln ihr **eigenes Framework** während ihres Lernpfads, was typischerweise **mehrere Jahre** in Anspruch nimmt.

Es gibt **keinen universellen Standard** zum Transport von Informationen zwischen Frameworks, was führt zu:

- Herausforderungen bei der Interoperabilität
- Inkonsistenz über das Feld hinweg

---

## Standardisierungsbemühungen

Eine Anstrengung zur Standardisierung von Partialwellenmodellen wurde von der **RUB-H-Gruppe** mit mehreren Methodologie-Papieren[^6][^7][^8][^9] initiiert.

### Amplituden-Serialisierung

Ein Prototyp für eine Beschreibung von Kaskadenzerfällen, der in den letzten Jahren entwickelt wurde, ist verfügbar unter [amplitude-serialization](https://github.com/ComPWA/amplitude-serialization).

**Aktuelle Einschränkung**: Die Modellkomplexität ist stark auf Dreikörperzerfälle begrenzt, was die Aufnahme dieser Modellklasse in den DEMOS-Standard erforderlich macht.

---

## Konsortiums-Beiträge

### Komplexe Modelle als Showcase

Die RUB-H-Gruppe wird **hochzitierte Beispiele** serialisieren:

1. **Pcc̄ Pentaquarks** - Entdeckung in Λ⁰b → J/ψK⁻p-Zerfällen[^10]
2. **Λ⁺c → pK⁻π⁺**-Zerfälle - Demonstration der korrekten Berichterstattung von Modellierungsunsicherheit mit 18 alternativen Modellen[^11]
3. **χc1(3872) und T⁺cc Tetraquark**-Analysen - Komplizierte Lineshape-Parametrisierungen[^12][^13]
4. **Tcs und Tcs̄ Zustände** - Amplitudenmodelle von B-Zerfällen nach DDπ und DDK[^14][^15]

---

## Zusammenfassung

Hadronenphysik steht vor einzigartigen Herausforderungen beim Modell-Sharing:

❌ **Kritische Probleme**:

- Komplexe Modelle aus Publikationen unmöglich zu reproduzieren
- Dutzende inkompatibler Frameworks
- Kein universeller Standard für Modellaustausch
- Modellunsicherheiten selten berichtet
- Jahre erforderlich zur Entwicklung von Analyseexpertise

✅ **Chancen**:

- RUB-H pioniert Standardisierungsbemühungen
- Amplituden-Serialisierungs-Prototyp existiert
- Starke Konsortiums-Repräsentation in wichtigen Experimenten
- Klarer Bedarf von der Community erkannt

Die DEMOS-Initiative wird diese Herausforderungen angehen, indem sie einen umfassenden Standard bereitstellt, der die Komplexität von Hadronenphysik-Modellen erfassen kann, während Reproduzierbarkeit und experimentübergreifende Zusammenarbeit ermöglicht werden.

---

## Referenzen

[^1]: C. Morningstar et al., "Estimating the two-particle K-matrix for multiple partial waves," *Nucl. Phys. B*, vol. 924, pp. 477–507, 2017.

[^2]: M. Aghasyan et al., "Light isovector resonances in π⁻p → π⁻π⁻π⁺p at 190 GeV/c," *Phys. Rev. D*, vol. 98, no. 9, p. 092003, 2018.

[^3]: A. Rabusov et al., "Measurement of the presence of a₁(1420) and ω(782) in τ⁻ → π⁻π⁻π⁺ντ at Belle," *17th International Workshop on Tau Lepton Physics*, May 2024.

[^4]: N. Hüsken et al., "Poles and poltergeists in e⁺e⁻ → DD̄ data," *Phys. Rev. D*, vol. 109, no. 11, p. 114010, 2024.

[^5]: N. Hüsken et al., "K-matrix analysis of e+e- annihilation in the bottomonium region," *Phys. Rev. D*, vol. 106, no. 9, p. 094013, 2022.

[^6]: M. Mikhasenko et al., "Dalitz-plot decomposition for three-body decays," *Phys. Rev. D*, vol. 101, no. 3, p. 034033, 2020.

[^7]: K. Habermann and M. Mikhasenko, "Wigner rotations for cascade reactions," Sept. 2024.

[^8]: M. Mikhasenko et al., "What is the right formalism to search for resonances?" *Eur. Phys. J. C*, vol. 78, no. 3, p. 229, 2018.

[^9]: A. Pilloni et al., "What is the right formalism to search for resonances? II. The pentaquark chain," *Eur. Phys. J. C*, vol. 78, no. 9, p. 727, 2018.

[^10]: R. Aaij et al., "Observation of J/ψp Resonances Consistent with Pentaquark States," *Phys. Rev. Lett.*, vol. 115, p. 072001, 2015.

[^11]: R. Aaij et al., "Amplitude analysis of the Λ⁺c → pK⁻π⁺ decay," *Phys. Rev. D*, vol. 108, no. 1, p. 012023, 2023.

[^12]: R. Aaij et al., "Study of the lineshape of the χc1(3872) state," *Phys. Rev. D*, vol. 102, no. 9, p. 092005, 2020.

[^13]: R. Aaij et al., "Study of the doubly charmed tetraquark T⁺cc," *Nature Commun.*, vol. 13, no. 1, p. 3351, 2022.

[^14]: R. Aaij et al., "Amplitude analysis of the B⁺ → D⁺D⁻K⁺ decay," *Phys. Rev. D*, vol. 102, p. 112003, 2020.

[^15]: R. Aaij et al., "Amplitude analysis of B⁰ → D̄⁰D⁺sπ⁻ and B⁺ → D⁻D⁺sπ⁺ decays," *Phys. Rev. D*, vol. 108, no. 1, p. 012017, 2023.
