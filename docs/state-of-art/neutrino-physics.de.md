---
title: Neutrinophysik - Stand der Technik
---

# Neutrinophysik

## Überblick

In der Neutrino-Oszillationsphysik hat ein Modell typischerweise **drei Hauptkomponenten**:

1. **Initialer Neutrino-Fluss**
2. **Flavor-Transition** unter gegebenen Annahmen
3. **Detektorantwort**

## Fluss-Beschreibung

Die Beschreibung des nicht-oszillierten Flusses kann sein:

- **Theoretisch** (z.B. für Solar-Neutrinos)
- **Daten-getrieben** (z.B. atmosphärische Neutrinos, Kernreaktoren)

## Oszillationsberechnungen

Der Code zur Berechnung von Flavor-Übergangswahrscheinlichkeiten reicht von:

- Einfachen **Zwei-Flavor-Vakuum-Oszillations**-Wahrscheinlichkeitsberechnungen
- Rechenintensiveren Szenarien, wie **Beyond the Standard Model (BSM) n-Flavor-Oszillationen**

## Detektorantwort

Die Antwort des Neutrino-Detektors übersetzt das **oszillierte Spektrum** in den **Raum der Observablen**.

---

## Experimentelle Kollaborationen

Experimentelle Kollaborationen entwickeln ausgefeilte Modelle zur Analyse ihrer Daten:

- **Super-K** (Super-Kamiokande)
- **Borexino**
- **IceCube**
- **T2K**
- **NOvA**
- **Daya Bay**

### Sharing-Praktiken

Diese Modelle werden:

- **Selten geteilt** mit der Öffentlichkeit
- Bleiben oft **proprietär**

---

## Global-Fitter-Bemühungen

Es gibt mehrere Global-Fitter-Bemühungen, die darauf abzielen, offizielle Ergebnisse zu reproduzieren:

- **NuFit**[^1]
- **Bari**[^2]
- **Valencia**[^3]

Andere Gruppen nutzen diese Daten zur Erforschung von **BSM-Physik**.

---

## Aktuelle Standards-Situation

Bis heute existiert **kein gemeinsamer Standard** für diese Zwecke.

### Unterschiedliche Praktiken

Die Praktiken variieren erheblich zwischen Kollaborationen:

- Das **GLoBES**[^4]-Software-Paket zielte einst darauf ab, Simulations- und Analyse-Pipelines für Reaktor- und Strahl-Neutrino-Oszillationsexperimente zu vereinheitlichen
- Allerdings ist GLoBES weitgehend **aus der Nutzung gefallen**

---

## TUM-Gruppen-Beiträge

### IceCube-Datenveröffentlichungen

Die **TUM-Gruppe (Eller)** hat eine Datenveröffentlichung für **IceCubes Oszillationsanalysen** vorbereitet und veröffentlicht.

**Herausforderung**: Da kein vordefiniertes Format existierte, wurden Entscheidungen über die Struktur **ad hoc** getroffen.

Der Prozess, obwohl unkompliziert, erforderte das Navigieren von:

- Internen Genehmigungsprozessen
- Spiegelnd die etablierte Position des PI innerhalb der Kollaboration

### Globale Fits

Darüber hinaus hat die TUM-Gruppe **globale Neutrino-Oszillationsfits** basierend auf öffentlichen Daten und reimplementierten Likelihoods[^5][^6][^7] durchgeführt.

---

## MPP-Gruppen-Beiträge

### GERDA und MAJORANA

Die **MPP-Gruppe (Schulz)** war tief involviert in die Physik-Analyse der **GERDA**- und **MAJORANA**-Experimente, mit Fokus auf:

- Statistische Modellierung
- Hintergrund-Unterdrückungstechniken
- **Neutrinoloser Doppelbeta-Zerfall**-Studien

### LEGEND-Übergang

Ihre Beiträge haben den Übergang zu **LEGEND** unterstützt durch:

- Verfeinerung der Datenanalysemethoden
- Sicherstellung robuster Interpretation experimenteller Ergebnisse
- Abstimmung mit breiteren Bemühungen zur Förderung der Präzisions-Neutrinophysik

---

## Showcase-Modelle

### Kombinierte Analyse

MPP (Schulz) wird eine **kombinierte neutrinolose Doppelzerfallanalyse**[^8] zur DEMOS-Modellgalerie hinzufügen, basierend auf:

- Datenveröffentlichungen der GERDA- und MAJORANA-Experimente
- Veröffentlichten Likelihoods aus der Kosmologie
- Neutrino-Oszillationsexperimenten

**Bedeutung**: Dieses Modell wird ein gutes Showcase dafür sein, wie der DEMOS-Standard verwendet werden kann, um statistische Modelle aus verschiedenen Domänen **auszudrücken und zu kombinieren**.

### Neutrino-Oszillationsmodelle

Die TUM-Gruppe (Eller) wird an der Containerisierung von Neutrino-Oszillationsmodellen arbeiten und sie mit dem **MaaS-Protokoll** ausstatten für nahtlose Bereitstellung und Integration in diverse Infrastrukturen.

---

## Zusammenfassung

Neutrinophysik stellt einzigartige Herausforderungen für das Modell-Sharing dar:

❌ **Aktuelle Herausforderungen**:

- Kein gemeinsamer Standard existiert
- Modelle selten öffentlich geteilt
- GLoBES ist aus der Nutzung gefallen
- Ad-hoc-Formate bei Datenveröffentlichungen
- Proprietäre Kollaborationspraktiken

✅ **Chancen**:

- TUM-Gruppenerfahrung mit IceCube-Datenveröffentlichungen
- MPP-Expertise in Doppelbeta-Zerfallsanalyse
- Global-Fit-Erfahrung und Likelihood-Rekonstruktion
- Klarer Bedarf an Standardisierung erkannt

🎯 **DEMOS-Vorteile**:

- Standardisiertes Format für Oszillationsparameter
- Kombination von Modellen aus verschiedenen Experimenten
- Domänenübergreifende Integration (Kosmologie + Oszillationen)
- MaaS-Protokoll für komplexe Detektorantwortmodelle
- Verbesserte Reproduzierbarkeit für globale Fits

Die Neutrinophysik-Community wird signifikant vom DEMOS-Standard profitieren, der einen besseren Vergleich von Ergebnissen über Experimente hinweg ermöglicht und die Kombination von Daten aus verschiedenen Quellen für Präzisionsphysik erleichtert.

---

## Referenzen

[^1]: I. Esteban et al., "NuFit-6.0: Updated global analysis of three-flavor neutrino oscillations," Oct. 2024.

[^2]: A. Marrone et al., "Global fits to neutrino oscillations: status and prospects," *PoS*, EPS-HEP2015, p. 093, 2015.

[^3]: P. F. de Salas et al., "2020 global reassessment of the neutrino oscillation picture," *JHEP*, vol. 02, p. 071, 2021.

[^4]: P. Huber et al., "New features in the simulation of neutrino oscillation experiments with GLoBES 3.0: General Long Baseline Experiment Simulator," *Comput. Phys. Commun.*, vol. 177, pp. 432–438, 2007.

[^5]: M. Ettengruber et al., "Testing the number of neutrino species with a global fit of neutrino data," *Phys. Rev. D*, vol. 109, no. 9, p. 095016, 2024.

[^6]: T. Kozynets et al., "Constraints on non-unitary neutrino mixing in light of atmospheric and reactor neutrino data," July 2024.

[^7]: M. Ettengruber et al., "Discovering neutrinoless double-beta decay in the era of precision neutrino cosmology," *Phys. Rev. D*, vol. 106, no. 7, p. 073004, 2022.

[^8]: M. Ettengruber et al., "Discovering neutrinoless double-beta decay in the era of precision neutrino cosmology," *Phys. Rev. D*, vol. 106, no. 7, p. 073004, 2022.
