# AGENTS.md

## Stack

- **Astro 6 beta** (`^6.0.0-beta.11`) — not stable; APIs may shift between minor releases.
- **Tailwind CSS v4** via `@tailwindcss/vite` plugin. Uses `@import "tailwindcss"` syntax, not the v3 `@tailwind` directives.
- **TypeScript** with `astro/tsconfigs/strict`.
- **Node >= 22.12.0** (enforced in `package.json` `engines`).

## Commands

| Action | Command |
|--------|---------|
| Install deps | `yarn` (lockfile is `yarn.lock`) |
| Dev server | `yarn dev` → `localhost:4321` |
| Production build | `yarn build` → `dist/` |
| Preview build | `yarn preview` |

There are **no test, lint, or typecheck scripts** configured. `yarn build` is the only verification step available.

## Architecture

Single-page app. Three Astro components assembled in `src/pages/index.astro`:

```
InputTextArea (left)  ↔  ControlPanel (center)  ↔  OutputTextArea (right)
```

**Inter-component communication uses custom DOM events**, not shared state:

| Event | Emitter | Listener |
|-------|---------|----------|
| `json-valid` | InputTextArea | (currently unused) |
| `json-invalid` | InputTextArea | (currently unused) |
| `env-generated` | ControlPanel | OutputTextArea |
| `env-error` | ControlPanel | OutputTextArea |

All scripts run client-side inside `<script>` tags in each `.astro` file. There is no server-side logic.

## Gotchas

- `src/components/Welcome.astro` and `src/assets/` are leftover from the Astro basics template — not used by the app.
- `ControlPanel.astro` contains the conversion logic (`flattenToEnv`, `convertJsonToEnv`) and clipboard operations. It's the largest component.
- `OutputTextArea.astro` has its own inline copy button (separate from the ControlPanel copy button).
- Tailwind classes are used directly in templates — no `tailwind.config.*` file exists (expected for Tailwind v4).
