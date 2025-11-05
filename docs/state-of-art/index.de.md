---
title: Stand der Technik
---

# Stand der Technik

## Das vielfältige ErUM-Software-Ökosystem

Die ErUM-Disziplinen werden von einem unglaublich **vielfältigen und fragmentierten Software-Ökosystem** unterstützt, in dem Modelle implementiert und verwendet werden. Forschende nutzen eine breite Palette von Programmiersprachen, darunter:

- **C++** - Leistungskritische Anwendungen
- **Fortran** - Legacy-Scientific-Computing
- **Python** - Moderne Datenanalyse
- **Julia** - Hochleistungs-Numerik
- **Mathematica** - Symbolische Mathematik

Jede Sprache ist auf spezifische Rechenbedürfnisse und Community-Präferenzen zugeschnitten.

## Aktuelle Praktiken

### Individuelle Implementierung

Meistens schreiben Forschende **individuellen Analysecode** für spezifische Studien, einschließlich detaillierter Modelle für besondere Anwendungsfälle. Diese kodierten Modelle werden oft durch private Kommunikation auf Anfrage geteilt.

### Manuelle Reproduktion

In anderen Fällen müssen **komplexe analytische Ausdrücke** aus wissenschaftlichen Publikationen manuell reproduziert werden – ein Prozess, der nicht nur **fehleranfällig**, sondern häufig auch **nicht durchführbar** ist aufgrund unvollständiger Informationen in den Publikationen.

### Rekonstruktion von Legacy-Code

Gelegentlich müssen Forschende mühsam **Modellcode aus jahrzehntealten Publikationen rekonstruieren**, nur um ihn in moderne Workflows einzubinden. Viele Forschungsmodelle bleiben **unzugänglich** aufgrund von:

- Fehlenden ausreichenden Informationen in der Literatur
- Erheblichem Aufwand für die Vorbereitung zur Wiederverwendung
- Komplexen individuellen Code-Abhängigkeiten
- Veralteten oder Legacy-Software-Anforderungen
- Komplexen Machine-Learning-Techniken

Dieses Problem ist besonders akut für Modelle, die auf komplexem individuellem Code beruhen, wodurch eine breitere Zusammenarbeit behindert wird.

### Begrenzte Versionskontrolle

Für Code-Fragmente, die durch direkte Kommunikation geteilt werden, werden **Versionskontrolltechniken** und **Zenodo-Referenzen** zunehmend häufiger. Dennoch bleiben diese Praktiken eher die **Ausnahme als die Regel**.

---

## Der Bedarf an Vereinheitlichung

Diese Heterogenität stellt eine grundlegende Herausforderung für die Zusammenarbeit sowohl über Forschungsdomänen hinweg als auch innerhalb einzelner Felder dar.

!!! note "Respekt für etablierte Werkzeuge"
    Etablierte Werkzeuge, Frameworks und Praktiken können nicht einfach verworfen werden – sie sind zeitgeprüft und tief in ihren jeweiligen Communities verankert.

### Der DEMOS-Ansatz

Stattdessen wird dringend ein **vereinheitlichender Standard** benötigt, der:

- Die Vielfalt bestehender Ökosysteme respektiert
- Nahtlose Zusammenarbeit und Interoperabilität ermöglicht
- Als Brücke zwischen Werkzeugen, Repositories und Disziplinen fungiert
- Forschenden ermöglicht, Modelle über Disziplinen hinweg zu teilen, zu kombinieren und zu erweitern
- Bestehende Workflows nicht stört

Durch die Bereitstellung des neuen DEMOS-Standards als Kommunikationsschicht zwischen Werkzeugen, Repositories und Disziplinen zielt DEMOS darauf ab, eine vernetzte und kollaborative Forschungsumgebung zu schaffen, die neue Möglichkeiten für interdisziplinäre Innovation eröffnet.

---

## Modellkomplexität über Domänen hinweg

Es ist wichtig zu erkennen, dass die **Definition eines Modells** zwischen verschiedenen Feldern variieren kann, von:

- **Einfachen Funktionen**, die nur von wenigen Parametern abhängen
- **Komplizierten, mehrdimensionalen Objekten**, die von Tausenden von Parametern abhängen
- **Gebinnten Modellen**, die in einer Observablen diskretisiert sind
- **Glatten analytischen Funktionen**

Dennoch sind viele Modelleigenschaften und Bausteine **über die ErUM-Disziplinen hinweg gemeinsam**, was den Bedarf für einen einheitlichen Modellstandard unterstreicht, um eine Modell-Sharing-Plattform zu ermöglichen.

---

## Domänenspezifischer Stand der Technik

Im Folgenden untersuchen wir die ErUM-Felder hinsichtlich Modellkomplexität sowie aktueller Praktiken zum Teilen, Reproduzieren und Erweitern von Modellen.

### [Teilchenphysik →](particle-physics.md)

Überblick über das ROOT/RooFit-Ökosystem, PyHF, den HS3-Standard und statistische Modellierung in der Hochenergiephysik.

### [Hadronenphysik →](hadron-physics.md)

Aktuelle Praktiken in Hadronenspektroskopie, Partialwellenanalyse und Amplitudenmodellen bei LHCb, Belle II, BESIII und COMPASS.

### [Kernphysik →](nuclear-physics.md)

Ab-initio-Kernstrukturberechnungen, chirale effektive Feldtheorie und Nukleon-Nukleon-Wechselwirkungen.

### [Neutrinophysik →](neutrino-physics.md)

Neutrino-Oszillationsmodelle, Detektorantwortfunktionen und globale Fits bei IceCube, Super-K und anderen Experimenten.

### [Laserphysik →](laser-physics.md)

Laser-Materie-Wechselwirkungsmodelle, Warm-Dense-Matter-Physik und Strukturfaktoren für Röntgenuntersuchungen.

### [Astroteilchenphysik →](astroparticle-physics.md)

Kosmische-Strahlen-Propagation, Multi-Messenger-Modelle und Quellenmodellierung mit CRPropa, GALPROP und CORSIKA.

---

## Zusammenfassung

Zusammenfassend stellen **Modelle einen unschätzbaren Teil** der Beschreibung physikalischer Effekte und der Interpretation experimenteller Daten über alle Domänen der ErUM-Felder hinweg dar.

Dennoch wird der Austausch von Modellen zwischen Experimenten, über Felder hinweg oder zwischen Experiment und Theorie **erheblich behindert** durch das Fehlen eines etablierten Standards.

Wir streben daher an, einen solchen Standard zu etablieren – **den DEMOS-Standard** – zusammen mit einer Plattform, die den Austausch von Modellen über Disziplinen hinweg erleichtern und einfachen, offenen Zugang für eine breite Palette von Praktikern bieten wird.

Um diese Ziele zu erreichen, ist unser Konsortium einzigartig positioniert und vereint ein vielfältiges Spektrum an Expertise von experimentellen und theoretischen Physikern über die ErUM-Disziplinen hinweg – eine solide Grundlage für den Erfolg unseres Vorschlags.
