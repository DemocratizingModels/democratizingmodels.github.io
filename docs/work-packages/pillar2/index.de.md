---
title: Pillar 2 - Portal & Infrastruktur
---

# Pillar 2: Portal & Infrastruktur

Die zweite Schlüsselkomponente der Initiative ist die Entwicklung einer **robusten und skalierbaren digitalen Infrastruktur**, um die Entdeckung, Validierung und das Teilen von Modellen über Disziplinen hinweg zu erleichtern. Dieses Portal wird als zentraler Hub fungieren, wo Forscher auf Modelle zugreifen, neue beitragen und mit Tools und Ressourcen interagieren können, die interdisziplinäre Zusammenarbeit unterstützen.

---

## Übersicht

Pillar 2 konzentriert sich auf die Schaffung eines umfassenden digitalen Ökosystems, bestehend aus:

1. **Front-end Portal** - Benutzer-zuständige Schnittstelle für Modell-Entdeckung und Exploration
2. **Back-end Registry** - Modell-Verwaltung, Validierung und CI/CD Infrastruktur
3. **Interoperabilität** - Integration mit bestehenden Forschungsdaten-Plattformen (HEPData, Zenodo)

Das Portal wird Forschern einfachen Zugang zu rechnerischen Modellen bieten, die eine einfache Integration in ihre Workflows ermöglichen. Darüber hinaus wird die Infrastruktur bestehende Forschungs-Datenplattformen und Repositories nutzen und sich in das wissenschaftliche Ökosystem integrieren, ohne Hardware-Investitionen zu duplizieren.

---

## Arbeitspakete

### WP2.1: Front-end Portal

Das Front-end bietet eine intuitive Schnittstelle zur Exploration, Entdeckung und Dokumentation von Physik-Modellen. Features beinhalten eine Modell-Galerie, LLM-powered Discovery, interaktive JavaScript Visualisierung und Binder Integration für Live-Ausführung.

**Leitung:** RUB-H

[Mehr erfahren →](wp2-1-frontend.md)

### WP2.2: Back-end Registry & CI/CD

Das Back-end fungiert als Verbindung zwischen dem Front-end und der Modell-Datenbank. Es bietet ein Modell-Registry, automatisierte Validierungs-Pipelines mit GitHub Actions und RESTful APIs für Modell-Zugriff.

**Leitung:** HZDR

[Mehr erfahren →](wp2-2-backend.md)

### WP2.3: Interoperabilität

Integration mit bestehender Infrastruktur inklusive HEPData, Zenodo und Domain-spezifischen Repositories. Etablierung von maschinenlesbaren Metadaten-Standards mit DOI und Container UUID Referenzen.

**Leitung:** TUDO

[Mehr erfahren →](wp2-3-interoperability.md)

---

## Schlüssel-Ziele

Die Ziele von Pillar 2 sind:

1. **Demokratisierung des Zugriffs** auf Forschungsmodelle durch ein intuitives Web-Portal
2. **Automatisierung der Validierung** mit CI/CD-Pipelines
3. **Ermöglichung der Entdeckung** durch LLM-powered Such-Fähigkeiten
4. **Sicherung der Interoperabilität** mit bestehenden Daten-Repositories
5. **Unterstützung Live-Interaktion** via Binder und föderalisierte Rechner-Ressourcen
6. **Qualität beibehalten** durch automatisierte Tests und Review-Workflows

---

## Zeitplan

| Meilenstein | Quartal | Beschreibung |
|-----------|---------|-------------|
| **M2** | 2026.Q4 | Portal bereitgestellt, Modell-Registry etabliert, grundlegende Konstruktionen dokumentiert |
| **M5** | 2027.Q3 | Domain-spezifische Bausteine dokumentiert, Galerie mit 10+ Beispielen |
| **M7** | 2028.Q1 | Upload/Validierung funktioniert mit CI Tools, Engine Tests bei 70%+ |
| **M8** | 2028.Q2 | Sprachmodell bestimmt Tags, LLM Suche operativ |

---

## Personalkraft-Zuteilung

Insgesamt Personenjahre für Pillar 2: **2,5 Jahre**

| Arbeitspaket | Personenjahre | Leit-Institution |
|--------------|--------------|------------------|
| WP2.1 Front-end | 1,0 | RUB-H |
| WP2.2 Back-end | 0,7 | HZDR |
| WP2.3 Interoperabilität | 0,5 | TUDO |
| Projektmanagement | 0,3 | Verteilt |

---

## Technische Architektur

### Front-end Stack

- **Framework:** React.js für Modularität und Skalierbarkeit
- **Visualisierung:** JavaScript Engine zum Parsen verschachtelter Modelle
- **Suche:** LLM-powered Discovery mittels RAG (Retrieval Augmented Generation)
- **Ausführung:** Binder Integration mit mybinder.org und FAIRUM Ressourcen
- **API:** REST APIs für Echtzeit-Metadata Abruf

### Back-end Stack

- **Versionskontrolle:** GitHub/GitLab für Modell-Registry
- **CI/CD:** GitHub Actions für automatisierte Validierung
- **Datenbank:** Modell-Dateien verknüpft mit oder in dedizierter Datenbank gespeichert
- **API:** RESTful Schnittstellen für Modell-Zugriff und Operationen
- **Validierung:** Automatisierte Integritäts- (Checksum) und Korrektheitsprüfungen (Referenzpunkte)

### Integrations-Punkte

- **HEPData:** Direkte Verknüpfung für Partikelphysik Likelihoods
- **Zenodo:** DOI-basierte Referenzen und Langzeit-Bewahrung
- **GitHub/GitLab:** Pull/Merge Request Workflows für Submissions
- **FAIRUM:** Föderalisierte Rechner-Ressourcen für interaktive Sessions

---

## Erwartete Ergebnisse

### Plattform-Liefergegenstände

1. **Public Web Portal**
   - Responsive, benutzerfreundliche Schnittstelle
   - Modell-Galerie mit Kuratierten Beispielen
   - Such-Funktionalität (Stichwort + LLM-powered)
   - Interaktive Visualisierung der Modell-Struktur
   - Link zu GitHub/GitLab für Submissions

2. **Modell-Registry**
   - Zentralisiertes Metadata-Repository
   - UUID-basierte Modell-Identifikation
   - DOI Integration für Zitationen
   - Versions-Verfolgung
   - Such-Indizes

3. **CI/CD Infrastruktur**
   - Automatisierte Validierungs-Pipelines
   - Checksum Verifikation
   - Referenzpunkt-Tests
   - Performance-Visualisierung Generierung
   - Status-Berichterstattung zu Front-end

4. **Integrations-Tools**
   - HEPData Connector
   - Zenodo Linker
   - GitHub Actions Workflows
   - API-Dokumentation

### Dokumentation

- Plattform Benutzer-Handbuch
- Modell-Submission Richtlinien
- API Referenz-Dokumentation
- Integrations-Beispiele
- Best Practices für Modell-Vorbereitung

---

## Konsortium-Beiträge

### Führende Rollen

- **RUB-H** - Front-end Entwicklung, Portal Design, LLM Integration
- **HZDR** - Back-end Infrastruktur, CI/CD Pipelines, Registry
- **TUDO** - Interoperabilität, HEPData/Zenodo Integration, Koordination

### Unterstützende Rollen

- **TUM** - Binder Integration, FAIRUM Zusammenarbeit
- **LMU, SC** - Modell-Validierungs-Beispiele
- **MPP** - Containerisierungs-Unterstützung
- **JGU** - AmpTools Integration-Tests

---

## Integration mit bestehender Infrastruktur

Das Portal **ersetzt nicht** bestehende Infrastruktur. Stattdessen:

✅ **Erweitert** HEPData mit standardisiertem Modell-Zugriff
✅ **Nutzt** Zenodo für Langzeit-Bewahrung
✅ **Erweitert** GitHub/GitLab Workflows für Submissions
✅ **Verbindet** bestehende Repositories durch vereinheitlichte APIs
✅ **Bereichert** Metadaten durch maschinenlesbare Standards

Bestätigungsschreiben von HEPData und Zenodo Teams bestätigen Unterstützung für diesen Integrations-Ansatz.

---

## Benutzer-Journey

### Modell-Entdeckung

1. Benutzer besucht Portal und sucht nach Modellen (Stichwort oder natürliche Sprache)
2. LLM-powered Suche gibt relevante Modelle mit Zusammenfassungen zurück
3. Benutzer durchsucht Modell-Galerie mit Visualisierungen
4. Benutzer sieht detaillierte Metadaten, DOI und Dokumentation

### Modell-Exploration

1. Benutzer wählt interessierendes Modell
2. JavaScript Visualisierung zeigt Modell-Struktur
3. Benutzer klickt "Run in Binder" für interaktive Exploration
4. Session verbindet sich mit mybinder.org oder FAIRUM Ressourcen
5. Benutzer führt aus und modifiziert Modell in Live Notebook

### Modell-Submission

1. Benutzer bereitet Modell im DEMOS Format vor
2. Benutzer submittiert via GitHub/GitLab Pull/Merge Request
3. CI/CD Pipeline validiert Submission automatisch
4. Manuelle Review adressiert Relevanz und Sicherheit
5. Genehmigtes Modell erscheint im Portal mit generierter Metadata

---

## Technische Herausforderungen & Lösungen

### Skalierbarkeit

**Herausforderung:** Validierungs-Feedback-Loop Ressourcen-Verbrauch
**Lösung:** Sorgfältige Ressourcen-Zuteilung, priorisierte Tests, Caching-Strategien

### LLM Kosten

**Herausforderung:** API-Kosten für Sprachmodell-Abfragen während Entwicklung
**Lösung:** Budget-Zuteilung (angefordert), Exploration von GWDG/KISSKI Konsortium-Partnership für Llama 3.1 70B Zugriff

### Latenz

**Herausforderung:** Interaktive Session-Startup-Zeit
**Lösung:** FAIRUM Zusammenarbeit für föderalisierte Ressourcen mit reduzierter Latenz

### Wartung

**Herausforderung:** Langfristige Plattform-Nachhaltigkeit
**Lösung:** CI-basierte Wartungs-Pipelines, Community Governance (Pillar 3)

---

## Erfolgskriterien

Pillar 2 wird als erfolgreich erachtet, wenn:

✅ Portal ist öffentlich zugänglich und responsiv
✅ Modell-Registry enthält 3+ Modelle pro ErUM Domain
✅ LLM-powered Suche liefert relevante Ergebnisse
✅ CI/CD validiert Modelle automatisch (70%+ Test-Abdeckung)
✅ Interaktive Binder Sessions starten erfolgreich
✅ HEPData und Zenodo Integration operativ
✅ API-Dokumentation vollständig und nutzbar
✅ Benutzer-Feedback Surveys zeigen positive Zufriedenheit

---

## Verbindung zu anderen Pillars

**Pillar 1 (Format)** → Bietet den DEMOS-Standard, den die Infrastruktur implementiert
**Pillar 2 (Infrastruktur)** → Bietet die Plattform zum Teilen und Entdecken
**Pillar 3 (Community)** → Treibt Adoption voran und bevölkert das Registry mit Modellen

---

## Nächste Schritte

Erkunden Sie die detaillierten Arbeitspakete:

- [WP2.1: Front-end Portal →](wp2-1-frontend.md)
- [WP2.2: Back-end Registry & CI/CD →](wp2-2-backend.md)
- [WP2.3: Interoperabilität →](wp2-3-interoperability.md)
