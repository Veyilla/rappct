# rappct

Rust-Toolkit für die Arbeit mit Windows AppContainer- und LPAC-Prozessgrenzen.

Die Projektdokumentation befindet sich in [`docs/`](./docs/).

Einstiegspunkt: [`docs/index.md`](./docs/index.md)

## Lokaler Release-Prozess (kein GitHub-Action-Publish)

Dieses Repository verwendet einen rein lokalen Release-Ablauf. Der Veröffentlichungsinhalt wird durch eine Manifest-Allowlist in `include` gesteuert:

- `LICENSE`
- `README.md`
- `Cargo.toml`
- `src/**`
- `examples/**`
- `tests/**`

Die Release-Kette läuft wie folgt ab:

- `just release-version-check` prüft, ob die Crate-Version höher ist als die aktuell auf crates.io veröffentlichte Version.
- `just release-gate` führt Formatierungs-, Lint- und Testprüfungen sowie die Paketliste und Trockenlauf-Checks auf einem **sauberen Arbeitsverzeichnis** aus.
- `just release-gate-log` führt den vollständigen Gate-Prozess mit einem zeitgestempelten Protokoll in `output/release-gate` durch.
- `just release` führt den vollständigen Gate-Prozess aus und fragt anschließend zur ausdrücklichen Bestätigung des Publizierens auf.

`cargo publish` darf nicht direkt außerhalb dieses Ablaufs ausgeführt werden.

---

*Dies ist die deutschsprachige Übersetzung von [`README.md`](./README.md).*

---

> **Fork-Hinweis:** Dieses Repository ist ein Fork von [cpjet64/rappct](https://github.com/cpjet64/rappct).
> Zusätzliche Erweiterungen in diesem Fork:
> - `UseCase::McpServerSandbox` — Isolierte LPAC-Sandbox für MCP-Server-Prozesse ohne Netz- oder Bibliotheksrechte
