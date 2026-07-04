# UI Framework

A layered UI framework for Unity built around [Zenject](https://github.com/modesttree/Zenject).

- **Views** — `View` / `IView` with lifecycle events and an awaitable close (`Task CloseAwaiter`).
- **Schema-driven layers** — `UISchema` (ScriptableObject) describes layers and rendering order; `UIRoot` materializes them.
- **Window systems** — pluggable strategies per layer: simple, single (one window at a time), stack (back-navigation), and world-space variants with a dedicated world UI camera.
- **Build processors** — `IUIBuildProcessor` hook to post-process every created view (e.g. wiring UI audio).
- **Zenject integration** — installers, `PlaceholderFactory`-based view creation, per-view sub-containers.

## Requirements

- Unity 6000.0+
- [Zenject](https://github.com/modesttree/Zenject) present in the consuming project (the package's assembly references it by name `Zenject`).

## Installation

Add via Package Manager → *Install package from git URL*:

```
https://github.com/ega-ega/UIFramework.git?path=UnityUIFramework/Packages/com.egaega.uiframework
```

Or in `Packages/manifest.json`:

```json
"com.egaega.uiframework": "https://github.com/ega-ega/UIFramework.git?path=UnityUIFramework/Packages/com.egaega.uiframework"
```

## Repository layout

- `UnityUIFramework/` — host Unity project used to develop the package (includes Zenject under `Assets/Plugins` as a dev-time dependency).
- `UnityUIFramework/Packages/com.egaega.uiframework/` — the package itself; this is what consumers install.

## License

MIT
