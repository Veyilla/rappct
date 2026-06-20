# rappct

> 🇩🇪 [Deutsch](#deutsch) · 🇬🇧 [English](#english)
>
> This is a fork of [cpjet64/rappct](https://github.com/cpjet64/rappct), maintained by [@Veyilla](https://github.com/Veyilla).
> Extended with `UseCase::McpServerSandbox` — an LPAC sandbox preset for MCP server processes.

---

## 🇩🇪 Deutsch

Rust-Toolkit für die Arbeit mit Windows AppContainer- und LPAC-Prozessgrenzen.

Die Projektdokumentation befindet sich in [`docs/`](./docs/).

Einstiegspunkt: [`docs/index.md`](./docs/index.md)

### Lokaler Release-Prozess (kein GitHub-Action-Publish)

Dieses Repository verwendet einen rein lokalen Release-Ablauf. Der Veröffentlichungsinhalt wird durch eine Manifest-Allowlist in `include` gesteuert:

- `LICENSE`
- `README.md`
- `Cargo.toml`
- `src/**`
- `examples/**`
- `tests/**`

Die Release-Kette läuft wie folgt ab:

- `just release-version-check` prüft, ob die Crate-Version höher ist als die auf crates.io veröffentlichte Version.
- `just release-gate` führt Formatierungs-, Lint- und Testprüfungen sowie Paketliste und Trockenlauf-Checks auf einem **sauberen Arbeitsverzeichnis** aus.
- `just release-gate-log` führt den vollständigen Gate-Prozess mit einem zeitgestempelten Protokoll in `output/release-gate` durch.
- `just release` führt den vollständigen Gate-Prozess aus und fragt anschließend zur ausdrücklichen Bestätigung auf.

`cargo publish` darf nicht direkt außerhalb dieses Ablaufs ausgeführt werden.

---

## 🇬🇧 English

Rust toolkit for working with Windows AppContainer and LPAC process boundaries.

Project documentation is in [`docs/`](./docs/).

Start here: [`docs/index.md`](./docs/index.md)

### Local release process (no GitHub Action publish)

This repository uses a local-only release flow. Publish payload is controlled by a manifest `include` allow-list:

- `LICENSE`
- `README.md`
- `Cargo.toml`
- `src/**`
- `examples/**`
- `tests/**`

The release chain is:

- `just release-version-check` verifies crate version is greater than the published crate on crates.io.
- `just release-gate` runs formatting/lints/tests, packaging list, and dry-run checks on a **clean working tree**.
- `just release-gate-log` runs the full gate with a timestamped transcript in `output/release-gate`.
- `just release` runs the full gate and then prompts for explicit publish confirmation.

Do not run `cargo publish` directly outside this flow.
