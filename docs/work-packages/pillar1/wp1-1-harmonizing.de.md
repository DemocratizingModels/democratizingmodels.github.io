---
title: WP1.1 - Harmonisierung verschiedener Modelle
---

# WP1.1: Harmonisierung verschiedener Modelle

Das Ziel dieses Arbeitspakets ist es, die **Bausteine und elementaren Operationen** zu definieren, die für die Erstellung einer breiten Palette von Modellen über die verschiedenen ErUM-Forschungsdomänen hinweg erforderlich sind.

---

## Übersicht

Aufbauend auf Techniken aus RooFit/HS3 wird das zentrale Element des DEMOS-Standards ein **Dataflow-ähnlicher Graph** sein: jeder Baustein kann seine Ausgabe als Eingabe für einen anderen Block bereitstellen. Diese flexible Kette von Berechnungen ermöglicht die Konstruktion komplexer Wahrscheinlichkeitsverteilungen, Likelihood-Funktionen sowie Priors und Posteriors für Bayessche Inferenz.

---

## Wichtige technische Anforderungen

### Strukturelle Flexibilität

Der DEMOS-Standard muss ausreichend flexibel sein, um die Bedürfnisse verschiedener Felder zu unterstützen:

- **Komplexe Zahlen**: Essentiell in mehreren Bereichen einschließlich Hadronenphysik und Quantenmechanik
- **Vektoren und Matrizen**: Reguläre Primitive für Übergangs-Amplituden in Hadronen- und Kernphysik
- **Dataflow-Graphen**: Ermöglichen die Konstruktion komplexer Objekte aus einfacheren durch mathematische Operationen
- **Lazy Evaluation**: Speicherbelegung und Berechnungen müssen zur Parsing-Zeit ableitbar sein

### Statische Kompilierungskompatibilität

Eine wichtige Anforderung liegt in den statischen Eigenschaften von Modellen:

- Speicherbelegung muss zur Parsing-Zeit bestimmbar sein
- Lazy-Berechnungen müssen mit statisch typisierten Sprachen wie C++ kompatibel sein
- Frühere TUDO-Erfahrung mit der HS3 ROOT-Engine wird helfen, diese Herausforderungen zu bewältigen

---

## Hauptmeilensteine

### M1: Fixierung der strukturellen Freiheit (2026.Q1)

**Prioritätsaufgabe**: Geleitet durch sorgfältige Bewertung konsortiumsbereitgestellter Anwendungsfälle

**Ansatz**:
- Jede Forschungsdomäne entwickelt eine Zusammenfassung der Modellmerkmale
- Domänenspezifische Modellformat-Vorschläge bis 2025.Q4 erstellt
- Workshop in 2026.Q1 zur Überprüfung und Finalisierung des Designs

**Verantwortlichkeiten**:
- **HZDR**: Laserphysik (LP)
- **RUB-A**: Astroteilchenphysik (AP)
- **RUB-N**: Kernphysik (NP)
- **RUB-H**: Hadronenphysik (HP)
- **TUDO**: Teilchenphysik (PP)
- **TUM**: Neutrinophysik (NuP)

### Katalog der Basis-Primitive

Die Gestaltung des DEMOS-Standards wird durch Anwendungsfälle gesteuert: Gruppen werden beginnen, bedeutende Modelle aus ihrer Domäne anzupassen, sobald das Projekt startet. Abschnitt 3.3.2 des Antrags detailliert die Modelle, die definieren werden:

- Strukturelle Merkmale
- Katalog der Basis-Primitive
- Domänenspezifische Rechenblöcke

---

## Domänenspezifische Vorschläge

### Workshop (2026.Q1)

Ein umfassender Workshop wird abgehalten, um:

- Domänenspezifische Vorschläge zu überprüfen
- Das Design des DEMOS-Standards zu finalisieren
- Prioritäre domänenspezifische Komponenten zu identifizieren
- Konsens über strukturelle Merkmale zu etablieren

Der Workshop wird Vertreter aller ErUM-Domänen zusammenbringen, um sicherzustellen, dass der Standard diversen Bedürfnissen gerecht wird und gleichzeitig Konsistenz wahrt.

---

## Erweiterungsmechanismus

### Kohärenter Mechanismus zum Hinzufügen von Primitiven (2028.Q3)

Ein Schlüsselmerkmal des DEMOS-Standards wird ein **kohärenter Mechanismus zum Hinzufügen neuer Primitive** sein, der sicherstellt:

- Anpassungsfähigkeit an sich entwickelnde Bedürfnisse verschiedener Felder
- Unterstützung für domänenspezifische Erweiterungen
- Fähigkeit, benutzerdefinierte Verteilungen und Funktionen zu referenzieren
- Framework für Tests und zukünftige Erweiterungen

Dieser Mechanismus ist kritisch für langfristige Nachhaltigkeit und Community-Akzeptanz.

---

## Metadaten und Attribution

### Publikationsverknüpfung via DOIs

Der Standard wird umfassende Metadaten beinhalten:

- **DOIs**: Verknüpfung mit Publikationen für Provenienz und Attribution
- **Versionsinformationen**: Verfolgung der Modellentwicklung im Laufe der Zeit
- **Modellspezifische Metadaten**: Berücksichtigung domänenspezifischer Bedürfnisse

Beispiele domänenspezifischer Metadaten:
- Gitterabstand für Gitter-QCD-Modelle
- Quarkmassen für Kernphysik
- Detektorkonfiguration für experimentelle Modelle
- Cutoff-Parameter für effektive Feldtheorien

### Versionierungsstrategie

Der DEMOS-Standard wird ein robustes Versionierungssystem implementieren:

- Semantische Versionierung (MAJOR.MINOR.PATCH)
- Garantien für Abwärtskompatibilität
- Migrationsleitfäden zwischen Versionen
- Ausmusterungsrichtlinien

---

## Nicht-serialisierbare Modelle

### MaaS-Protokoll-Integration

Der Standard wird beschreiben, wie nicht-serialisierbare Blöcke registriert werden:

- Container-orientierte Arbeit von MPP (WP1.3)
- MaaS-Protokoll ausführlich im Standard dargelegt (2027.Q2)
- UUID-basiertes Referenzierungsschema
- Kommunikationsprotokoll-Spezifikationen

---

## Dokumentations-Ergebnisse

### Webbasierte Dokumentation (2026.Q2)

Umfassende Dokumentation mit Versionierung, abgestimmt auf das Format:

- **Standardspezifikation**: Vollständige technische Referenz
- **Baustein-Katalog**: Alle primitiven Operationen
- **Domänenspezifische Leitfäden**: Feldspezifische Konventionen
- **Beispiele und Tutorials**: Praktische Serialisierungsleitfäden
- **API-Referenz**: Für alle drei Engines
- **Best Practices**: Community-Richtlinien

### Format und Struktur

Die Dokumentation wird sein:

- **Maschinenlesbar**: JSON-Schema und formale Spezifikationen
- **Menschenlesbar**: Klare Erklärungen mit Beispielen
- **Interaktiv**: Live-Beispiele wo möglich
- **Versioniert**: Abgestimmt auf Standard-Releases

---

## Anwendungsfall-Validierung

### Entwicklung durch reale Modelle vorantreiben

Die Standardentwicklung wird kontinuierlich gegen reale Anwendungsfälle validiert:

1. **Frühe Adoption**: Gruppen beginnen sofort mit der Serialisierung von Modellen
2. **Feedback-Schleife**: Probleme identifiziert und iterativ adressiert
3. **Domänenübergreifende Tests**: Sicherstellen der Kompatibilität über Felder hinweg
4. **Community-Input**: Regelmäßige Einholung von Nutzerfeedback

### Showcase-Modelle

Bedeutende Modelle aus jeder Domäne werden den Standard testen:

- **Teilchenphysik**: Higgs-Entdeckungsmodelle, HistFactory-Likelihoods
- **Hadronenphysik**: Partialwellen-Zerlegungen, Kaskadenzerfälle
- **Kernphysik**: Zwei-Nukleonen- und Drei-Nukleonen-Potentiale
- **Neutrinophysik**: Oszillationsmodelle mit Detektorantwort
- **Astroteilchenphysik**: Kosmische Strahlenausbreitung, Quellenmodelle
- **Laserphysik**: Streuquerschnitte, Strukturfaktoren

---

## Technische Herausforderungen

### Unterstützung komplexer Zahlen

Implementierung komplexer Zahlen erfordert:

- Native Unterstützung in C++ (std::complex)
- Effiziente Darstellung in Python (complex-Typ)
- Julias native Unterstützung komplexer Zahlen
- Konsistentes Serialisierungsformat (Real-/Imaginärteil-Paare)

### Matrixoperationen

Herausforderungen für Matrix-/Vektor-Primitive:

- **Speicher-Layout**: Row-major vs. column-major
- **Sparse vs. Dense**: Optimierung für verschiedene Anwendungsfälle
- **Dimensionalität**: Unterstützung für N-dimensionale Arrays
- **Broadcasting**: Konsistente Regeln über Sprachen hinweg

### Statische Typisierungsbeschränkungen

Statische C++-Typisierung stellt Herausforderungen dar:

- Typauflösung zur Parse-Zeit
- Template-Instantiierungsstrategien
- Laufzeit-Polymorphismus wo benötigt
- Management des Kompilierungs-Overheads

---

## Zusammenarbeit und Kommunikation

### Gruppenübergreifende Koordination

Regelmäßige Koordinationsmechanismen:

- **Monatliche Meetings**: Fortschrittsupdates und Problemlösung
- **GitHub-Issues**: Technische Diskussionen und Entscheidungen
- **Mailingliste**: Ankündigungen und allgemeine Kommunikation
- **Slack/Mattermost**: Echtzeit-Zusammenarbeit

### Community-Engagement

Breitere Community-Beteiligung:

- **Nutzerumfragen**: Anforderungen und Feedback sammeln
- **Beta-Testing**: Early-Adopter-Programm
- **Hackathons**: Intensive Entwicklungs-Sprints
- **Konferenzpräsentationen**: Bewusstsein schaffen

---

## Risikominderung

### Identifizierte Risiken

| Risiko | Minderungsstrategie |
|------|-------------------|
| Scope Creep durch diverse Anforderungen | Klares Priorisierungsframework, phasenweise Implementierung |
| Inkompatible Domänenbedürfnisse | Frühe Identifikation durch Workshops, Erweiterbarkeits-Mechanismen |
| Statische Typisierungsbeschränkungen in C++ | Nutzung der TUDO-Expertise, Prototyp-Tests |
| Mangelnde Community-Akzeptanz | Kontinuierliches Engagement, Führungspositionen in Kollaborationen |

---

## Erfolgsmetriken

WP1.1 wird bewertet anhand:

✅ **Strukturelle Freiheit fixiert** (2026.Q1): Klare Spezifikation der Modellstruktur
✅ **Domänenvorschläge vollständig** (2025.Q4): Alle Domänen reichen Vorschläge ein
✅ **Workshop-Erfolg** (2026.Q1): Konsens über Kernmerkmale erreicht
✅ **Primitive-Katalog** (2026.Q2): Umfassende Liste dokumentiert
✅ **Erweiterbarkeits-Mechanismus** (2028.Q3): Framework zum Hinzufügen von Primitiven betriebsbereit
✅ **Dokumentation Live** (2026.Q2): Webbasierte Docs verfügbar
✅ **10+ Modelle serialisiert**: Diverse Beispiele demonstrieren Flexibilität

---

## Zusammenfassung der Ergebnisse

### Bis 2026.Q2

- ✓ Strukturelle Freiheit fixiert
- ✓ Domänenspezifische Vorschläge überprüft
- ✓ Workshop mit Design-Konsens abgeschlossen
- ✓ Katalog der Basis-Primitive definiert
- ✓ Webbasierte Dokumentation veröffentlicht
- ✓ Metadaten-Schema spezifiziert

### Bis 2027.Q2

- ✓ MaaS-Protokoll im Standard dargelegt
- ✓ Erste Charge domänenspezifischer Modelle serialisiert
- ✓ Validierungs-Framework betriebsbereit

### Bis 2028.Q3

- ✓ Kohärenter Mechanismus zum Hinzufügen von Primitiven vollständig
- ✓ Umfassender Satz von Showcase-Modellen verfügbar
- ✓ Standard-Versionierungssystem etabliert
- ✓ Community-Akzeptanz demonstriert

---

## Personalzuweisung

**Gesamt**: 0,7 Personenjahre

### Verteilung nach Domäne

- HZDR (LP): 0,1 PJ
- RUB-A (AP): 0,1 PJ
- RUB-N (NP): 0,1 PJ
- RUB-H (HP): 0,1 PJ
- TUDO (PP): 0,2 PJ
- TUM (NuP): 0,1 PJ

---

## Integration mit anderen Arbeitspaketen

### Abhängigkeiten

- **WP1.2 (Engines)**: Standard muss in allen drei Sprachen implementierbar sein
- **WP1.3 (MaaS)**: Protokoll für nicht-serialisierbare Modelle
- **WP2.1 (Front-end)**: Dokumentationsportal-Integration
- **WP3.2 (Präsentation)**: Anwendungsfälle treiben Anforderungen

### Ausgaben verwendet von

- Alle Engine-Implementierungen (WP1.2)
- Modell-Validierungswerkzeuge (WP2.2)
- Community-Dokumentation (WP3.1)
- Modellgalerie-Beispiele (WP2.1)

---

## Langfristige Vision

Die Harmonisierungsarbeit etabliert die Grundlage für:

- **Interdisziplinäre Zusammenarbeit**: Gemeinsame Sprache für Modelle
- **Reproduzierbarkeit**: Vollständige Modellspezifikationen
- **Bewahrung**: Langfristige Zugänglichkeit von Forschungsmodellen
- **Bildung**: Zugängliche Beispiele für Studenten
- **Innovation**: Einfache Kombination und Erweiterung von Modellen

Durch sorgfältiges Design eines flexiblen aber strukturierten Standards ermöglicht WP1.1 dem gesamten DEMOS-Ökosystem zu gedeihen und der ErUM-Community für Jahrzehnte zu dienen.

---

## Nächste Schritte

- Erkunden Sie [WP1.2: Engines →](wp1-2-engines.md), um zu sehen, wie der Standard implementiert wird
- Erfahren Sie mehr über [WP1.3: Container (MaaS) →](wp1-3-containers.md) für komplexe Modelle
- Zurück zur [Säule 1 Übersicht →](index.md)
