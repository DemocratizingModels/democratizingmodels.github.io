---
title: Säule 1 - Modellformat-Standardisierung
---

# Säule 1: Modellformat-Standardisierung

Die erste Schlüsselsäule dieser Initiative ist die Schaffung eines **einheitlichen, standardisierten Modellformats**, das den vielfältigen Bedürfnissen der ErUM-Forschungsgemeinschaft gerecht wird.

---

## Übersicht

Diese Säule konzentriert sich auf drei große Arbeitspakete:

### WP1.1: Harmonisierung verschiedener Modelle

Identifizierung wichtiger gemeinsamer Merkmale über ErUM-Forschungsdomänen hinweg und Standard-Rechenprimitive für jede Domäne, die den DEMOS-Standard strukturieren werden.

[Mehr erfahren →](wp1-1-harmonizing.md)

### WP1.2: Engines

Implementierung der DEMOS-Standard-Berechnungs-Engines in **C++**, **Python** und **Julia**, um breite Zugänglichkeit und Leistung zu gewährleisten.

[Mehr erfahren →](wp1-2-engines.md)

### WP1.3: Container (Models as a Service)

Für Modelle, die benutzerdefinierten komplexen Code oder Legacy-Systeme verwenden, Implementierung eines **Models as a Service (MaaS)**-Ansatzes unter Verwendung von Containerisierung und gut definierten Kommunikationsprotokollen.

[Mehr erfahren →](wp1-3-containers.md)

---

## Hauptziele

Die Ziele von Säule 1 sind:

1. **Einen gemeinsamen Standard definieren**, der die Vielfalt bestehender Ökosysteme respektiert
2. **Berechnungs-Engines implementieren** in mehreren Sprachen für breite Akzeptanz
3. **Komplexes Modell-Sharing ermöglichen** durch Containerisierung (MaaS)
4. **Statische Typkompatibilität sicherstellen** für Sprachen wie C++
5. **Interaktive Erkundungsmöglichkeiten** für Modelle bereitstellen

---

## Zeitplan

| Meilenstein | Quartal | Beschreibung |
|-----------|---------|-------------|
| **M1** | 2026.Q2 | Modellierungsstandard definiert: strukturelle Freiheit eingeschränkt, native Primitive identifiziert |
| **M3** | 2027.Q1 | Engines in Python, Julia und C++ unterstützen verschachtelte Modellkonstruktionen |
| **M4** | 2027.Q2 | Model as a Service Protokoll funktioniert, UUIDs generiert |
| **M7** | 2028.Q1 | Validierungswerkzeuge funktionieren, Engine-Tests decken 70%+ ab |

---

## Personalzuweisung

Gesamte Personenjahre für Säule 1: **3,4 Jahre**

| Arbeitspaket | Personenjahre |
|--------------|--------------|
| WP1.1 Harmonisierung | 0,7 |
| WP1.2 Engines | 2,05 |
| WP1.3 Container | 0,65 |

---

## Erwartete Ergebnisse

### Technische Ergebnisse

1. **DEMOS-Standardspezifikation**
   - JSON-basiertes Serialisierungsformat
   - Dataflow-Graph-Struktur
   - Katalog der Rechenprimitive
   - Metadaten-Schema
   - Versionierungsmechanismus

2. **Berechnungs-Engines**
   - C++-Engine (ROOT/RooFit-Integration)
   - Python-Engine (JAX/Numba-Backend)
   - Julia-Engine (symbolisch + numerisch)
   - Sprachübergreifende Validierungstests

3. **MaaS-Infrastruktur**
   - Kommunikationsprotokoll-Spezifikation
   - Container-Templates
   - Client/Server-Bibliotheken für alle Engines
   - UUID-basierte Modellreferenzierung

### Dokumentation

- Standardspezifikations-Dokumentation
- Engine-Implementierungsleitfäden
- Domänenspezifische Serialisierungsbeispiele
- MaaS-Protokoll-Dokumentation

---

## Konsortiumsbeiträge

### Leitende Institutionen

- **TUDO** - C++-Engine, HS3-Expertise
- **LMU** - Python-Engine, PyHF-Expertise
- **TUM** - Python-Engine-Entwicklung
- **SC** - PyHF-Wartung
- **HZDR** - Julia-Engine, Berechnungsgraphen
- **RUB-H** - Julia-Engine-Prototyp
- **MPP** - MaaS-Implementierung, Container
- **JGU** - C++-Implementierung (AmpTools)

---

## Integration mit bestehenden Tools

Der DEMOS-Standard wird integriert mit und erweitert:

- **ROOT/RooFit/RooStats** - Via C++-Engine und HS3-Kompatibilität
- **PyHF** - Via Python-Engine
- **HS3** - Als Grundlage und Erweiterung
- **Domänenspezifische Frameworks** - Via MaaS-Protokoll

---

## Erfolgskriterien

Säule 1 wird als erfolgreich betrachtet, wenn:

✅ DEMOS-Standardspezifikation ist vollständig und versioniert
✅ Alle drei Engines (C++, Python, Julia) unterstützen Kern-Primitive
✅ Sprachübergreifende Tests demonstrieren Konsistenz
✅ Mindestens 10 verschiedene Modelle mit dem Standard serialisiert
✅ MaaS-Protokoll ermöglicht containerisierte Modellintegration
✅ 70%+ Testabdeckung für Engine-Implementierungen
✅ Community-Feedback in Spezifikation integriert

---

## Nächste Schritte

Erkunden Sie die detaillierten Arbeitspakete:

- [WP1.1: Harmonisierung verschiedener Modelle →](wp1-1-harmonizing.md)
- [WP1.2: Engines →](wp1-2-engines.md)
- [WP1.3: Container (MaaS) →](wp1-3-containers.md)
