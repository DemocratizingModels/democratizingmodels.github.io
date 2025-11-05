---
title: WP1.3 - Containers (Models as a Service)
---

# WP1.3: Containers - Models as a Service (MaaS)

Auch bei einem gründlichen und breiten Modellstandard gibt es Grenzen für seine Kapazität über Komplexität, Sprachen und Betriebssysteme hinweg. Dieses Arbeitspaket behandelt Modelle, die **spezialisierte Codes, Daten oder Rechnerressourcen** benötigen, durch einen Containerisierungs- und Service-orientierten Ansatz.

---

## Übersicht: Das MaaS-Konzept

**Models as a Service (MaaS)** ermöglicht es Modellen, die nicht direkt serialisiert werden können, am DEMOS-Ökosystem teilzunehmen, indem:

- Sie in separaten Prozessen laufen
- Sie durch ein Standard-Protokoll kommunizieren
- Modell-Code unabhängig von Analysis-Code bleibt
- Mehrere Modelle mit variierenden Software-Anforderungen kombiniert werden

Dieser Ansatz nutzt zwei bewährte Technologien:

1. **Gut definierte Kommunikationsprotokolle** - Für langfristige Systemkompatibilität
2. **Software-Containerisierung** - Für Portabilität und Reproduzierbarkeit

---

## Wann MaaS verwenden

### Modelle, die MaaS benötigen

MaaS ist angemessen für Modelle, die:

- **Komplexe, benutzerdefinierte Codes verwenden**, die nicht leicht serialisierbar sind
- **Legacy-Software mit spezifischen Versionsanforderungen benötigen**
- **Spezialisierte Daten benötigen**, die nicht leicht verteilt werden
- **Spezifische Rechnerressourcen benötigen** (GPUs, großer Speicher, Cluster)
- **Komplexe Machine-Learning-Komponenten mit Framework-Abhängigkeiten haben**
- **Proprietäre oder lizenzierte Software nutzen**
- **Ungewöhnliche Programmiersprachen nutzen**, nicht im Core-Engines behandelt

### Native vs. MaaS Entscheidung

Der Entscheidungsbaum:

1. **Kann das Modell in DEMOS-Primitiven ausgedrückt werden?** → Native Serialisierung verwenden
2. **Ist es einfacher benutzerdefinierter Code in C++/Fortran?** → Leichte MaaS Wrapper verwenden
3. **Ist es komplex mit vielen Abhängigkeiten?** → Vollständige Containerisierung verwenden
4. **Benötigt es spezifische Infrastruktur?** → Remote MaaS Hosting verwenden

---

## Kommunikationsprotokolle

### Kommunikationsmodi

MaaS unterstützt mehrere Kommunikationsmuster:

#### Lokale Kommunikation (Inter-Process)

- Gleiche Maschine, verschiedene Prozesse
- Niedrige Latenz
- Kein Netzwerk-Overhead
- Einfaches Debugging

#### Verteilte Kommunikation

- **MPI**: Message Passing Interface für HPC-Cluster
- **IP Network**: Standard TCP/IP für Remote-Services
- **HTTP/REST**: Für Web-zugängliche Services

### Protocol-Anforderungen

Das MaaS-Protokoll muss unterstützen:

- **Dichte-Berechnungen**: P(x|parameters)
- **Zufällige Datengenerierung**: Sampling aus Verteilungen
- **Datenzugriff**: Abrufen vorab berechneter Datensätze
- **Metadata-Abfragen**: Modell-Informationen und Fähigkeiten
- **Parameter-Updates**: Modell-Parameter ändern
- **Gradient-Berechnung**: Wo anwendbar

---

## Protocol-Definition (2026.Q4)

**Leitung**: MPP

### Übersicht bestehender Standards

Eine umfassende Übersicht wird evaluieren:

- **Datenserialisierungsformate**: Protocol Buffers, MessagePack, FlatBuffers, Cap'n Proto
- **RPC Frameworks**: gRPC, Apache Thrift, ZeroMQ
- **Anforderungen**: Minimale Abhängigkeiten, sprachübergreifende Kompatibilität, niedriger Overhead

### Ausgewählter Ansatz

Kriterien für Auswahl:

1. **Minimale Abhängigkeiten**: Einfach in jeder Sprache zu implementieren
2. **Binäre Effizienz**: Niedriger Overhead für numerische Daten
3. **Sprachübergreifende Unterstützung**: Funktioniert mit C++, Python, Julia, Fortran
4. **Reif und stabil**: In der Produktion erprobt
5. **Open Source**: Kostenlos zu verwenden und zu ändern

### Protocol-Spezifikation

Die formale Definition wird beinhalten:

- **Nachrichtenformate**: Binäre Struktur-Spezifikationen
- **Kommunikationsmuster**: Request-Response, Streaming
- **Fehlerbehandlung**: Standardisierte Error-Codes und Nachrichten
- **Versionierung**: Protocol-Evolutions-Strategie
- **Authentifizierung**: Sicherheitsüberlegungen (optional)

---

## UUID-basiertes Referenzierungsschema

### Motivation

Modelle, die via MaaS gehostet werden, benötigen eindeutige, persistente Identifikatoren:

- **Universell einzigartig**: Keine zentrale Koordination erforderlich
- **Persistent**: Stabil über Modellversionen hinweg
- **Auflösbar**: Kann den Service-Endpunkt lokalisieren
- **Zitierbar**: Ermöglicht korrekte Attribution

### UUID-Struktur

**Format**: Standard UUID v4 mit Erweiterungen

```json
{
  "type": "maas_reference",
  "uuid": "550e8400-e29b-41d4-a716-446655440000",
  "endpoint": "https://models.example.org/uuid",
  "version": "1.2.3",
  "checksum": "sha256:...",
  "metadata": {
    "doi": "10.1234/example",
    "description": "...",
    "authors": ["..."]
  }
}
```

### Registry-Integration

MaaS Modelle werden im DEMOS-Registry registriert mit:

- UUID als primärer Identifikator
- Endpunkt-URLs für Zugriff
- Metadata für Entdeckung
- Health-Status-Überwachung
- Versions-Verlauf

---

## Implementierung in Engines

### Client und Server Funktionalität

**Jede DEMOS Engine** (C++, Python, Julia) wird beinhalten:

#### Client-Seite

- Mit MaaS-Services verbinden
- Anfragen gemäß Protokoll senden
- Antworten empfangen und verarbeiten
- Fehler handhaben und erneut versuchen
- Ergebnisse cachen, wenn angemessen

#### Server-Seite

- Benutzerdefinierte Modelle für MaaS wrappen
- Auf Anfragen hören
- Modell-Berechnungen ausführen
- Formatierte Antworten zurückgeben
- Nutzung und Fehler protokollieren

Diese bidirektionale Unterstützung bedeutet:

- Jede Engine kann **auf** MaaS-Modelle zugreifen
- Jede Engine kann **benutzerdefinierte Modelle als** MaaS-Services wrappen

---

## Leichte C/C++ MaaS-Server-Bibliothek (2027.Q1)

**Leitung**: MPP und TUDO

### Motivation

Legacy-C/C++-Modelle und Fortran-Codes stellen einen großen Teil des bestehenden Forschungs-Codes dar. Eine leichte Bibliothek ermöglicht ihre Integration mit minimaler Änderung.

### Design-Prinzipien

- **Minimale Abhängigkeiten**: Nur Standard-C/C++-Bibliothek
- **Einfaches API**: Wenige Funktionen zu implementieren
- **Klare Dokumentation**: Einfach für Nicht-Experten
- **Beispiel-Templates**: Copy-Paste Anfangspunkte
- **Fortran-Bindings**: Via ISO C Binding

### Beispiel-Nutzung

```cpp
#include "demos_maas.h"

// Benutzer implementiert diese Funktionen
double my_model_density(const double* x, const double* params);
void my_model_sample(double* x, const double* params);

int main() {
    DemosMaaSServer server;
    server.register_density(my_model_density);
    server.register_sampler(my_model_sample);
    server.serve(); // Auf Anfragen hören
}
```

### Features

- Automatische Protocol-Behandlung
- Multi-Threading Unterstützung
- Grundlegende Fehlerbehandlung
- Protokollierungsfähigkeiten
- Konfiguration über JSON

---

## Containerisierungs-Strategie

### Warum Container?

Container bieten:

- **Isolierung**: Keine Konflikte mit Host-Umgebung
- **Reproduzierbarkeit**: Genau definierte Softwareumgebung erhalten
- **Portabilität**: Laufen überall, wo Container unterstützt werden
- **Versionierung**: Unveränderliche Images mit Version-Tags
- **Verteilung**: Standard-Registries (Docker Hub, etc.)

### Container-Technologien

**Primär**: Docker/Podman

- Industrie-Standard
- Exzellentes Tooling
- Großes Ökosystem
- Gute Dokumentation

**Alternative**: Singularity/Apptainer

- Beliebt in HPC-Umgebungen
- Besser für Multi-User Systeme
- Kompatibel mit Docker Images

### Container Best Practices

1. **Minimale Base Images**: Größe und Attack Surface reduzieren
2. **Multi-Stage Builds**: Build- und Runtime-Umgebungen trennen
3. **Version Pinning**: Explizite Abhängigkeitsversionen
4. **Security Scanning**: Schwachstellen identifizieren
5. **Dokumentation**: Klare README und Anweisungen

---

## Anwendungsfälle

### Neutrino-Oszillations-Modelle (TUM Leitung)

**Herausforderung**: Komplexe Detektor-Response, verschiedene Flux-Modelle

**Ansatz**:

- Neutrino-Oszillations-Rechner containerisieren
- Mit MaaS-Protokoll ausstatten
- In Infrastruktur einsetzen
- Nahtlose Integration in Analysen ermöglichen

**Vorteile**:

- Konsistente Umgebung über Institutionen hinweg
- Einfache Updates und Versionierung
- Reduktion lokaler Setup-Burden
- Reproduzierbare Ergebnisse

### Astropartikel-Modelle (RUB-A)

**Herausforderung**: Großflächige Monte-Carlo-Simulationen, 3D-Propagation

**Modelle zu containerisieren**:

- CRPropa Cosmic-Ray Propagation
- Source-Verteilungs-Modelle
- Partikel-Interaktions-Codes

**Größenordnung**: 10^4 bis 10^6 CPU-Stunden pro Simulation

**MaaS Vorteile**:

- Laufen auf angemessener Infrastruktur
- Cache teure Berechnungen
- Teile Ergebnisse über Kollaborationen
- Bewahre exakte Softwareversionen

### Kernphysik-Modelle (RUB-N)

**Herausforderung**: Multi-Gigabyte Datendateien, komplexe Matrix-Element-Generierung

**Modelle zu containerisieren**:

- Three-Nucleon Force Berechnungen
- Matrix-Element Generatoren
- Basis-Transformations-Codes

**MaaS Vorteile**:

- Zentralisierte Datenverwaltung
- Rechner-Ressourcen co-lokalisiert mit Daten
- Konsistente numerische Präzision
- Reduzierte lokale Speicheranforderungen

---

## Domain-spezifische Anpassungen

### MPP Beiträge (Decay Chains)

Die MPP-Gruppe wird MaaS-Anpassungen vorantreiben für:

- Hadron Decay-Chain Modelle
- Komplexe Partial-Wave Formalisierungen
- Kovariante Tensor-Formalisierungsimplementierungen

**Spezifisches Beispiel**: τ⁻ → π⁻π⁻π⁺ντ Decay-Modell (Belle II)

- Nutzt ungewöhnliche kovariante Tensor-Formalisierung
- Limitierte Framework-Unterstützung
- Idealer MaaS-Kandidat (2028.Q1)
- Native Implementierung verzögert
- Containerisierte Version ermöglicht sofortige Nutzung
- Cross-Validierung wenn native Version fertig

### Warm-Dense-Matter Modelle (HZDR)

**Domain-spezifische Schnittstelle** (2028.Q3):

Herausforderung: Umfassende Analysen erfordern viele Structure-Factor Modelle gleichzeitig

Lösung: Automatisierte Modell-Serving Infrastruktur

- Neue Structure-Factor Berechnungen hochladen
- Automatische Containerisierung
- Registry Integration
- Sofortige Verfügbarkeit via MaaS

Anwendungen:

- Inertial Confinement Fusion Studien
- XFEL Experimente bei HiBEF
- Path-Integral Monte Carlo Ergebnisse
- TDDFT Simulations-Outputs

---

## Infrastruktur-Anforderungen

### Hosting-Infrastruktur

Modelle können gehostet werden:

1. **Lokal**: Benutzer-Maschine via Container
2. **Institutionell**: Department/Lab Server
3. **National**: Föderalisierte Rechner-Ressourcen
4. **International**: Kollaborations-weite Services

### Ressourcen-Management

Überlegungen:

- **Load Balancing**: Anfragen verteilen
- **Scaling**: Kapazität hinzufügen wenn nötig
- **Monitoring**: Nutzung und Gesundheit verfolgen
- **Kosten**: Wer zahlt für Rechner/Speicher?

### Governance

Fragen zu adressieren:

- Wer kann MaaS-Modelle registrieren?
- Qualitätssicherungs-Prozess?
- Ressourcen-Zuteilungs-Politiken?
- Langfristige Hosting-Verpflichtungen?

---

## Performance-Überlegungen

### Latenz vs. Ausführungszeit

MaaS führt Kommunikations-Overhead ein:

- **Akzeptabel**: Wenn Ausführungszeit >> Latenz (typischerweise > 100ms)
- **Problematisch**: Für sehr schnelle Modelle (< 10ms Ausführung)
- **Minderung**: Batch-Anfragen, lokales Caching

### Optimierungsstrategien

1. **Binärer I/O**: Effiziente Serialisierung
2. **Kompression**: Für große Daten-Transfers
3. **Caching**: Wiederholte Berechnungen speichern
4. **Batching**: Mehrere Evaluierungen senden
5. **Parallele Ausführung**: Mehrere Worker

### Benchmarking

Performance wird gemessen:

- Round-Trip Latenz
- Durchsatz (Anfragen/Sekunde)
- Skalierbarkeit (vs. Zahl der Worker)
- Vergleich mit nativen Implementierungen

---

## Sicherheit und Datenschutz

### Sicherheitsüberlegungen

Für öffentlich-zuständige MaaS-Services:

- **Authentifizierung**: Wer kann zugreifen?
- **Autorisierung**: Welche Operationen erlaubt?
- **Rate Limiting**: Missbrauch verhindern
- **Input Validierung**: Anfragen bereinigen
- **Audit Logging**: Nutzung verfolgen

### Datenschutz-Überlegungen

Modelle können enthalten:

- Proprietäre Algorithmen
- Unpublizierte Daten
- Wettbewerbsforschung
- Datenschutz-sensitive Informationen

**Lösungen**:

- Private Container-Registries
- Access Control Lists
- Institutionelles Hosting
- Vertraulichkeits-Vereinbarungen

---

## Entwicklungs-Zeitplan

### Phase 1: Protocol-Definition (2026.Q4)

- Übersicht bestehender Standards
- Design MaaS-Protokoll
- Spezifikations-Dokument schreiben
- Referenz-Bibliothek implementieren

### Phase 2: Engine-Integration (2027.Q1)

- MaaS Client zu allen Engines hinzufügen
- MaaS Server zu allen Engines hinzufügen
- C/C++ leichte Bibliothek entwickeln
- Beispiel-Implementierungen erstellen

### Phase 3: Anwendungsfall-Entwicklung (2027-2028)

- **TUM**: Neutrino-Oszillations-Modelle
- **RUB-A**: Cosmic-Ray Propagation
- **RUB-N**: Nuclear Force Modelle
- **MPP**: Decay-Chain Modelle
- **HZDR**: Structure-Factor Interface

### Phase 4: Production Deployment (2028)

- Operative Hosting-Infrastruktur
- Überwachung und Wartung
- Dokumentation abgeschlossen
- Community-Training

---

## Meilensteine

### M4: MaaS Protocol funktioniert (2027.Q2)

- Protocol formal definiert
- UUIDs generiert
- Grundlegender Client/Server funktionsfähig
- Beispiel-Container verfügbar

### M7: Integration abgeschlossen (2028.Q1)

- Alle Engines unterstützen MaaS
- C/C++ leichte Bibliothek fertig
- Erste Production Services bereitgestellt
- Validierung gegen nativen Implementierungen

### M10: Production Services (2028.Q3)

- Mindestens 3 containerisierte Modelle pro Domain
- Robuste Hosting-Infrastruktur
- Usage Monitoring operativ
- Community-Adoption demonstriert

---

## Personalkraft-Zuteilung

**Gesamt**: 0,65 Personenjahre

### Nach Institution

- **MPP**: 0,35 py (Leitung, Protocol, Decay-Modelle)
- **TUM**: 0,1 py (Neutrino-Modelle)
- **RUB-A**: 0,1 py (Astropartikel-Modelle)
- **RUB-N**: 0,1 py (Nuclear-Modelle)

---

## Liefergegenstände-Zusammenfassung

### Technische Liefergegenstände

1. **MaaS Protocol-Spezifikation**
   - Binäre Nachrichtenformate
   - Kommunikationsmuster
   - Fehlerbehandlung
   - Versioning-Strategie

2. **Referenz-Implementierungen**
   - Python Client/Server
   - C++ Client/Server
   - Julia Client/Server
   - Leichte C/C++-Bibliothek

3. **Container-Templates**
   - Dockerfile Beispiele
   - Konfigurations-Templates
   - Deployment-Scripts
   - Health Check Utilities

4. **Dokumentation**
   - Protocol-Spezifikation
   - Benutzer-Handbücher
   - Entwickler-Handbücher
   - Best Practices

5. **Beispiel-Modelle**
   - Neutrino Oszillationen (TUM)
   - Cosmic Ray Propagation (RUB-A)
   - Nuclear Forces (RUB-N)
   - Decay Chains (MPP)
   - Structure Factors (HZDR)

---

## Integration mit anderen Arbeitspaketen

### Abhängigkeiten

- **WP1.1**: Standard muss MaaS-Referenzierung beschreiben
- **WP1.2**: Engines müssen Client/Server implementieren
- **WP2.2**: Registry muss MaaS-Modelle unterstützen

### Beiträge zu

- **WP2.1**: MaaS-Modelle in Galerie
- **WP2.2**: Validierung containerisierter Modelle
- **WP3.1**: Dokumentation und Tutorials
- **WP3.2**: Showcase komplexer Domain-Modelle

---

## Erfolgskriterien

WP1.3 wird erfolgreich sein, wenn:

✅ MaaS Protocol formal definiert und dokumentiert
✅ Alle drei Engines unterstützen MaaS Client und Server
✅ Leichte C/C++-Bibliothek ermöglicht einfaches Wrapping
✅ Mindestens 5 Production MaaS-Services operativ
✅ Performance-Overhead akzeptabel (< 2x vs. native)
✅ Container-Templates für gängige Szenarien verfügbar
✅ Community-Mitglieder deployen ihre eigenen MaaS-Modelle
✅ Cross-Validierung mit nativen Implementierungen erfolgreich

---

## Langfristige Vision

Der MaaS-Ansatz stellt sicher:

### Konservierung

Legacy-Modelle bleiben zugänglich auch wenn:

- Programmiersprachen evolvieren
- Abhängigkeiten veralten
- Betriebssysteme ändern
- Hardware-Architekturen verschieben

### Flexibilität

Forscher können:

- Bestes Tool für jede Komponente nutzen
- Modelle über Sprachen kombinieren
- Spezialisierte Infrastruktur nutzen
- Modelle unabhängig aktualisieren

### Skalierbarkeit

Das System unterstützt:

- Einfache Modelle bis komplexe Simulationen
- Lokale Ausführung bis verteiltes Computing
- Einzelne Benutzer bis große Kollaborationen
- Aktuelle und zukünftige Rechner-Paradigmen

### Nachhaltigkeits

Langfristige Wartung ist machbar:

- Klare Schnittstellengrenzen
- Isolierte Abhängigkeiten
- Unabhängige Versionierung
- Dokumentierte Protokolle

---

## Risiken und Minderung

| Risiko | Impact | Minderung |
|--------|--------|-----------|
| Netzwerk-Latenz zu hoch | Schlechte Benutzererfahrung | Caching, Batching, lokale Container |
| Container-Sicherheitslücken | Mögliche Exploits | Scanning, Updates, Access Controls |
| Hosting-Infrastruktur-Kosten | Unsustainable Operation | Gemeinsame Ressourcen, Institutionelle Unterstützung |
| Protocol-Evolutions-Probleme | Kompatibilität bricht | Sorgfältige Versionierung, Veraltungspolitiken |
| Komplexe Setup-Burden | Niedrige Adoption | Templates, Automation, Dokumentation |

---

## Fazit

WP1.3 - MaaS erweitert die Reichweite von DEMOS über das, was nativ serialisiert werden kann, und stellt sicher, dass:

- **Komplexe Modelle** sind nicht ausgeschlossen
- **Legacy Code** bleibt wertvoll
- **Spezialisierte Infrastruktur** kann genutzt werden
- **Zukünftige Technologien** können berücksichtigt werden

Durch die Kombination von Containerisierung mit einem gut-definierten Protokoll bietet MaaS einen **nachhaltigen, flexiblen und mächtigen** Mechanismus für die Einbeziehung der vollständigen Vielfalt von Forschungs-Modellen in das DEMOS-Ökosystem.

---

## Nächste Schritte

- Überprüfen Sie [WP1.1: Harmonizing →](wp1-1-harmonizing.md) um zu sehen, wie der Standard definiert wird
- Erkunden Sie [WP1.2: Engines →](wp1-2-engines.md) um native Implementierungen zu verstehen
- Zurück zu [Pillar 1 Übersicht →](index.md)
