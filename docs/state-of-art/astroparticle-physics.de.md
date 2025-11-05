---
title: Astroteilchenphysik - Stand der Technik
---

# Astro- und Astroteilchenphysik

## Überblick

In der Astro- und Astroteilchenphysik ist die Modellierung astrophysikalischer Quellen über ein breites Spektrum von Detektionskanälen ein zentraler Aspekt der Forschung.

### Detektionskanäle

- **Elektromagnetische Strahlung** (Radio bis TeV-Energien)
- **Neutrinos**
- **Kosmische Strahlung**
- **Gravitationswellen**

### Doppelte Zwecke

Diese Modelle dienen zwei Zwecken:

1. Helfen Wissenschaftlern zu verstehen, wie **Observablen auf der Erde** in Impuls, Raum und Zeit zusammenhängen
2. Liefern **Vorhersagen**, die die technische Gestaltung von Instrumenten und die Entwicklung von Analysemethoden leiten

---

## Modellstruktur

Ein typisches Modell in dieser Domäne verwendet **Wahrscheinlichkeitsverteilungsfunktionen als Eingaben** – die Quellen und Ziele repräsentieren – und propagiert diese, um **Ausgabe-Wahrscheinlichkeitsverteilungen im Phasenraum** zu erstellen.

---

## Modellkomplexität

Theoretische Modelle in diesem Feld können nach ihrer Komplexität klassifiziert werden.

### Analytische Modelle

**Analytische Modelle** werden oft verwendet, beinhalten aber typischerweise signifikante **Vereinfachungen** der zugrunde liegenden Physik.

### Numerische Modelle

Diese Modelle werden ergänzt und validiert durch komplexere **numerische Modelle**, die berücksichtigen können:

- **Dreidimensionale Verteilungen** der Quellenumgebung
- Realistischere Physik

Numerische Modelle basieren häufig auf:

- **Lösern für partielle Differentialgleichungen** (sowohl linear als auch nichtlinear)
- **Monte-Carlo-Ansätzen**

### Statistisches Fitting

Das Fitten theoretischer Modelle an Daten wird üblicherweise unter Verwendung statistischer Methoden durchgeführt, wobei **MCMC-Ansätze** besonders verbreitet sind.

---

## Serialisierungsherausforderungen

Die Serialisierung von Modellen in der Astro- und Astroteilchenphysik kann Herausforderungen darstellen, insbesondere bei **numerischen Lösern**.

### Parallelisierung

- **Monte-Carlo-Codes** werden trivial parallelisiert durch Verteilung einzelner Teilchentrajektorien auf separate Knoten
- **Numerische Löser** für partielle Differentialgleichungen erfordern ausgeklügeltere Parallelisierungstechniken

---

## CRPropa: Ein führender Code

**CRPropa**, ein Propagations- und Wechselwirkungscode, hauptsächlich entwickelt von **RUB-A**, ist ein Beispiel für einen modularen Code geschrieben in **C++ mit einem Python-Wrapper**.

### Design-Eigenschaften

Sein Design ermöglicht einfache Anpassung von:

- Quellenumgebungen
- 3D-Verteilungsfunktionen, die als Modell-Eingaben dienen

### Rechnerische Anforderungen

Abhängig von der Komplexität des Modells kann ein einzelner Lauf zwischen:

- **10⁴ CPU-Stunden** (einfachere Modelle)
- **10⁶ CPU-Stunden** (komplexe Modelle)

erfordern. Einfachere Modelle, oft zu Testzwecken erstellt, können auf deutlich kürzeren Zeitskalen ausgeführt werden.

---

## Modellproduktion und -nutzung

### Entwicklungsskala

Modellproduktion und -nutzung in dieser Domäne involvieren sowohl kleine als auch groß angelegte Bemühungen.

### CRPropa-Kollaboration

**CRPropa** wird von einer internationalen Kollaboration von etwa **20 Forschenden** gepflegt.

Der Code ist **öffentlich**, komplett mit:

- Beispielen
- Handbüchern
- **Help Desk**, betrieben von den Entwicklern auf Rotationsbasis

### Nutzerbasis

Seine Nutzerbasis umfasst **über 100 Forschende**, und der Code wird verwendet für:

- Theoretische Studien
- Beobachtungsanalysen mit Instrumenten wie **Auger** und **IceCube**

---

## Ähnliche öffentliche Codes

Ähnliche öffentliche Codes haben vergleichbare Entwicklungs- und Nutzer-Engagement-Niveaus:

### GALPROP und DRAGON

- Fokussieren auf die Modellierung der Propagation und Wechselwirkung kosmischer Strahlung **in der Milchstraße**
- Verwenden **numerische Lösungen der Transportgleichung**

### CRPropa-Unterscheidung

- **CRPropa** ist im Gegensatz dazu zugeschnitten auf **galaktische und extragalaktische Propagation**
- Verwendet einen **Monte-Carlo-Ansatz**

### CORSIKA

- **CORSIKA** simuliert die Entwicklung von **kosmischen Strahlungs-Schauern in der Erdatmosphäre**
- Verwendet ebenfalls ein **Monte-Carlo-Framework**

---

## Showcase-Modelle

Die von **RUB-A** für das Projekt ausgewählten Astroteilchen-Modelle fokussieren auf:

- **Teilchenpropagation**
- **Beobachtbare Spektren unter spezifischen Annahmen**

Bereitstellung von Templates für eine breitere Verbreitung des DEMOS-Standards im Feld.

### Modell-Diversität

Die Modelle decken diverse Quellen und Teilchentypen ab und bieten verschiedene Darstellungen:

- **Parametrische Verteilungen** im Histogrammformat
- **Analytische Formulierungen**

### Spezifische Modelle

1. **γ-Strahlen aus Jets** der Seyfert-II-Galaxie NGC 1068[^1]
2. **Kosmische-Strahlen-Transport** in der Central Molecular Zone mit anisotroper Diffusion[^2]
3. **Kosmische-Strahlen-Elektronen** in der frontal ausgerichteten Galaxie M51 durch Synchrotronstrahlung[^3]
4. **Multi-Messenger-Modell**, das Active-Galactic-Nuclei-Corona und Starburst-Emissionen integriert[^4]
5. **Analytisches galaktisches Zentrum Magnetfeldmodell**, das kosmische-Strahlen-Propagation mit γ-Strahlen-Beobachtungen verknüpft[^5]

---

## Zusammenfassung

Astroteilchenphysik bietet einzigartige Modell-Sharing-Möglichkeiten:

✅ **Aktuelle Stärken**:

- Gut etablierte öffentliche Codes (CRPropa, GALPROP, CORSIKA)
- Internationale Kollaborationen (CRPropa: ~20 Entwickler, 100+ Nutzer)
- Öffentliche Dokumentation und Help Desks
- Multi-Messenger-Ansatz
- Breite Nutzerbasis über Theorie und Experiment hinweg

❌ **Aktuelle Herausforderungen**:

- Diverse rechnerische Anforderungen (10⁴ bis 10⁶ CPU-Stunden)
- Komplexe numerische Löser erfordern ausgeklügelte Parallelisierung
- Modelle reichen von einfach analytisch bis komplex 3D-numerisch
- Kein standardisiertes Format für Modellaustausch
- Schwierig, Modelle aus verschiedenen Codes zu kombinieren

🎯 **DEMOS-Vorteile**:

- Standardisiertes Format für sowohl analytische als auch histogramm-basierte Modelle
- Vergleich zwischen verschiedenen Propagationscodes ermöglichen
- Multi-Messenger-Analyse erleichtern
- Bessere Integration zwischen galaktischen und extragalaktischen Studien
- Verbesserte Reproduzierbarkeit für theoretische Vorhersagen
- Einfachere Kombination von Modellen für Instrumentendesign

Die Astroteilchenphysik-Community wird vom DEMOS-Standard profitieren, indem ein besserer Vergleich von Ergebnissen aus verschiedenen Codes ermöglicht wird und die Integration von Modellen über das gesamte Spektrum kosmischer Boten und Energieskalen hinweg erleichtert wird.

---

## Referenzen

[^1]: S. Salvatore et al., "Possible jet contribution to the γ-ray luminosity in NGC 1068," *Astron. Astrophys.*, vol. 687, p. A139, July 2024.

[^2]: J. Dörner et al., "Impact of Anisotropic Cosmic-Ray Transport on the Gamma-Ray Signatures in the Galactic Center," *Astrophys. J.*, vol. 965, no. 2, p. 180, April 2024.

[^3]: J. Dörner et al., "Cosmic-ray electron transport in the galaxy M 51," *Astron. Astrophys.*, vol. 669, p. A111, January 2023.

[^4]: B. Eichmann et al., "Solving the Multimessenger Puzzle of the AGN-starburst Composite Galaxy NGC 1068," *Astrophys. J.*, vol. 939, no. 1, p. 43, November 2022.

[^5]: M. Guenduez et al., "A novel analytical model of the magnetic field configuration in the Galactic center," *Astron. Astrophys.*, vol. 644, p. A71, December 2020.
