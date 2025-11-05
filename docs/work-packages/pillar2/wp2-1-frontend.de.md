---
title: WP2.1 - Front-end Portal
---

# WP2.1: Front-end Portal, Modell-Galerie und Sprach-Schnittstelle

**Leit-Institution:** RUB-H (Ruhr-Universität Bochum - Hadron Physik)
**Zeitplan:** 2026.Q2 - 2028.Q2
**Personenjahre:** 1,0

---

## Übersicht

Das Front-end des vorgeschlagenen Portals spielt eine zentrale Rolle bei der **Demokratisierung des Zugriffs** auf Forschungsmodelle im ErUM Domain, indem es eine intuitive und zugängliche Schnittstelle für die Exploration, Entdeckung und Dokumentation von Physik-Modellen bereitstellt. Diese Schnittstelle wird sich nahtlos mit Back-end Systemen integrieren, zeigt sowohl individuelle Modelle als auch kuratierte Beispiele und bietet fortgeschrittene LLM-powered Such-Fähigkeiten.

---

## Schlüssel-Features

### 1. Modell-Portal (2026.Q2)

Eine responsive, benutzerfreundliche Web-Anwendung, die kritische Ressourcen zusammenfasst:

- **Umfassende Modell-Ansicht**
  - Erweiterte Metadata-Anzeige
  - Modell-Struktur Visualisierung
  - Dokumentation und Referenzen
  - DOI Links für Zitationen
  - Verwandte Modelle und Bausteine

- **Technische Implementierung**
  - Gebaut mit **React.js** Framework für Modularität und Skalierbarkeit
  - REST API Integration mit Back-end Systemen
  - Echtzeit-Abruf von Modell-Metadaten
  - Dynamische Visualisierungs-Updates
  - Mobile-responsive Design

- **Benutzer-Erlebnis**
  - Zugängliche Schnittstelle für diverse Hintergründe
  - Klare Navigation und Such-Funktionalität
  - Filterung nach Domain, Komplexität, Tags
  - Modell-Vergleichs-Fähigkeiten

### 2. Modell-Galerie (2026.Q3)

Eine kuratierte Präsentation exemplarischer Modelle mit reichen Visualisierungen:

- **Visuelle Präsentationen**
  - Performance-Metriken Visualisierung
  - Berechnete Outputs und Vorhersagen
  - Modell-Struktur Diagramme
  - Parameter-Sensitivitäts-Plots
  - Uncertainty Quantification Displays

- **Dynamische Inhalte**
  - Von Back-end generierte Visualisierungen
  - Interaktive Plots und Abbildungen
  - Ausführungs-Statistiken
  - Validierungs-Ergebnisse

- **Kurierung**
  - Vorgestellte Modelle aus jeder Domain
  - Hochimpakt-Forschungs-Beispiele
  - Pädagogische Demonstrationen
  - Komplexe Modell-Präsentationen

### 3. JavaScript Visualisierungs-Engine (2026.Q2)

Ein interaktives Tool zur Exploration der Modell-Struktur:

- **Fähigkeiten**
  - Parse DEMOS JSON Format
  - Zeige verschachtelte Modell-Syntax graphisch
  - Zeige Dataflow-Graph Struktur
  - Markiere Bausteine und Verbindungen
  - Exportiere Visualisierungen

- **Interaktive Features**
  - Zoom und Pan Funktionalität
  - Node Expansion/Collapse
  - Hover Tooltips mit Details
  - Parameter-Inspektion
  - Abhängigkeits-Verfolgung

### 4. LLM-powered Discovery Tool (2028.Q2)

Natürliche Sprach-Such-Funktionalität powered durch Large Language Models:

- **Technologie**
  - **Retrieval Augmented Generation (RAG)** Mechanismus
  - AI Agents für Metadata-Analyse
  - Automatische Tag-Generierung
  - Zusammenfassungs-Erstellung
  - Ähnlichkeits-Matching

- **Benutzer-Fähigkeiten**
  - Natürliche Sprach-Abfragen (z.B. "Finde Modelle für B Meson Zerfälle mit Charm Quarks")
  - Semantische Suche über Keywords hinaus
  - Kontext-bewusste Empfehlungen
  - Cross-Domain Entdeckung

- **Infrastruktur**
  - Zusammenarbeit mit **GWDG/KISSKI Konsortium**
  - Zugriff auf **Llama 3.1 70B** Modell
  - API-Kosten Budget-Zuteilung für Entwicklung
  - Erfahrung aus RUB GPT@RUB Projekt (tausende von Benutzern bedient)

### 5. Interaktive Ausführung - Binder Integration (2027.Q3)

Ermögliche Benutzern, Modelle in Live-Rechner-Umgebungen auszuführen:

- **mybinder.org Integration**
  - "Run in Binder" Button für jedes Modell
  - Automatische Notebook-Generierung
  - Leichte Rechner-Unterstützung

- **FAIRUM Zusammenarbeit**
  - Verbindung zu nationalen föderalisierten Ressourcen (Zusammenarbeit mit ErUM-Data FAIRUM Projekt)
  - Großflächige Rechner-Unterstützung
  - Stark reduzierte Latenz
  - Erweiterte Rechner-Kapazität
  - Gemeinsame Entwicklung zwischen RUB-H und TUM Teams

- **Benutzer-Erlebnis**
  - One-Click Ausführungs-Umgebung
  - Vorkonfigurierte Abhängigkeiten
  - Beispiel Notebooks
  - Interaktive Parameter-Exploration
  - Resultat Visualisierung

---

## Technische Architektur

### Front-end Stack

```
┌─────────────────────────────────────────┐
│          React.js Anwendung             │
├─────────────────────────────────────────┤
│  Komponenten:                           │
│  • Such-Schnittstelle (Stichwort + LLM) │
│  • Modell-Galerie                       │
│  • Modell Detail-Seiten                 │
│  • JavaScript Visualisierungs-Engine    │
│  • Binder Integration                   │
└─────────────────────────────────────────┘
              │
              ↓ REST API
┌─────────────────────────────────────────┐
│         Back-end Services               │
├─────────────────────────────────────────┤
│  • Modell-Registry                      │
│  • Metadata-Datenbank                   │
│  • Visualisierungs-Generator            │
│  • LLM Service (RAG)                    │
└─────────────────────────────────────────┘
              │
              ↓
┌─────────────────────────────────────────┐
│      Externe Integrationen              │
├─────────────────────────────────────────┤
│  • GitHub/GitLab (Submissions)          │
│  • mybinder.org (Ausführung)            │
│  • FAIRUM (Rechner-Ressourcen)          │
│  • GWDG/KISSKI (LLM API)                │
└─────────────────────────────────────────┘
```

### Daten-Fluss

1. **Modell-Entdeckung**
   - Benutzer-Abfrage → Front-end → LLM Service → Modell-Registry → Ergebnisse
   - Metadaten + Visualisierungen zurück zu Front-end

2. **Modell-Exploration**
   - Benutzer wählt Modell → Front-end hole Details
   - JavaScript Engine parsed JSON → Renders Struktur
   - Visualisierungs-API bietet berechnete Outputs

3. **Interaktive Ausführung**
   - Benutzer klickt "Run in Binder"
   - Front-end generiert Binder Link
   - Session startet auf mybinder.org oder FAIRUM
   - Benutzer interagiert mit Live Notebook

---

## GitHub/GitLab Integration

### Submission Workflow

Das Front-end bietet **Links und Status-Updates** während GitHub/GitLab den aktuellen Submission-Prozess behandelt:

1. Benutzer bereitet Modell im DEMOS Format vor
2. Portal bietet Submission-Richtlinien und Template
3. Benutzer submittiert via **GitHub Pull Request** oder **GitLab Merge Request**
4. CI/CD Pipelines triggern automatisch (WP2.2)
5. Front-end zeigt Submission-Status und Validierungs-Ergebnisse
6. Genehmigte Modelle erscheinen in Galerie

**Schlüssel-Punkt:** Keine maßgeschneiderte Review-Schnittstelle nötig - nutze bestehende GitHub/GitLab Workflows

### Status-Verfolgung

- Link zu Submission PR/MR
- CI/CD Pipeline Status Badges
- Validierungs-Ergebnisse Display
- Review-Kommentare Integration
- Merge/Approval Notifications

---

## LLM-powered Search Implementierung

### Automatische Bereicherung

Wenn neue Modelle eingereicht werden, AI Agents:

1. Analysieren Modell-Metadaten und Dokumentation
2. Generieren beschreibende Tags automatisch
3. Erstellen menschenlesbare Zusammenfassungen
4. Identifizieren verwandte Modelle
5. Extrahieren Schlüssel-Features und Parameter

### Such-Fähigkeiten

**Stichwort-Suche:**
```
Eingabe: "Higgs Boson Entdeckung"
Ausgabe: Mit Higgs, LHC, 2012, Entdeckung getaggte Modelle
```

**Semantische Suche:**
```
Eingabe: "Wie ändern Neutrinos ihr Flavor während des Reisens?"
Ausgabe: Neutrino-Oszillations-Modelle, Mixing-Matrizen,
        Materie-Effekte, MSW-Effekt
```

**Cross-Domain Entdeckung:**
```
Eingabe: "Statistische Methoden für seltene Ereignis-Suchen"
Ausgabe: Modelle aus Partikelphysik, Neutrino-Physik,
        Dunkle Materie Suchen
```

### Technologie-Stack

- **RAG Framework:** Abruf von Modell-Metadaten + LLM-Generierung
- **LLM Modell:** Llama 3.1 70B (via GWDG/KISSKI)
- **Vektor-Datenbank:** Für effiziente Ähnlichkeits-Suche
- **Embeddings:** Modell-Beschreibungen und Metadaten vektorisiert
- **API:** Integration mit Front-end Such-Schnittstelle

---

## Skalierbarkeits-Überlegungen

### Kritische Belange

**Validierungs-Feedback-Loop:**
- CI/CD Ausführung für Visualisierungs-Generierung
- Möglicher Ressourcen-Engpass
- Erfordert sorgfältige Ressourcen-Zuteilung

**Lösungen:**
- Priorisierte Tests (schnelle Tests zuerst)
- Caching von Visualisierungs-Ergebnissen
- Inkrementelle Validierung
- Ressourcen-Quoten pro Submission
- Queue-Management für CI/CD Jobs

---

## Entwicklungs-Erfahrung

### RUB-H Team Expertise

**Vorherige Arbeiten:**
- **amplitude-serialization Projekt:** Prototype für Hadron Three-Body Decay Modelle
  - Demonstriert technische Kapazität
  - Erkundet Machbarkeit verschiedener Lösungen
  - Bietet Grundlage für DEMOS Portal

**GPT@RUB Projekt:**
- Erfahrung mit Frontier LLM Zugriff
- Bedient tausende RUB Studenten und Mitarbeiter
- Infrastruktur und Skalierungs-Wissen
- Schnittstellen-Design Erfahrung

**Zusammenarbeit:**
- GWDG/KISSKI Konsortium Partnership untersucht
- Zugriff auf Llama 3.1 70B via API
- Budget für Entwicklungs- und Test-Phase

---

## Zeitplan & Meilensteine

| Datum | Meilenstein | Beschreibung |
|------|-----------|-------------|
| **2026.Q2** | Portal bereitgestellt | Öffentliche Web-Schnittstelle zugänglich |
| **2026.Q2** | JS Visualisierung | Modell-Struktur Visualisierung funktioniert |
| **2026.Q3** | Modell-Galerie | 10+ kuratierte Beispiele angezeigt |
| **2027.Q3** | Binder Integration | Interaktive Ausführung operativ |
| **2028.Q2** | LLM Suche | Natürliche Sprach-Modell Entdeckung |

---

## Liefergegenstände

### Software-Komponenten

- [ ] React.js Web-Anwendung (Open Source)
- [ ] JavaScript Visualisierungs-Engine
- [ ] LLM Such-Schnittstelle
- [ ] Binder Integrations-Modul
- [ ] API Client Bibliotheken

### Dokumentation

- [ ] Benutzer-Handbuch für Portal-Navigation
- [ ] Modell-Submission Richtlinien
- [ ] Visualisierungs-Engine API Docs
- [ ] Such-Abfrage Beispiele
- [ ] Binder Nutzungs-Anweisungen

### Inhalte

- [ ] Modell-Galerie mit 10+ Beispielen bis 2027.Q3
- [ ] Dokumentation für Domain-spezifische Bausteine
- [ ] Tutorial Notebooks
- [ ] Video-Demonstrationen

---

## Erfolgs-Metriken

✅ Portal erhält 100+ Unique Visitors pro Monat
✅ Modell-Galerie Features 10+ diverse Beispiele
✅ LLM Suche gibt relevante Ergebnisse zurück (>80% Benutzer-Zufriedenheit)
✅ Binder Sessions starten erfolgreich (>90% Erfolgsquote)
✅ Benutzer-Feedback Surveys zeigen positive Erfahrung (>4/5 Durchschnitts-Rating)
✅ JavaScript Visualisierung rendered komplexe Modelle korrekt
✅ Response-Zeit <2 Sekunden für Such-Abfragen

---

## Zusammenarbeits-Punkte

### Intern (DEMOS Projekt)

- **WP2.2 (HZDR):** REST API Spezifikation, CI/CD Status Integration
- **WP2.3 (TUDO):** HEPData/Zenodo Links, Metadaten-Standards
- **WP3.1:** Dokumentations-Inhalte, Tutorials
- **WP3.2:** Showcase-Modelle für Galerie

### Extern

- **FAIRUM Projekt:** Föderalisierte Rechner-Ressourcen für Binder
- **GWDG/KISSKI:** LLM API Zugriff
- **mybinder.org:** Ausführungs-Umgebungs-Infrastruktur
- **GitHub/GitLab:** Submission und Review Workflows

---

## Risiko-Minderung

| Risiko | Impact | Minderung |
|--------|--------|-----------|
| LLM API Kosten übersteigen Budget | Mittel | Partnership mit GWDG/KISSKI, Open-Source Modell Fallback |
| Binder Ressourcen-Limitierungen | Mittel | FAIRUM Zusammenarbeit, Ressourcen-Quoten |
| CI/CD Überload | Hoch | Priorisierte Tests, Caching, Queue Management |
| Benutzer-Adoption langsam | Mittel | Pillar 3 Outreach, Workshops, Dokumentation |
| Technische Schuld-Ansammlung | Mittel | Code Reviews, Refactoring Sprints, CI Testing |

---

## Verbindung zu Projekt-Zielen

Dieses Arbeitspaket unterstützt direkt die DEMOS Mission zur **Demokratisierung von Modellen** durch:

1. **Barrieren senken** - Intuitive Schnittstelle zugänglich für alle Forscher
2. **Entdeckung ermöglichen** - LLM Suche hilft Benutzern relevante Modelle zu finden
3. **Exploration erleichtern** - Interaktive Visualisierung und Binder Ausführung
4. **Transparenz fördern** - Offene Anzeige von Modell-Struktur und Metadaten
5. **Zusammenarbeit ermutigen** - GitHub/GitLab Workflows fördern Community-Beitrag

---

## Nächste Schritte

Nach Exploration von WP2.1, weiter zu:

- [WP2.2: Back-end Registry & CI/CD →](wp2-2-backend.md)
- [WP2.3: Interoperabilität →](wp2-3-interoperability.md)
- [Zurück zu Pillar 2 Übersicht →](index.md)
