# Sicherheitsrichtlinie / Security Policy

> 🇩🇪 [Deutsch](#deutsch) · 🇬🇧 [English](#english)

---

## <a id="deutsch"></a>🇩🇪 Deutsch

### Unterstützte Versionen

Dieses Repository folgt einem zentralen Entwicklungsmodell. Sicherheits-Fixes werden direkt auf dem Hauptzweig (main) vorgenommen und bei Bedarf in langlebige Integrationszweige zusammengeführt. Diese werden Branches genannt.

### Melden einer Sicherheitslücke

Bitte melde potenzielle Sicherheitslücken privat an die Projektverantwortlichen (Maintainer), bevor du einen öffentlichen Fehlerbericht im Issue-Bereich auf GitHub erstellst.

Bitte füge deinem Bericht folgende Details bei:
- Betroffene Dateien, Programmteile (Module) oder Funktionsschalter (Feature-Flags)
- Schritte zum Nachstellen des Problems sowie die erwarteten Auswirkungen
- Details zu deinem System (Windows-Version, Rust-Entwicklerwerkzeuge und verwendete Benutzerrechte, z. B. als Administrator)

Bitte veröffentliche keine Anleitungen oder Details zum Ausnutzen der Sicherheitslücke (Exploits), bevor ein Sicherheits-Update bereitsteht.

### Sicherheitskonzept

Dieses Projekt setzt konsequent auf einen lokalen und selbstgehosteten Arbeitsablauf (Local-First und Self-Hosted):
- Keine externen Cloud- oder CDN-Abhängigkeiten zur Laufzeit
- Lokale CI-Prüfungen (wie `just ci-fast` und `just ci-deep`) vor der Integration sind Pflicht
- Validierung von Abhängigkeiten und Sicherheitswarnungen in der CI (über `cargo deny` und `cargo audit`)
- Sicherheitskritische Windows-Schnittstellen und Systemgrenzen sind durch explizite Prüfungen und Feature-Flags geschützt

### Härtungshinweise für Mitwirkende

- Sicherheitsgrenzen von Sandbox, Authentifizierung, ACLs oder Berechtigungen dürfen nicht geschwächt werden.
- Defensive Fehlerpfade und Berechtigungsprüfungen müssen vollständig getestet sein.
- Telemetrie, Geheimnisse, Passwörter oder Zugangsdaten dürfen niemals im Quellcode, in Tests oder in Skripten landen.
- Die bestehenden Sicherheitsprüfungen in der CI und in lokalen Abläufen müssen aktiv bleiben.

---

## <a id="english"></a>🇬🇧 English

### Supported Versions

This repository follows trunk-style maintenance for active development. Security fixes are applied to the current active branch and then merged into long-lived integration branches as needed.

### Reporting a Vulnerability

Report potential vulnerabilities privately to the maintainers before opening a public issue.

Include:
- affected file/module and feature flags
- reproduction steps and expected impact
- environment details (Windows version/build, Rust toolchain, privileges)

Do not disclose exploit details publicly until a fix is available.

### Security Posture

This project intentionally preserves a strict local-first and self-hosted workflow:
- no required cloud/CDN runtime dependencies
- mandatory local CI gates (`just ci-fast`, `just ci-deep`) before integration
- dependency and advisory validation in CI (`cargo deny`, `cargo audit`, advisory policy script)
- Windows boundary-sensitive functionality guarded by explicit checks and feature flags

### Hardening Notes for Contributors

- Avoid weakening sandbox, auth, ACL, or capability boundaries.
- Keep defensive error paths and capability checks fully tested.
- Do not introduce telemetry, secrets, or credential material into source, tests, or scripts.
- Maintain existing security checks in CI and local workflows.
