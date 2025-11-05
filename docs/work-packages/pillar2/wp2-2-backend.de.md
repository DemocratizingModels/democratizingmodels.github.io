---
title: WP2.2 - Back-end Registry & CI/CD
---

# WP2.2: Back-end: Modell-Registry und Continuous Integration

**Leit-Institution:** HZDR (Helmholtz-Zentrum Dresden-Rossendorf)
**Zeitplan:** 2026.Q4 - 2028.Q1
**Personenjahre:** 0,7

---

## Übersicht

Das Back-end der Plattform fungiert als **Verbindungspunkt zwischen Front-end und der Datenbank** mit den Modell-Dateien. Es ist das zentrale Rückgrat, das Aktionen auf neu eingefügte Modelle durchführt und Zugriffs-Punkte zum Abrufen von Modellen aus der Datenbank bietet.

Die Back-end Infrastruktur stellt sicher:

- **Qualitätskontrolle** durch automatisierte Validierung
- **Reproduzierbarkeit** durch Versionierung und Checksums
- **Zugänglichkeit** durch gut definierte APIs
- **Nachhaltigkeit** durch CI/CD Automation
- **Skalierbarkeit** durch Enterprise-Level Technologien

---

## Kern-Komponenten

### 1. Modell-Registry (2026.Q4)

Ein Repository für dedizierte Metadaten jedes Modells, verbindend die Modell-ID mit der aktuellen Modell-Datei.

**Zweck:**
- Zentrale Verwaltung eingefügter Modelle
- Metadata Speicherung und Indexierung
- Versions-Verfolgung
- DOI und UUID Mapping
- Such-Index Generierung

**Daten-Struktur:**

```json
{
  "model_id": "uuid-string",
  "name": "B+ → K+ νν̄ BELLE II 2024",
  "doi": "10.1103/PhysRevD.109.112006",
  "version": "1.0.0",
  "domain": "particle_physics",
  "collaboration": "Belle II",
  "file_location": "s3://demos/models/belle2_bknn.json",
  "checksum": "sha256:abc123...",
  "reference_points": "tests/belle2_bknn_refs.json",
  "metadata": {
    "tags": ["B-meson", "rare-decay", "neutrino"],
    "search_keywords": ["..."],
    "citations": ["..."]
  },
  "validation_status": "approved",
  "submission_date": "2024-11-05",
  "last_updated": "2024-11-05"
}
```

**Technologie:**
- **GitHub** als Hosting-Plattform (Versions-Kontrolle, Issues, Pull Requests)
- Alternative: **Invenio** Framework (wird evaluiert)
- JSON-basierte Registry Dateien
- Git-Verlauf für Versionierung

### 2. Drei-Schritt Modell-Einbezugs-Prozess

#### Schritt 1: Validierung (2028.Q1)

**Automatisierte Prüfungen:**

1. **Integritäts-Validierung**
   - Checksum Verifikation (SHA-256)
   - JSON Schema Validierung
   - Datei-Format Compliance
   - Abhängigkeits-Prüfung

2. **Korrektheit-Validierung**
   - Referenzpunkt-Tests
   - Erwartete Output Verifikation
   - Numerische Stabilitäts-Prüfungen
   - Cross-Engine Konsistenz (optional)

**Manuelle Überprüfung:**

1. **Relevanz-Bewertung**
   - Wissenschaftliche Signifikanz
   - Angemessen für DEMOS Bereich
   - Richtige Dokumentation
   - Zitations-Vollständigkeit

2. **Sicherheits-Überprüfung**
   - Kein bösartiger Code
   - Keine sensiblen Daten
   - Keine Urheberrechtsverletzungen
   - Lizenz-Compliance

#### Schritt 2: Pre-processing

**Metadata-Bereicherung:**

- Extrahiere Metadata aus Modell-Datei (wenn verfügbar)
- Füge Speicher-spezifische Informationen hinzu
- Generiere Such-Indizes und Keywords
- Verknüpfe DOI Referenzen
- Weise UUID zu falls nicht vorhanden

**Automatisierte Aufgaben:**

- Generiere Modell-Visualisierungen
- Erstelle Thumbnail-Bilder
- Extrahiere Parameter-Listen
- Berechne Modell-Statistiken
- Baue Dokumentations-Links

#### Schritt 3: Einfügung

**Registry-Update:**

- Füge Modell-Eintrag zu Registry hinzu
- Aktualisiere Such-Indizes
- Verknüpfe mit bestehenden Ressourcen (HEPData, Zenodo)
- Triggere Front-end Deployment

**Speicherung:**

- Kopiere Modell-Datei in Datenbank (oder)
- Erstelle Referenz zu externem Speicher
- Aktualisiere CDN/Cache falls anwendbar

### 3. Application Programming Interface (API) (2028.Q1)

RESTful API für Services, um mit Modell-Registry zu kommunizieren und mit Modell-Dateien zu interagieren.

**Endpunkte:**

```
GET    /api/models              # Liste alle Modelle
GET    /api/models/{id}         # Hole spezifisches Modell
POST   /api/models              # Submittiere neues Modell (authentifiziert)
PUT    /api/models/{id}         # Aktualisiere Modell-Metadata
DELETE /api/models/{id}         # Entferne Modell (nur Admin)

GET    /api/models/search?q={query}  # Suche Modelle
GET    /api/models/filter?domain=particle_physics&tag=rare-decay

GET    /api/models/{id}/file    # Download Modell-Datei
GET    /api/models/{id}/metadata  # Hole nur Metadata
GET    /api/models/{id}/validate  # Triggere Validierung
GET    /api/models/{id}/visualize # Hole Visualisierung
```

**Authentifizierung:**
- API Keys für authentifizierte Operationen
- OAuth Integration für Benutzer-Konten
- Rate Limiting für öffentlichen Zugriff
- Admin Privilegien für Moderation

**Dokumentation:**
- OpenAPI/Swagger Spezifikation
- Interaktiver API Explorer
- Code Beispiele in mehreren Sprachen
- Client Bibliotheken (Python, Julia, C++)

---

## CI/CD Infrastruktur

### GitHub Actions basierte Pipeline (2028.Q1)

**Trigger:**

- Pull Request geöffnet/aktualisiert
- Merge zu Hauptzweig
- Manueller Workflow Dispatch
- Geplante Validierungs-Durchläufe

**Workflow Schritte:**

```yaml
name: Model Validation Pipeline

on:
  pull_request:
    paths:
      - 'models/**'

jobs:
  validate:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v3

      - name: Validate JSON schema
        run: python scripts/validate_schema.py

      - name: Check integrity
        run: python scripts/check_checksums.py

      - name: Run reference tests
        run: python scripts/test_references.py

      - name: Generate visualizations
        run: python scripts/generate_viz.py

      - name: Report results
        run: python scripts/report_to_frontend.py
```

**Validierungs-Tools:**

- **Schema Validator:** Stellt sicher JSON konform DEMOS Standard
- **Checksum Verifier:** Validiert Datei-Integrität
- **Reference Tester:** Läuft Modell mit bekannten Eingaben, prüft Outputs
- **Visualization Generator:** Erstellt Plots und Diagramme
- **Coverage Reporter:** Verfolgt welche Modelle validiert wurden

**Status-Berichterstattung:**

- CI/CD Ergebnisse an Pull Request gepostet
- Status Badges generiert
- Validierungs-Berichte gespeichert
- Front-end benachrichtigt von Ergebnissen

### Continuous Deployment

**Automatisiertes Deployment:**

- Genehmigte Modelle → Registry Update
- Registry Update → Datenbank Sync
- Datenbank Sync → Cache Invalidation
- Cache Invalidation → Front-end Refresh

**Rollback Fähigkeit:**

- Git-Verlauf ermöglicht Versions-Rollback
- Fehlgeschlagene Deployments Auto-Revert
- Manuelle Override für Notfälle

---

## Technischer Stack

### Backend Technologien

```
┌──────────────────────────────────────────┐
│         GitHub/GitLab                    │
│  • Modell-Registry (JSON Dateien)       │
│  • Pull Request Workflows               │
│  • GitHub Actions (CI/CD)               │
└──────────────────────────────────────────┘
              ↓
┌──────────────────────────────────────────┐
│      Validierungs-Services               │
│  • Schema Validators                     │
│  • Referenzpunkt-Test Läufer            │
│  • Checksum Verifizierer                │
│  • Visualisierungs-Generatoren          │
└──────────────────────────────────────────┘
              ↓
┌──────────────────────────────────────────┐
│         Datenbank/Speicher               │
│  • Modell-Dateien (JSON)                 │
│  • Metadata (indiziert)                  │
│  • Visualisierungen (generiert)          │
│  • Test-Ergebnisse (gecacht)             │
└──────────────────────────────────────────┘
              ↓
┌──────────────────────────────────────────┐
│           API Layer                      │
│  • REST Endpunkte                        │
│  • Authentifizierung                     │
│  • Rate Limiting                         │
│  • CDN Integration                       │
└──────────────────────────────────────────┘
```

### Programmiersprachen

- **Python:** Validierungs-Skripte, API Server, Automation
- **Bash/Shell:** GitHub Actions Workflows
- **YAML:** Konfigurationsdalteien
- **JSON:** Registry und Modell-Dateien

---

## HZDR Erfahrung

### Bestehende Infrastruktur

**QEDjl-Projekt:**
- Small-Scale Version von CI/CD System bereits operativ bei HZDR
- Automatisierte Test- und Validierungs-Pipelines
- Continuous Deployment Workflows
- Bietet Grundlage für DEMOS Backend

**Expertise:**
- Enterprise-Level Softwareentwicklung
- Hochleistungs-Rechner-Infrastruktur
- Daten-Verwaltung und Archivierung
- Automatisierte Test Frameworks

---

## Modell-Speicher-Optionen

### Option 1: GitHub-basierter Speicher

**Vorteile:**
- Integriert mit Registry
- Eingebaute Versionskontrolle
- Kostenlos für öffentliche Repositories
- Vertraut für Entwickler

**Nachteile:**
- Dateigrößen-Limits (100 MB pro Datei)
- Große Binär-Dateien problematisch
- Bandwidth Limitierungen

**Best für:** Text-basierte JSON Modelle, kleine Datensätze

### Option 2: Dedizierte Datenbank

**Vorteile:**
- Keine Dateigrößen-Limits
- Optimiert für Abfragen
- Bessere Skalierbarkeit
- CDN Integration

**Nachteile:**
- Zusätzliche Infrastruktur-Kosten
- Komplexeres Setup
- Wartungs-Overhead

**Best für:** Große Modelle, High-Traffic Szenarien

### Option 3: Hybrid-Ansatz

**Registry auf GitHub + Dateien in Object Storage**

- Registry Metadata in GitHub
- Große Modell-Dateien in S3/MinIO
- Best of Both Worlds
- Links in Registry zeigen auf Speicher

**Empfohlener Ansatz**

---

## Validierungs-Tool Entwicklung (2028.Q1)

### Validierungs-Skript Suite

**1. Schema Validator**
```python
def validate_schema(model_file):
    """Validiere Modell gegen DEMOS JSON Schema"""
    schema = load_demos_schema()
    model = load_json(model_file)
    validate(model, schema)  # Wirft Error falls ungültig
```

**2. Integritäts-Checker**
```python
def verify_integrity(model_file, expected_checksum):
    """Verifiziere Datei wurde nicht beschädigt"""
    actual = compute_sha256(model_file)
    assert actual == expected_checksum
```

**3. Referenzpunkt-Tester**
```python
def test_references(model_file, reference_file):
    """Läufe Modell mit bekannten Eingaben, prüfe Outputs"""
    model = load_model(model_file)
    refs = load_references(reference_file)

    for ref in refs:
        result = model.evaluate(ref.inputs)
        assert_close(result, ref.expected, rtol=1e-5)
```

**4. Visualisierungs-Generator**
```python
def generate_visualizations(model_file):
    """Erstelle Plots für Modell-Galerie"""
    model = load_model(model_file)

    # Struktur-Diagramm
    generate_structure_plot(model)

    # Parameter-Verteilungen
    generate_parameter_plot(model)

    # Output Vorhersagen (falls anwendbar)
    generate_output_plot(model)
```

### Test-Abdeckungs-Verfolgung

**Ziel:** 70%+ Test-Abdeckung für Engine-Implementierungen

**Metriken:**
- Prozentsatz getesteter Bausteine
- Prozentsatz validierter Modelle
- Referenzpunkt-Abdeckung
- Cross-Engine Konsistenz-Rate

**Berichterstattung:**
- Abdeckungs-Badges in Repository
- Trend-Analyse über Zeit
- Pro-Domain Abdeckungs-Aufschlüsselung

---

## Zeitplan & Meilensteine

| Datum | Meilenstein | Beschreibung |
|------|-----------|-------------|
| **2026.Q4** | Registry etabliert | Modell-Registry operativ auf GitHub |
| **2027.Q4** | CI/CD Grund | Automatisierte Validierungs-Pipelines funktional |
| **2028.Q1** | Validierung abgeschlossen | Komplette Validierungs-Tool Suite operativ |
| **2028.Q1** | API bereitgestellt | REST API öffentlich zugänglich |
| **2028.Q1** | 70% Abdeckung | Engine Tests decken 70%+ ab |

---

## Liefergegenstände

### Software

- [ ] Modell-Registry Infrastruktur (GitHub-basiert)
- [ ] CI/CD Pipeline Konfigurationen (GitHub Actions)
- [ ] Validierungs-Tool Suite (Python)
- [ ] REST API Server (Python/FastAPI)
- [ ] API Client Bibliotheken (Python, Julia, C++)

### Dokumentation

- [ ] Backend Architektur-Dokumentation
- [ ] API Referenz (OpenAPI)
- [ ] Validierungs-Kriterien Handbuch
- [ ] CI/CD Workflow-Dokumentation
- [ ] Modell-Submission Richtlinien

### Infrastruktur

- [ ] GitHub Organisation und Repositories
- [ ] Automatisierte Test-Umgebung
- [ ] API Hosting (Cloud Deployment)
- [ ] Monitoring und Logging
- [ ] Backup und Disaster Recovery

---

## Erfolgs-Metriken

✅ Modell-Registry enthält 3+ Modelle pro ErUM Domain (18+ gesamt)
✅ CI/CD validiert 90%+ der Submissions ohne manuelle Eingriffe
✅ API Uptime >99%
✅ API Response-Zeit <500ms (p95)
✅ Validierungs-Suite deckt 70%+ Engine Funktionalität ab
✅ Null kritische Sicherheits-Anfälligkeit
✅ Umfassende Dokumentation (>90% Abdeckung)

---

## Zusammenarbeits-Punkte

### Intern (DEMOS Projekt)

- **WP2.1 (RUB-H):** API Spezifikation für Front-end Integration
- **WP2.3 (TUDO):** Metadaten-Standards, DOI Behandlung
- **WP1.2:** Engine Validierungs-Schnittstellen
- **WP3.2:** Modell-Submission aus Showcases

### Extern

- **GitHub:** Plattform-Provider, Actions Infrastruktur
- **QEDjl-Projekt:** Bestehende CI/CD Patterns bei HZDR
- **HEPData/Zenodo:** Metadaten-Austausch-Standards

---

## Risiko-Minderung

| Risiko | Impact | Minderung |
|--------|--------|-----------|
| GitHub Limitierungen | Mittel | Evaluiere Invenio Alternative, Hybrid Storage |
| CI/CD Ressourcen-Kosten | Mittel | Optimiere Workflows, Cache Ergebnisse, Priorisiere Tests |
| API Skalierungs-Probleme | Hoch | Load Balancing, CDN, Rate Limiting |
| Validierungs False Negatives | Hoch | Mehrere Validierungs-Methoden, Manuelle Review |
| Sicherheits-Anfälligkeit | Kritisch | Regelmäßige Audits, Automatisiertes Scanning, Responsible Disclosure |

---

## Evaluation: GitHub vs Invenio

### GitHub (Aktuelle Wahl)

**Vorteile:**
- Vertraut für Entwickler
- Kostenlos für Open Source
- Eingebaute CI/CD (Actions)
- Exzellente Versionskontrolle
- Community Features (Issues, PRs)

**Nachteile:**
- Dateigrößen-Limits
- Weniger flexibel für komplexe Metadata
- Limitierte Abfrage-Fähigkeiten

### Invenio (Alternative)

**Vorteile:**
- Purpose-built für Forschungs-Daten
- Flexible Metadata-Behandlung
- Fortgeschrittene Such-Fähigkeiten
- DOI Integration eingebaut
- Von Zenodo genutzt

**Nachteile:**
- Komplexeres Setup
- Hosting-Kosten
- Wartungs-Overhead
- Learning Curve

**Entscheidung:** Starte mit GitHub, evaluiere Invenio falls Limitierungen auftreten

---

## Verbindung zu Projekt-Zielen

Dieses Arbeitspaket unterstützt direkt die DEMOS Mission durch:

1. **Sicherung Qualität** - Automatisierte Validierung behält Standard-Compliance
2. **Vertrauen ermöglichen** - Checksums und Referenzpunkt-Tests sichern Reproduzierbarkeit
3. **Zugriff erleichtern** - RESTful API ermöglicht programmatisches Modell-Abrufen
4. **Nachhaltigkeit unterstützen** - CI/CD Automation reduziert Wartungs-Burden
5. **Transparenz fördern** - Offenes Registry und Validierungs-Ergebnisse

---

## Nächste Schritte

Nach Exploration von WP2.2, weiter zu:

- [WP2.3: Interoperabilität →](wp2-3-interoperability.md)
- [Zurück zu Pillar 2 Übersicht →](index.md)
- [WP2.1: Front-end Portal ←](wp2-1-frontend.md)
