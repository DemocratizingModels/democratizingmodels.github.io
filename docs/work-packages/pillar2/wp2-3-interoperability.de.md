---
title: WP2.3 - Interoperabilität
---

# WP2.3: Interoperabilität mit bestehender Infrastruktur

**Leit-Institution:** TUDO (TU Dortmund Universität)
**Zeitplan:** 2026.Q2 - 2028.Q1
**Personenjahre:** 0,5

---

## Übersicht

Das DEMOS Portal **wird nicht isoliert operieren**, sondern wird auf bestehenden Ressourcen wie HEPData, Zenodo und anderen Domain-spezifischen Repositories bauen und diese erweitern. Dieses Arbeitspaket stellt nahtlose Integration mit etablierter Infrastruktur sicher, indem es bestehende Plattformen verbessert statt ersetzt.

**Kern-Prinzip:** Die DEMOS Initiative plant nicht, bestehende Infrastruktur in irgendeiner Weise zu schmälern oder zu ersetzen. Vielmehr sollten bestehende Ressourcen erweitert und genutzt werden.

---

## Schlüssel-Ziele

1. **Bestehende Repositories erweitern** mit standardisiertem Modell-Zugriff
2. **Maschinenlesbare Metadaten** Standards etablieren mit DOI und UUID Referenzen
3. **Bidirektionale Integration** zwischen DEMOS und externen Plattformen ermöglichen
4. **Vereinheitlichte APIs** für Black-Box Interaktion mit Modellen bieten
5. **Modell-Entdeckung** über mehrere Repositories erleichtern
6. **Langzeit-Bewahrung** durch Integration mit Archivierungs-Services sicherstellen

---

## Ziel-Plattformen

### 1. HEPData

**Aktueller Status:**
- Hostet Partikelphysik experimentelle Daten
- ATLAS Kollaboration publiziert Likelihoods mit HS3 und pyhf Formaten
- Mehrere publizierte Modelle verfügbar (40+ mit pyhf Format)

**Integrations-Ziele:**

✅ **Standardisierter Zugriff**
- Biete Tools zum Zugriff auf HEPData-gehostete Modelle mit DEMOS Standard
- Konvertiere bestehende HS3/pyhf Modelle zu DEMOS Format
- Ermögliche direkt Download und Nutzung in DEMOS Engines

✅ **Metadata-Verknüpfung**
- Verknüpfe DEMOS Registry Einträge mit HEPData Records via DOI
- Bidirektionale Referenzen zwischen Plattformen
- Synchronisierte Metadata Updates

✅ **Entdeckungs-Verbesserung**
- HEPData Modelle discoverable durch DEMOS Portal
- DEMOS LLM Suche includes HEPData Records
- Vereinheitlichte Such-Schnittstelle über beide Plattformen

**Implementierungs-Zeitplan:**
- **2026.Q2:** Maschinenlesbare Metadata-Feld etabliert
- **2027.Q1:** Vollständige Integration mit Modell-Galerie und Entdeckung

**Unterstützung:**
- Bestätigungsschreiben von HEPData Team (Dr. Graeme Watt, Durham University)
- Zusammenarbeit bei Werkzeug-Entwicklung für HS3 Standard Integration

### 2. Zenodo

**Aktueller Status:**
- Allgemein-zweck Forschungs-Daten Repository
- DOI Zuteilung für Datensätze und Code
- Langzeit-Bewahrung Verpflichtung
- Zunehmend genutzt für Modell und Code Teilen

**Integrations-Ziele:**

✅ **DOI-basierte Referenzen**
- Jedes DEMOS Modell verknüpft mit Zenodo DOI (falls verfügbar)
- Bidirektionale Zitations-Verknüpfung
- Kredit-Zuteilung für Modell-Autoren

✅ **Langzeit-Bewahrung**
- Modelle hochgeladen zu DEMOS und Zenodo
- Zenodo bietet Archivierungs-Garantie
- DEMOS Registry zeigt zu Zenodo Records

✅ **Automatische Synchronisierung**
- DEMOS Submission triggert Zenodo Upload (optional)
- Zenodo Metadata synchronisiert zu DEMOS
- Versions-Verfolgung über beide Plattformen

**Implementierungs-Zeitplan:**
- **2026.Q2:** DOI Verknüpfung etabliert
- **2027.Q1:** Vollständige Integration mit automatischer Synchronisierung

**Unterstützung:**
- Bestätigungsschreiben von Zenodo Team (Lars Holm Nielsen, CERN IT Department)
- Zusammenarbeit bei Verbesserung der HS3 Standard Nutzbarkeit mit Zenodo

### 3. Domain-spezifische Repositories

**Zusätzliche Plattformen:**

- **RODARE** (HZDR): Self-hosted Plattform für Warm Dense Matter und Laser-Physik Modelle
- **GitHub/GitLab:** Code und Modell Repositories von einzelnen Forschungs-Gruppen
- **arXiv:** Preprints mit zusätzlichen Modell-Dateien
- **Kollaborations-Webseiten:** ATLAS, CMS, LHCb, Belle II, BESIII, etc.

**Integrations-Ansatz:**
- Metadata Harvesting wo möglich
- Manuelle Kurierung für bedeutende Modelle
- Links von DEMOS zu Original-Quellen
- Zitations-Verfolgung

---

## Technische Implementierung

### Maschinenlesbare Metadata-Feld (2026.Q2)

**Standard Metadata Schema:**

```json
{
  "demos_id": "uuid-12345",
  "external_references": {
    "hepdata": {
      "record_id": "ins2765432",
      "doi": "10.17182/hepdata.12345",
      "url": "https://hepdata.net/record/ins2765432"
    },
    "zenodo": {
      "record_id": "7654321",
      "doi": "10.5281/zenodo.7654321",
      "url": "https://zenodo.org/record/7654321"
    },
    "github": {
      "repo": "owner/repository",
      "commit": "abc123def456",
      "url": "https://github.com/owner/repository/tree/abc123"
    }
  },
  "publication": {
    "doi": "10.1103/PhysRevD.109.112006",
    "arxiv": "2401.12345",
    "inspire_id": "2750000"
  },
  "container": {
    "uuid": "container-uuid-67890",
    "registry": "docker.io",
    "image": "demos/model-12345:v1.0"
  }
}
```

**Schlüssel-Features:**

- **DOI Referenzen** für Publikationen und Datensätze
- **UUID Referenzen** für containerisierte Modelle (MaaS)
- **Repository Links** für Code und zusätzliche Materialien
- **Versions-Verfolgung** über Plattformen hinweg
- **Maschinenlesbar** für automatisierte Tools
- **Menschenlesbar** für Dokumentation

### Vereinheitlichte API Architektur

**Ziel:** Black-Box Interaktion mit MaaS Container Infrastruktur unabhängig von Hosting-Lokation.

**API Endpunkte:**

```
# DEMOS Registry
GET /api/models/{id}
GET /api/models/{id}/file
GET /api/models/{id}/execute

# HEPData Integration
GET /api/hepdata/{record_id}
GET /api/hepdata/{record_id}/convert

# Zenodo Integration
GET /api/zenodo/{record_id}
GET /api/zenodo/{record_id}/download

# Container Ausführung
POST /api/models/{id}/run
  {
    "inputs": {...},
    "parameters": {...}
  }
```

**Fähigkeiten:**

- **Entdecke Modelle** über mehrere Repositories
- **Download Modelle** von jeder Plattform
- **Führe Modelle aus** via MaaS Protocol
- **Kombiniere Modelle** aus verschiedenen Quellen
- **Verfolge Provenance** durch Metadata

### Konvertierungs-Tools

**Format-Konvertierung:**

```python
# HS3 → DEMOS
convert_hs3_to_demos(hs3_file) → demos_file

# pyhf → DEMOS
convert_pyhf_to_demos(pyhf_json) → demos_file

# DEMOS → HS3 (wo anwendbar)
convert_demos_to_hs3(demos_file) → hs3_file
```

**Anwendungsfälle:**

1. **Importiere bestehende Modelle** von HEPData zu DEMOS Registry
2. **Exportiere DEMOS Modelle** zu Legacy-Formaten für Kompatibilität
3. **Cross-validiere** Modelle zwischen Formaten
4. **Demonstriere Äquivalenz** verschiedener Darstellungen

---

## Zusammenarbeits-Strategie

### HEPData Team

**Aktivitäten:**

- Regelmäßige Treffen zur Integrations-Koordination
- Gemeinsame Entwicklung von Konvertierungs-Tools
- Tests mit bestehenden ATLAS/CMS Likelihoods
- Dokumentation von Best Practices
- Feedback zur DEMOS Standard Verbesserung

**Vorteile für HEPData:**

- Verbesserte Entdeckbarkeit via LLM Suche
- Standardisiertes Modell-Format reduziert Fragmentierung
- Interaktive Exploration durch Binder Integration
- Breitere Community Engagement

### Zenodo Team

**Aktivitäten:**

- Definiere DOI Zuteilungs-Workflow
- Implementiere Metadata Synchronisierung
- Teste automatische Upload Funktionalität
- Sicherstelle Langzeit-Bewahrung Compliance
- Community Outreach für Adoption

**Vorteile für Zenodo:**

- Strukturierte Modelle mit reichen Metadaten
- Erhöhte Nutzung für wissenschaftliche Modelle
- Integration mit Domain-spezifischem Portal
- Zitations-Verfolgung und Impact Metriken

### Domain Communities

**Engagement:**

- Präsentiere DEMOS bei Kollaborations-Treffen
- Biete Training zu Modell-Submission an
- Biete Unterstützung für Modell-Konvertierung
- Sammle Feedback zu Anforderungen
- Zeige erfolgreiche Beispiele

---

## Implementierungs-Phasen

### Phase 1: Grundlage (2026.Q2 - 2026.Q4)

**Liefergegenstände:**

- [ ] Maschinenlesbare Metadata Schema finalisiert
- [ ] DOI Verknüpfung in DEMOS Registry implementiert
- [ ] Grundlegender HEPData Record Lookup funktionsfähig
- [ ] Zenodo API Integration Prototype

### Phase 2: Integration (2027.Q1 - 2027.Q2)

**Liefergegenstände:**

- [ ] HEPData Modelle in Galerie integriert
- [ ] DEMOS Entdeckungs-Tool sucht HEPData
- [ ] Zenodo automatischer Upload funktioniert
- [ ] Konvertierungs-Tools für HS3/pyhf operational

### Phase 3: Verbesserung (2027.Q3 - 2028.Q1)

**Liefergegenstände:**

- [ ] Vereinheitlichte API für Cross-Repository Zugriff
- [ ] MaaS Protocol unterstützt externe Container
- [ ] Bidirektionale Synchronisierung abgeschlossen
- [ ] Dokumentation und Training-Material

---

## Koordinations-Rolle (TUDO)

TUDO koordiniert Interoperabilitäts-Bemühungen durch:

**1. Interface Design**
- Definiere gemeinsame API Spezifikationen
- Etabliere Metadaten-Standards
- Erstelle Konvertierungs-Tool Anforderungen

**2. Community Engagement**
- Liaison mit HEPData und Zenodo Teams
- Koordiniere mit Domain-spezifischen Repositories
- Erleichtere Zusammenarbeit über Institutionen hinweg

**3. Implementierungs-Unterstützung**
- Biete technische Anleitung zu Partnern
- Überprüfe und teste Integrations-Code
- Stelle Konsistenz über Plattformen sicher

**4. Dokumentation**
- Schreibe Integrations-Handbücher
- Erstelle Nutzungs-Beispiele
- Verlege Kompatibilitäts-Matrix

**5. Qualitätssicherung**
- Teste Cross-Repository Workflows
- Verifiziere Metadata Konsistenz
- Überwache Integrations-Gesundheit

---

## ATLAS Kollaborations-Beispiel

**Kontext:**

- ATLAS publiziert Likelihoods auf HEPData mit HS3 Format
- Mehrere Analysen nutzen ausgefeilte statistische Modelle
- Modelle verwendet für Higgs Entdeckung, Top Quark Messungen, BSM Suchen

**DEMOS Integration:**

1. **Entdeckung Higgs Modelle (2026.Q3)**
   - Importiere 2012 Higgs Entdeckungs-Modelle von HEPData
   - Konvertiere zu DEMOS Standard
   - Feature in Modell-Galerie als historisches Showcase
   - Ermögliche interaktive Exploration

2. **Neuere Analysen**
   - ttZ Produktions-Messungen
   - Charge-Asymmetrie Studien
   - Same-Charge Top-Quark Paar-Suchen
   - Importiere und standardisiere alle publizierten HS3 Modelle

3. **Zukünftige Submissions**
   - Ermutere ATLAS, direkt im DEMOS Format zu publizieren
   - Biete automatische HEPData Submission aus DEMOS
   - Sicherstelle Rückwärts-Kompatibilität mit bestehenden Tools

**Vorteile für ATLAS:**

- Einfacheres Modell-Sharing innerhalb Kollaboration
- Bessere Sichtbarkeit publizierter Ergebnisse
- Interaktive Exploration für Bildung
- Langzeit-Bewahrung und Zugänglichkeit

---

## Zeitplan & Meilensteine

| Datum | Meilenstein | Beschreibung |
|------|-----------|-------------|
| **2026.Q2** | Metadata Standard | Maschinenlesbare Metadata-Feld etabliert |
| **2027.Q1** | Galerie Integration | HEPData Modelle in DEMOS Galerie |
| **2027.Q1** | Entdeckungs Integration | DEMOS Suche includes externe Repositories |
| **2028.Q1** | Vollständige API | Vereinheitlichte APIs für Cross-Repository Zugriff |

---

## Liefergegenstände

### Software

- [ ] Metadata Schema Spezifikation
- [ ] HEPData Integration API
- [ ] Zenodo Integration API
- [ ] Konvertierungs-Tools (HS3, pyhf)
- [ ] Cross-Repository Such-Indexer

### Dokumentation

- [ ] Integrations-Architektur Handbuch
- [ ] API Nutzungs-Dokumentation
- [ ] Modell-Submission Workflow (Multi-Repository)
- [ ] Konvertierungs-Tool Dokumentation
- [ ] Best Practices Handbuch

### Partnerschaften

- [ ] Formale Vereinbarungen mit HEPData und Zenodo
- [ ] Regelmäßige Koordinations-Treffen
- [ ] Gemeinsame Entwicklungs-Sprints
- [ ] Gemeinsame Roadmap

---

## Erfolgs-Metriken

✅ 10+ Modelle von HEPData zu DEMOS importiert
✅ Alle DEMOS Modelle haben DOI Referenzen (wo anwendbar)
✅ Zenodo automatischer Upload funktionsfähig
✅ DEMOS Suche gibt HEPData Ergebnisse zurück
✅ Konvertierungs-Tools validiert auf 20+ Modellen
✅ API Response-Zeit <1 Sekunde für externe Abfragen
✅ Zero Metadata Inkonsistenzen zwischen Plattformen

---

## Bestätigungsschreiben

### HEPData (Dr. Graeme Watt, Durham University)

> "Im Namen des HEPData Teams sind wir erfreut, das 'DEMOS – Democratizing MOdelS' Proposal zum ErUM Data Call der BMBF zu unterstützen. Wir glauben, die vorgeschlagene Integration des HS3 Standards in HEPData stimmt stark mit unserem gemeinsamen Ziel überein, die Zugänglichkeit und Nutzbarkeit öffentlicher Likelihoods für die Hochenergiephysik-Community zu verbessern."

> "Falls dieses Proposal erfolgreich finanziert wird, freuen wir uns auf die Zusammenarbeit mit dem DEMOS Team zur Entwicklung von Tools, die die Integration und Nutzbarkeit des HS3 Standards innerhalb HEPData erweitern."

### Zenodo (Lars Holm Nielsen, CERN IT Department)

> "Im Namen des Zenodo Teams sind wir erfreut, das 'DEMOS - DEmocratizing MOdelS' Proposal zum ErUM Data Call der BMBF zu unterstützen. Wir glauben, die vorgeschlagene Integration des HS3 Standards mit Zenodo stimmt stark mit unserem gemeinsamen Ziel überein, die Zugänglichkeit und Nutzbarkeit öffentlicher Likelihoods in der Open Science Community zu verbessern."

> "Falls dieses Proposal erfolgreich finanziert wird, freuen wir uns auf die Zusammenarbeit mit dem DEMOS Team zur Entwicklung von Tools, die die Integration und Nutzbarkeit des HS3 Standards mit Zenodo erweitern."

---

## Risiko-Minderung

| Risiko | Impact | Minderung |
|--------|--------|-----------|
| API Änderungen bei externen Plattformen | Mittel | Version Pinning, Veraltungs-Überwachung, Fallback-Methoden |
| Metadata Schema Divergenz | Hoch | Regelmäßige Koordinations-Treffen, gemeinsame Spezifikation |
| Rechtliche/Lizenz-Konflikte | Mittel | Klare Zuschreibung, offene Lizenzen, Rechtliche Überprüfung |
| Plattform Verfügbarkeitsprobleme | Niedrig | Caching, lokale Kopien, graceful Degradation |
| Community Widerstand | Mittel | Frühes Engagement, Vorteile demonstrieren, graduales Adoption |

---

## Verbindung zu Projekt-Zielen

Dieses Arbeitspaket unterstützt direkt die DEMOS Mission durch:

1. **Bestehende Infrastruktur nutzen** - Baue auf etablierten Plattformen
2. **Langlebigkeit sicherstellen** - Integration mit Archivierungs-Services (Zenodo)
3. **Reichweite maximieren** - Modelle discoverable über mehrere Portale
4. **Community-Praktiken respektieren** - Arbeit mit bestehenden Workflows
5. **Impact verbessern** - Breitere Sichtbarkeit und Zitations-Verfolgung

---

## Nächste Schritte

Nach Exploration von WP2.3:

- [Zurück zu Pillar 2 Übersicht →](index.md)
- [WP2.1: Front-end Portal ←](wp2-1-frontend.md)
- [WP2.2: Back-end Registry & CI/CD ←](wp2-2-backend.md)
- [Erkunde Pillar 3: Community Engagement →](../pillar3/index.md)
