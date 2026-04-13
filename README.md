# Auto Color

![Abstract colorful editor chrome — title, side, and status bands](images/readme-hero.png)

**Auto Color** gives every folder you open a **stable, recognizable color**—pastel **title, activity, and status bars** plus a **subtle hue wash** across the rest of the workbench. Same project path → same palette; different repos → different hues. Works in **VS Code** and **Cursor**.

> Previously published as **AutoColorWorkspace** (`WyvernSystemsLLC.autocolor-workspace`). This listing is a **new extension** (`WyvernSystemsLLC.auto-color`) with renamed commands and settings. Uninstall the old one and remove legacy `autocolor-workspace.*` keys from settings if you migrate.

## At a glance

| | |
|--|--|
| **Setup** | None — runs when the workspace loads |
| **Chrome** | Vibrant pastels on title, activity, and status bars (optional **head + footer only** skips the activity bar) |
| **Surfaces** | Editor, sidebar, tabs, panel, terminal, welcome/empty editor, and more—**tinted with your workspace hue** at low saturation |
| **Depth** | Surface lightness follows **VS Code’s default dark-theme steps** (sidebar slightly above editor, tabs above that, etc.) so layout still reads clearly |
| **Borders** | Section dividers use a **lighter line** in the same hue so splits stay visible |
| **Text** | **Background keys only** on surfaces—syntax and list labels stay on your color theme |
| **Math** | Golden-angle hue and φ-weighted saturation/lightness for the chrome bars (calm, not neon) |
| **Persistence** | Writes `workbench.colorCustomizations` into **this workspace’s** `.vscode/settings.json` |
| **Merge** | Other customization keys you set manually are preserved |

## Why use it

- **Many windows open?** Spot the right project by bar color and overall tint.
- **Multi-root workspaces** use the **first root folder** path as the color seed unless you randomize (see below).

## Features

- Apply on startup and when workspace folders change
- Per-workspace enable/disable and a global master switch
- **Randomize color** — new hue on demand; seed stored in workspace settings
- **Reset to default color** — drop the seed and go back to path-derived colors
- **Set color scope** — all three bars, or title + status only (activity bar unchanged)
- Accessible **chrome** foregrounds from bar background luminance

## Commands

Open the Command Palette (**Cmd+Shift+P** / **Ctrl+Shift+P**):

| Command | What it does |
|--------|----------------|
| **Auto Color: Enable (all windows)** | Global on; applies in the current workspace. |
| **Auto Color: Disable (all windows)** | Global off; clears this extension’s keys here. |
| **Auto Color: Enable for this workspace** | On for this workspace (if global is on). |
| **Auto Color: Disable for this workspace** | Off here only; clears extension keys. |
| **Auto Color: Set color scope** | **All**: title + activity + status. **Head and footer**: title + status only. |
| **Auto Color: Randomize color** | Picks a new seed and repaints the whole palette. |
| **Auto Color: Reset to default color** | Clears `randomSeed`; color comes from the folder path again. |

## Settings

| ID | Scope | Default | Meaning |
|----|--------|---------|---------|
| `auto-color.enabled` | Application | `true` | Global on/off. |
| `auto-color.workspaceDisabled` | Window | `false` | Disable only this workspace. |
| `auto-color.scope` | Window | `all` | `all` or `headFooter` (title + status only). |
| `auto-color.randomSeed` | Window | `0` | Non-zero = use this seed instead of the path. Set by **Randomize**; `0`/unset = path-based. |

## What gets customized

The extension sets **many** `workbench.colorCustomizations` keys, including:

- **Chrome:** title / activity / status backgrounds and foregrounds (per scope).
- **Editor area:** `editor.background`, gutter, line highlight, empty group / pane, welcome page, walkthrough embed.
- **Tabs & groups:** tab strip, tab backgrounds and borders, group borders.
- **Sidebar & lists:** sidebar, section headers, list hover/selection.
- **Panel & terminal:** panel background and border, terminal background.
- **Misc:** breadcrumbs, editor widgets, quick input, notifications, inputs/dropdowns, debug toolbar, etc.

Disabling the extension or a workspace removes **only** the keys this extension manages (plus a few legacy keys from older versions).

## Requirements

- VS Code **1.85.0** or newer

## Install

### Visual Studio Marketplace

Search for **Auto Color**, or open (after publish):  
`https://marketplace.visualstudio.com/items?itemName=WyvernSystemsLLC.auto-color`

### VSIX

1. Build or download `auto-color-<version>.vsix`.
2. **Extensions → … → Install from VSIX…**

## Build a VSIX (manual upload)

```bash
npm install
npm run compile
npx vsce package
```

This produces `auto-color-<version>.vsix` in the project root. Upload via [Publisher Management](https://marketplace.visualstudio.com/manage) if you publish outside the CLI.

## Artwork

Extension icon and readme hero live under `images/`. Original artwork for this extension is included in the repo under the same **MIT** license as the code.

## Changelog

See [CHANGELOG.md](CHANGELOG.md).

## License

[MIT](LICENSE)

## For developers

```bash
npm install
npm run compile
```

Press **F5** to launch an Extension Development Host.

- Source: [wyvernsystems/auto-color-vscode-extension](https://github.com/wyvernsystems/auto-color-vscode-extension)

### Publish (CLI)

```bash
npx vsce login <publisher-id>
npx vsce publish
# or: npx vsce publish patch
```

Ensure `publisher` in `package.json` matches your Marketplace publisher ID.
