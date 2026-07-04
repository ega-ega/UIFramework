# UI Framework — Roadmap

## Status

Repo bootstrapped **2026-07-04**. The UI framework was extracted from the
TopDownShooter project into UPM package `com.egaega.uiframework` (v0.1.0,
tagged) with a TimeKit-style layout: host Unity project `UnityUIFramework/`
(Unity 6000.2.7f2) + the package under `Packages/`.

Key facts carried over from the extraction:

- Namespace `UI.Framework` and all script meta GUIDs are preserved from the
  source project — TopDownShooter can later switch to this package without
  losing prefab references.
- Zenject is a hard dependency (referenced by asmdef name `Zenject`); it lives
  in the host's `Assets/Plugins` as a dev-time copy (test suites trimmed —
  their assets exceeded the Windows path-length limit).
- Dead duplicate `SimpleWindowsSystem` was dropped during extraction (zero
  code/asset references in the source project).
- v0.1.0 is a verbatim transfer: compile-verified, no behavior changes.

## Next (improvement backlog, unordered)

- [ ] Rework `View` lifecycle: `Close()` currently both deactivates and
      destroys; `Open()` resolves a stale close-awaiter — split hide vs
      destroy, tighten the awaiter contract.
- [ ] Define the public API surface: most types sit in
      `UI.Framework.Implementation` as `internal` — decide what a consumer
      is meant to touch.
- [ ] Consider splitting `UIFramework.Core` (DI-agnostic) +
      `UIFramework.Zenject` assemblies once the API settles.
- [ ] Samples (`Samples~`) and tests — deferred at v0.1.0 by decision.

## Working mode

Development happens in this repo directly: open `UnityUIFramework/` in Unity
and drive it via MCP from a Claude Code session started at the repo root.
