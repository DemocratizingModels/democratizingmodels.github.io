---
title: WP1.2 - Engines
---

# WP1.2: Engines

Die Implementierung des DEMOS-Standards beinhaltet die Entwicklung von **praktischen Rechenwerkzeugen**, um den Standard in Engines zu übersetzen, die in der Lage sind, Modelle effektiv zu verarbeiten und auszuwerten. Dieses Arbeitspaket ist entscheidend für die Aufrechterhaltung der Gesamtkohärenz des Projekts.

---

## Übersicht

Jedes neue Feature, das in den Standard der Modellierungssprache eingeführt wird, wird von folgenden Begleitmaßnahmen begleitet:

- Implementierung in allen drei Engines (C++, Python, Julia)
- Unit Tests zur Validierung von Eigenschaften
- Sprachübergreifende Konsistenzprüfungen
- Performance-Benchmarks

Die Engines stellen sicher, dass der DEMOS-Standard nicht nur eine Spezifikation auf dem Papier ist, sondern ein lebendiges, nutzbares Werkzeug für die Forschungsgemeinschaft.

---

## Warum drei Sprachen?

Die Wahl von **C++**, **Python** und **Julia** spiegelt unsere Erwartungen für die langfristige Entwicklung des ErUM-Feldes wider:

### C++ Engine

**Rationale**:
- Integrale Rolle in Frameworks wie ROOT
- Performance-Vorteile für rechenintensive Aufgaben
- Starke Präsenz in etablierten Forschungsumgebungen
- Wesentlich für Rückwärtskompatibilität

**Hauptbenutzer**: ATLAS, CMS, LHCb, Belle II, Legacy-Analysis-Frameworks

### Python Engine

**Rationale**:
- Meistverwendete Sprache in wissenschaftlichem Computing heute
- Umfangreiche Bibliotheken in Industrie und Wissenschaft verbreitet
- Zugänglichkeit für diverse Benutzerhintergründe
- Einfaches Prototyping und interaktive Exploration

**Hauptbenutzer**: Moderne Analysis-Frameworks, Machine-Learning-Pipelines, neue Benutzer

### Julia Engine

**Rationale**:
- Zukunftsorientierte Features (Multiple Dispatch, effiziente Numerik)
- Gut positioniert für zukünftige forschungsorientierte Entwicklung
- Kombiniert Performance mit Benutzerfreundlichkeit
- Wachsende Akzeptanz im wissenschaftlichen Computing

**Hauptbenutzer**: Nächste Generation von Frameworks, Performance-kritische Anwendungen

---

## Einheitliche Engine-Struktur

Alle drei Engines folgen einem **gemeinsamen architektonischen Muster** mit drei Hauptkomponenten:

### 1. Parsen und In-Memory-Darstellung (2026.Q3)

**Funktionalität**:
- JSON-Dateien gemäß DEMOS-Standard lesen
- Rechenerische Bausteine identifizieren
- Ihre Beziehungen und Parameter detaillieren
- Relationale Karte des Modells konstruieren

**Technische Anforderungen**:
- Effizientes JSON-Parsing
- Validierung gegen Schema
- Fehlerbehandlung und Diagnostik
- Speichereffiziente Darstellung

### 2. Rechnerische Bausteine (2027.Q1)

**Implementierung als austauschbare Module**:
- Domain-spezifische Erweiterungen unterstützt
- Konsistente Schnittstelle über Blöcke hinweg
- Typsicherheit wo anwendbar
- Performance-Optimierung

**Kategorien von Blöcken**:
- Wahrscheinlichkeitsverteilungen
- Mathematische Operationen
- Spezialfunktionen
- Matrix-/Vektor-Operationen
- Komplexe Zahlenarithmetik
- Domain-spezifische Funktionen

### 3. Materialisierung (2027.Q1)

**Übersetzung des Lazy Computation Graph**:
- Korrekte Bausteine instantiieren
- Abhängigkeiten auflösen
- Ausführungspfade optimieren
- Verschiedene rechnerische Backends handhaben

**Backend-Unterstützung**:
- Native Implementierungen
- Just-in-time-Kompilation (wo verfügbar)
- GPU-Beschleunigung (zukünftige Überlegung)
- Automatische Differenziation-Unterstützung

---

## C++ Engine

**Leitung**: TUDO
**Zeitplan**: 2027.Q1
**Basis**: ROOT/RooFit HS3 Framework

### Technischer Ansatz

Bauen auf dem bestehenden HS3 Framework auf, um Duplizierung zu minimieren und die Funktionalität zu erweitern:

- **JSON-Parsing**: Bereits verfügbar über `RooJSONFactoryWSTool` (integriert in ROOT von TUDO)
- **RooFit-Integration**: Bestehende Bausteine nutzen
- **Erweiterung**: Neue strukturelle Komponenten hinzufügen

### Wichtigste Herausforderungen

#### Statische Typisierung und Kompilation

Die Unterstützung neuer struktureller Komponenten stellt Herausforderungen dar aufgrund von:

- Strikten Typ-Anforderungen
- Kompilierzeit-Auflösung
- Template-Instantiierungs-Komplexität

**Beispiele neuer Komponenten**:
- Komplexe interferierende Amplituden
- Matrix-Operationen auf Matrizen beliebiger Größe
- Vektor-wertige Funktionen

#### Erweiterung der Bausteine

Zahlreiche rechnerische Elemente müssen hinzugefügt werden:

- Funktionen jenseits des aktuellen RooFit-Satzes
- Verteilungen für spezifische Domains
- Matrix-/Vektor-Operationen
- Komplexe Zahlenunterstützung

### JGU-Beiträge

**Verantwortung**: Hinzufügen von rechnerischen Bausteinen zu ROOT/RooFit

**Spezifische Aufgaben**:
- Domain-spezifische Funktionen implementieren
- Neue Verteilungstypen hinzufügen
- RooFit-Funktionalität erweitern
- Implementierungen testen und validieren

### MaaS Protocol-Unterstützung

Native Unterstützung für Kommunikationsprotokoll mit containerisierten Modellen:

- Client-Implementierung für Zugriff auf Remote-Modelle
- Server-Implementierung für Exponierung von C++-Modellen
- Niedriger Overhead-Binär-I/O
- Plattformübergreifende Kompatibilität

---

## Python Engine

**Leitung**: LMU (mit TUM und SC)
**Zeitplan**: 2027.Q1
**Basis**: PyHF Expertise

### Technischer Ansatz

#### In-Memory-Darstellung

In Python verwaltet und nutzt seine dynamischen Fähigkeiten:

- Flexible Datenstrukturen
- Einfache Introspektion
- Interaktive Entwicklung
- Dynamische Typsystem-Vorteile

#### Bausteine als Plugins

Mit mehreren rechnerischen Backends:

- **JAX**: Für Just-in-time-Kompilation und automatische Differenziation
- **Numba**: Für JIT-Kompilation von numerischem Code
- **SymPy**: Für symbolische Berechnungen

Dieser Multi-Backend-Ansatz stellt sicher:

- Performance-Optimierung
- Flexibilität im Computingstil
- Gradient-Berechnung für Inferenz
- Symbolische Manipulation wenn nötig

#### Materialisierungs-Strategie

Verbinde den Lazy Computation Graph mit gewählten rechnerischen Backends:

- Wähle optimales Backend für jede Operation
- Minimiere Datenbewegung
- Optimiere Ausführungsreihenfolge
- Unterstütze verschiedene Inferenz-Methoden

### Team-Expertise

**Lorentz Gartner** (LMU PhD-Kandidat):

- Perfekte Eignung für das Projekt
- Umfangreiche Python-Entwicklungserfahrung
- Zeitplan stimmt mit 3-jährigem Projekt überein (Start Oktober 2025)
- Expertise in Flavor-Physik und Belle II Experiment
- Wird Verbindung zwischen DEMOS-Standard und b-Anomalie-Modellen vorantreiben

**TUM und SC Partner**:

- Lukas Heinrich (TUM): PyHF Co-Creator
- Giordon Stark (SC): PyHF Wartung
- Kombinierte tiefe Expertise in statistischer Modellierung

### Integration mit bestehenden Tools

Die Python Engine wird sich nahtlos integrieren mit:

- PyHF Modellen (HistFactory Format)
- JAX Ökosystem
- scikit-hep Tools
- Jupyter Notebooks
- Allgemeinen Python-Analysis-Frameworks

---

## Julia Engine

**Leitung**: HZDR, RUB-H, TUDO, MPP
**Zeitplan**: 2027.Q1
**Basis**: Mehrere Pilotprojekte

### Grundlage und Prototypen

#### Bestehende Arbeiten

- **HS3 Engine Prototype**: MSc Projekt bei TUDO und MPP (Robin Pelkner)
- **Amplitude Serialisierung**: Pilotprojekt bei RUB-H
- **Computational Graph Optimierung**: Umfangreiche Arbeiten bei HZDR (Anton Reinhard Diplom)

Diese Prototypen demonstrieren Machbarkeit und informieren Design-Entscheidungen.

### Technischer Ansatz

Nutzen Julias einzigartige Features:

#### Multiple Dispatch

- Natürliche Darstellung mathematischer Operationen
- Typ-basierte Spezialisierung
- Erweiterbarkeit ohne Modifikation
- Sauberer, lesbarer Code

#### Modulares Package-Ökosystem

**Separate Packages für verschiedene Belange**:

- JSON-Parsing Package
- In-Memory-Darstellung Package
- Rechnerische Bausteine Packages (domain-spezifisch)
- Meta-Package integriert alles

**Vorteile**:
- Unabhängige Entwicklung und Versionierung
- Einfache Erweiterbarkeit durch Community
- Minimale Abhängigkeiten pro Package
- Klare Trennung der Belange

#### Symbolische und numerische Methoden

Effiziente Kombination von:

- Symbolischer Differenziation
- Numerischer Optimierung
- Just-in-time-Kompilation
- Natürlicher Performance

### Design-Prioritäten

1. **Erweiterbarkeit**: Einfach neue Bausteine hinzufügen
2. **Performance**: Native Julia Geschwindigkeit
3. **Typsicherheit**: Julias Typsystem nutzen
4. **Interoperabilität**: Gut mit anderen Julia Packages zusammenarbeiten

### Anwendungsfälle

Julia Engine besonders geeignet für:

- Komplexe mathematische Modelle
- Performance-kritische Berechnungen
- Forschungsorientierte Entwicklung
- Zukünftige Framework-Entwicklung

---

## Sprachübergreifende Konsistenz

### CI/CD-basierte Validierung (2027.Q4)

Umfassendes Continuous Integration System:

- **Automatisierte Tests**: Jeder Commit löst Tests aus
- **Sprachübergreifende Tests**: Identische Modelle in allen Engines bewertet
- **Konsistenzprüfungen**: Numerische Übereinstimmung verifiziert
- **Performance-Benchmarks**: Regressionsverfolgung

### Downstream Tests (2028.Q1)

**Test Suite Design**:

- Referenzmodelle mit bekannten Ausgaben
- Toleranz-Spezifikationen
- Edge-Case-Abdeckung
- Performance-Baselines

**Test-Kategorien**:

1. **Parsing Tests**: Gültige und ungültige JSON
2. **Evaluierungs-Tests**: Numerische Genauigkeit
3. **Gradient-Tests**: Automatische Differenziation Konsistenz
4. **Integrations-Tests**: Komplette Workflow-Validierung

### Test-Abdeckungs-Ziel

**Ziel**: 70% Code-Abdeckung bis 2028.Q1

**Strategie**:
- Unit Tests für individuelle Bausteine
- Integrations-Tests für Workflows
- Regressions-Tests für Bug Fixes
- Domain-spezifische Validierungs-Tests

---

## Standard-Softwareentwicklungspraktiken

Alle Engines folgen:

### Versionskontrolle

- Git Repositories (GitHub/GitLab)
- Semantische Versionierung
- Tagged Releases
- Changelog-Wartung

### Dokumentation

- API-Dokumentation (automatisch generiert)
- Benutzerhandbücher
- Beispiele und Tutorials
- Entwicklungshandbücher

### Code-Qualität

- Linting und Formatting-Tools
- Code-Review Anforderungen
- Style Guide Einhaltung
- Abhängigkeitsverwaltung

### Test-Infrastruktur

- Unit Test Frameworks
- Integrations-Test Suites
- Continuous Integration
- Coverage-Berichterstattung

---

## Performance-Überlegungen

### Optimierungsstrategien

Verschiedene Engines nutzen unterschiedliche Ansätze:

#### C++ Optimierung

- Template Metaprogrammierung
- Kompilierzeit-Optimierungen
- SIMD Vektorisierung
- Effiziente Speicherverwaltung

#### Python Optimierung

- JIT-Kompilation (JAX, Numba)
- Vektorisierte Operationen (NumPy)
- Cython für kritische Pfade
- Lazy Evaluation

#### Julia Optimierung

- Native Just-in-time Kompilation
- Typ-Spezialisierung
- Automatische Optimierung
- LLVM Backend

### Benchmarking

Regelmäßige Performance-Überwachung:

- Ausführungszeit-Verfolgung
- Speichernutzungs-Profiling
- Vergleich über Engines
- Regressions-Erkennung

---

## Interoperabilität und Konvertierung

### Sprachübergreifende Modell-Übertragung

Modelle serialisiert im DEMOS-Standard können:

- In jeder Engine geladen werden
- Konsistent ausgewertet werden
- Über Sprachen kombiniert werden
- In jedem Framework erweitert werden

### Konvertierungs-Tools

**Aus bestehenden Formaten**:

- PyHF JSON → DEMOS (LMU)
- HS3 → DEMOS (TUDO)
- ROOT Workspaces → DEMOS (TUDO)
- Domain-spezifische Formate → DEMOS (verschiedene)

**Zu anderen Formaten** (wenn nützlich):

- DEMOS → Visualisierungsformate
- DEMOS → Dokumentationsformate
- DEMOS → Legacy-Formate (für Kompatibilität)

---

## Gemeinsame Entwicklungs-Vorteile

### Gemeinsame Infrastruktur

Alle Engine-Teams profitieren von:

- Gemeinsame Test Suite
- Gemeinsame Benchmarks
- Design Pattern Austausch
- Zusammenarbeit bei Problemlösung

### Best Practices Austausch

- Code Review über Teams hinweg
- Architektur-Diskussionen
- Performance-Optimierungstechniken
- Bug-Fix-Verbreitung

### Konsistente Fortschritte

Gleichmäßige Verteilung von Personalkraft stellt sicher:

- Kein einzelner Ausfallpunkt
- Mehrere Validierungsquellen
- Integration vielfältiger Perspektiven
- Reduziertes Verzögerungsrisiko

---

## Risikominderung

### Identifiziertes Risiko: Verzögerte Engine-Lieferung

**Risiko**: Mögliche Verzögerungen bei der Lieferung des vollständig funktionalen Stacks für eine Engine

**Bewertung**: Begrenzt - würde das Gesamtprojekt nicht erheblich beeinflussen

**Minderung**:

1. **Alternative Stacks verfügbar**: Andere Engines dienen als Validierung
2. **Phasierte Lieferung**: Kernfunktionalität priorisiert
3. **Cross-Team-Unterstützung**: Teams unterstützen sich gegenseitig
4. **Regelmäßige Fortschrittsüberprüfungen**: Frühzeitige Erkennung von Problemen

### Weitere Risiken und Minderungsmaßnahmen

| Risiko | Minderung |
|--------|-----------|
| Inkompatible Sprachfeatures | Frühes Prototyping, Standard-Design-Flexibilität |
| Performance-Engpässe | Profiling, Optimierung, alternative Backends |
| Abhängigkeitskonflikte | Minimale Abhängigkeiten, Versionsverwaltung |
| Wartungslast | Klarer Code, Dokumentation, Community-Engagement |

---

## Personalkraft-Zuteilung

**Gesamt**: 2,05 Personenjahre

### Nach Engine

- **C++ Engine**: 0,15 py + 0,2 py (JGU) = 0,35 py
- **Python Engine**: 0,7 py
- **Julia Engine**: 0,4 py + 0,2 py + 0,1 py + 0,2 py = 0,9 py

### Nach Institution

- **TUDO**: 0,15 py (C++ Leitung)
- **JGU**: 0,2 py (C++ Bausteine)
- **LMU**: 0,7 py (Python Leitung)
- **HZDR**: 0,4 py (Julia Beiträge)
- **RUB-H**: 0,1 py (Julia Prototype)
- **TUDO**: 0,2 py (Julia HS3 Prototype)
- **MPP**: 0,2 py (Julia HS3 Prototype)
- **TUM**: 0,1 py (Python Unterstützung)

---

## Meilensteine

### M3: Engines Unterstützen Verschachtelte Konstruktionen (2027.Q1)

Alle drei Engines können:
- Komplexe DEMOS-Modelle parsen
- Verschachtelte Strukturen instantiieren
- Wahrscheinlichkeitsverteilungen auswerten
- Domain-spezifische Primitive handhaben

### M7: Validierung und Tests Abgeschlossen (2028.Q1)

- CI/CD-Pipeline operativ
- Sprachübergreifende Tests bestanden
- 70%+ Test-Abdeckung erreicht
- Performance-Benchmarks etabliert

---

## Zusammenfassung der Liefergegenstände

### Bis 2026.Q3

- ✓ Parsing-Komponenten implementiert
- ✓ In-Memory-Darstellungen designed
- ✓ Grundlegende JSON-Validierung funktioniert

### Bis 2027.Q1

- ✓ Alle drei Engines unterstützen verschachtelte Modelle
- ✓ Kern-Bausteine implementiert
- ✓ Materialisierung funktioniert
- ✓ Grundlegende Beispiele funktionsfähig

### Bis 2027.Q4

- ✓ CI/CD-basierte Validierung operativ
- ✓ Umfassende Test-Suites vorhanden
- ✓ Domain-spezifische Blöcke hinzugefügt

### Bis 2028.Q1

- ✓ Sprachübergreifende Downstream-Tests bestanden
- ✓ 70% Test-Abdeckung erreicht
- ✓ Performance-Optimierung abgeschlossen
- ✓ Dokumentation veröffentlicht

---

## Langfristige Wartung

### Nachhaltigkeitsstrategie

- Klares Governance-Modell
- Community Beitrag Richtlinien
- Regelmäßiger Release-Zeitplan
- Rückwärtskompatibilität-Politik
- Veraltungs-Verfahren

### Community-Engagement

- Entwickler-Mailing-Liste
- GitHub/GitLab Issue Tracking
- Beitrag Richtlinien
- Verhaltenskodex
- Regelmäßige Entwicklertreffen

---

## Integration mit anderen Arbeitspaketen

### Eingaben von

- **WP1.1**: Standard-Spezifikation, Primitives-Katalog
- **WP3.2**: Echte Modelle zum Testen
- **WP2.2**: Validierungsanforderungen

### Ausgaben zu

- **WP1.3**: Engines beinhalten MaaS Client/Server Funktionalität
- **WP2.1**: Engines treiben interaktive Exploration an
- **WP2.2**: Engines in Validierungs-Pipelines verwendet
- **WP3.1**: Engines in Tutorials demonstriert
- **WP3.2**: Engines evaluieren Showcase-Modelle

---

## Erfolgskriterien

WP1.2 wird erfolgreich sein, wenn:

✅ Alle drei Engines implementieren vollständig den DEMOS-Standard
✅ Sprachübergreifende numerische Konsistenz demonstriert
✅ CI/CD-Pipeline stellt fortgesetzte Kompatibilität sicher
✅ Test-Abdeckung übersteigt 70%
✅ Performance erfüllt oder übertrifft bestehende Tools
✅ Dokumentation ermöglicht unabhängige Nutzung
✅ Community-Adoption beginnt
✅ Domain-spezifische Modelle erfolgreich evaluiert

---

## Nächste Schritte

- Erfahren Sie mehr über [WP1.3: Containers (MaaS) →](wp1-3-containers.md) für komplexe Modell-Unterstützung
- Überprüfen Sie [WP1.1: Harmonizing →](wp1-1-harmonizing.md) um zu sehen, wie der Standard definiert wird
- Zurück zu [Pillar 1 Übersicht →](index.md)
