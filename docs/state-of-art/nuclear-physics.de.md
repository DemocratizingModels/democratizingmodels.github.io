---
title: Kernphysik - Stand der Technik
---

# Kernphysik

## Überblick

Im Bereich der Kernphysik bietet das **Ab-initio-Framework** einen grundlegenden Ansatz zur Untersuchung von Kernstruktur und -dynamik.

Dieses Rechenframework beinhaltet die Lösung der **N-Körper-Schrödinger-Gleichung**, wobei relativistische Korrekturen über eine Eins-über-Masse-Entwicklung eingebunden werden. Dies ermöglicht nun die zuverlässige Beschreibung von Eigenschaften leichter und mittelschwerer Kerne für spezifische nukleare Hamiltonoperatoren.

## Unsicherheitsquellen

Für diese Kerne entsteht die dominante Unsicherheitsquelle nicht aus den Rechenframeworks, sondern aus dem **nuklearen Hamiltonoperator selbst**, insbesondere den schlecht verstandenen **Drei-Nukleon-Kräften**.

---

## Chirale Effektive Feldtheorie (EFT)

In den letzten zwei Jahrzehnten hat die **chirale effektive Feldtheorie (EFT)** die traditionellen phänomenologischen Ansätze zu nuklearen Wechselwirkungen in diesen Kontexten weitgehend ersetzt.

### RUB-N Führung

**RUB-N** gehört zu den **weltweit führenden Gruppen**, die Modelle entwickeln für:

- Kernkräfte
- Nukleare Wechselwirkungen mit externen elektroschwachen Sonden
- Alles im Rahmen der chiralen EFT

Siehe Referenzen [^1] und [^2] für umfassende Übersichten.

---

## Modellkomponenten

### Nukleare Wechselwirkungsmodelle

Nukleare Modelle entsprechen mathematischen Ausdrücken, die beschreiben:

1. **Zwei-Nukleon (NN) Potentiale**
2. **Drei-Nukleon (3N) Potentiale**
3. **Zugehörige Stromoperatoren**

Diese Potentiale werden angeboten bei:

- Verschiedenen **Ordnungen** der EFT-Entwicklung
- Verschiedenen Werten des **Cutoff-Parameters**
- Verschiedenen **Basen**

### Niederenergie-Konstanten (LECs)

**Korrelierte Unsicherheiten** für die Niederenergie-Konstanten (LECs) sind ebenfalls verfügbar.

### Marginalisierung über Trunkierung

Arbeiten zur Erzeugung **großer Samples von Potentialen** (von Hunderten bis zu Tausenden) mit zufällig gewählten Termen höherer Ordnung sind im Gange, um die **Marginalisierung** über Beiträge von trunkierten Korrekturen jenseits des betrachteten Genauigkeitsniveaus zu ermöglichen.

---

## Rechnerische Aspekte

### NN-Kräfte

Für **NN-Kräfte** sind bestehende Codes in **Fortran** oder **Python** in der Lage, die NN-Matrixelemente **dynamisch ("on-the-fly")** zu generieren.

### 3N-Kräfte

Die Generierung von Matrixelementen für **3N-Kräfte** ist jedoch wesentlich komplexer und führt oft zu Datendateien, die **mehrere Dutzend Gigabyte** überschreiten können.

---

## Community-Struktur

### Modellentwickler

Mehrere Forschungsgruppen sind aktiv mit der Modellierung nuklearer Wechselwirkungen befasst, wobei **RUB-N** als einer der **prominentesten Beitragenden** anerkannt ist.

### Nutzer-Community

Auf der Nutzerseite gibt es:

- **Mehrere Dutzend etablierte** Few- und Many-Body-Gruppen weltweit
- Eine **viel größere Anzahl einzelner Forschender**, die auf diese Wechselwirkungen angewiesen sind

Sammlungen von Artikeln[^3][^4][^5] bieten einen Hinweis auf die weitverbreitete Nutzung dieser Modelle in der Community.

---

## Aktuelle Sharing-Praktiken

### NN-Wechselwirkungen

Für **NN-Wechselwirkungen** werden Matrixelemente typischerweise:

- Veröffentlicht
- Codes zu ihrer Generierung werden **auf Anfrage bereitgestellt**

### Analytische Ausdrücke

Analytische Ausdrücke für verschiedene Beiträge werden oft als **Mathematica-Notebooks** geteilt.

### Einschränkungen

Diese Sharing-Mechanismen von Modellen sind jedoch **nicht standardisiert**, und informelle Mechanismen wie **direkte Anfragen an Autoren** bleiben üblich.

---

## Verbesserungsmöglichkeiten

Bemühungen zur Entwicklung und Verbreitung von **Standards und Workflows** könnten signifikant verbessern:

- **Zugänglichkeit** nuklearer Wechselwirkungsmodelle
- **Reproduzierbarkeit** von Berechnungen
- **Zusammenarbeit** innerhalb der Kernphysik-Community

---

## DEMOS-Beiträge

### Showcase-Modelle

Innerhalb dieser Förderperiode wird sich **RUB-N** auf die Serialisierung von Modellen für **NN-Wechselwirkungen** konzentrieren, die dominante Beiträge zu Kernstruktur und Niederenergie-Reaktionen liefern.

Die Modellentwicklung umfasst:

1. Ableitung von NN-Potentialen aus der effektiven chiralen Lagrangedichte bis zu einer spezifizierten Ordnung
2. Einführung eines geeigneten UV-Regulators
3. Bestimmung von NN-Niederenergie-Konstanten durch globale Partialwellenanalyse (PWA)
4. Fehleranalyse und Quantifizierung der Trunkierungsunsicherheit

### Umfassende Modellsammlung

Die in [^6] entwickelten NN-Potentialmodelle sind verfügbar bei:

- **Fünf EFT-Entwicklungsordnungen**
- **Verschiedenen Cutoff-Werten**

Diese Wechselwirkungen wurden in [^7] erweitert, um **Isospin-brechende Korrekturen** einzuschließen von:

- QED-Beiträgen
- Unterschieden in Quark-Massen

### Errungenschaft

Die resultierenden Modelle wurden verwendet, um eine umfassende PWA aller verfügbaren NN-Streudaten bis zur Pion-Produktionsschwelle durchzuführen, einschließlich:

- Bestimmung einer konsistenten Datenbank von NN-Daten
- Unsicherheitsquantifizierung

**Ergebnis**: Zum ersten Mal wurde eine **statistisch perfekte Beschreibung** von NN-Daten innerhalb des chiralen EFT-Frameworks erreicht.

---

## Zu teilende Ressourcen

Wir werden einen Mechanismus zum Teilen dieser Modelle zusammen mit:

- **Detaillierter Dokumentation**
- **Anwendungsbeispielen**
- **Benchmark-Ergebnissen**
- **Ressourcen zur Durchführung der Unsicherheitspropagation**:
    - Kovarianzmatrizen für LECs
    - Samples von Modellen mit zufällig gewählten Wechselwirkungen höherer Ordnung
    - Zur Quantifizierung von Trunkierungsfehlern
- **Dokumentierte aktuelle Datenbank** von gegenseitig konsistenten NN-Streudaten

---

## Zusammenfassung

Das Teilen von Kernphysik-Modellen stellt sowohl Herausforderungen als auch Chancen dar:

✅ **Aktuelle Praktiken**:

- NN-Matrixelemente typischerweise veröffentlicht
- Code auf Anfrage bereitgestellt
- Mathematica-Notebooks für analytische Ausdrücke
- Starkes theoretisches Framework (chirale EFT)

❌ **Einschränkungen**:

- Keine standardisierten Sharing-Mechanismen
- Informelles anfrage-basiertes System
- 3N-Kräfte besonders herausfordernd (Dutzende GB-Dateien)
- Begrenzte Automatisierung und Zugänglichkeit

🎯 **DEMOS-Vorteile**:

- Standardisierte Modellserialisierung
- Umfassende Dokumentation
- Werkzeuge zur Unsicherheitsquantifizierung
- Zugängliche Datenbank von Wechselwirkungen
- Verbesserte Zusammenarbeit über Few- und Many-Body-Communities hinweg

Die Kernphysik-Community wird stark von dem DEMOS-Standard profitieren, der ein effizienteres Teilen komplexer nuklearer Wechselwirkungsmodelle ermöglicht und eine breitere Zusammenarbeit in Ab-initio-Kernstrukturberechnungen fördert.

---

## Referenzen

[^1]: E. Epelbaum et al., "Modern Theory of Nuclear Forces," *Rev. Mod. Phys.*, vol. 81, pp. 1773–1825, 2009.

[^2]: E. Epelbaum et al., "High-precision nuclear forces from chiral EFT: State-of-the-art, challenges and outlook," *Front. in Phys.*, vol. 8, p. 98, 2020.

[^3]: M. Piarulli et al., "Editorial: Uncertainty quantification in nuclear physics," *Front. in Phys.*, vol. 11, p. 1270577, 2023.

[^4]: L. Marcucci, "Editorial: The Long-Lasting Quest for Nuclear Interactions: The Past, the Present and the Future," *Front. in Phys.*, vol. 8, p. 609907, 2020.

[^5]: I. Tews et al., "Nuclear Forces for Precision Nuclear Physics: A Collection of Perspectives," *Few Body Syst.*, vol. 63, no. 4, p. 67, 2022.

[^6]: P. Reinert et al., "Semilocal momentum-space regularized chiral two-nucleon potentials up to fifth order," *Eur. Phys. J. A*, vol. 54, no. 5, p. 86, 2018.

[^7]: P. Reinert et al., "Precision determination of pion-nucleon coupling constants using effective field theory," *Phys. Rev. Lett.*, vol. 126, no. 9, p. 092501, 2021.
