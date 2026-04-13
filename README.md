# AutoColorWorkspace

![Abstract colorful editor chrome — title, side, and status bands](images/readme-hero.png)

**AutoColorWorkspace** tints the VS Code window chrome so every folder you open gets a **stable, readable color** you can recognize from the corner of your eye. Same project path → same palette; different repos → different hues. Works in **VS Code** and **Cursor**.

## At a glance

| | |
|--|--|
| **Setup** | None — runs when the workspace loads |
| **Colors** | One harmonious hue per workspace, with **lighter/darker shades** on title, activity, and status bars |
| **Math** | Golden-angle hue and φ-weighted saturation/lightness (calm, not neon) |
| **Persistence** | Writes only `workbench.colorCustomizations` keys into **this workspace’s** `.vscode/settings.json` |
| **Your theme** | Merges with existing customizations; other keys are left alone |

## Why use it

- **Many windows open?** Scan by bar color instead of reading the window title.
- **Multi-root workspaces** use the **first root folder** path as the color seed (documented below).
- **Optional scope**: color **all three** bars, or **head + footer only** (title + status) and leave the activity bar to your theme.

## Features

- Automatic apply on startup and when workspace folders change
- Per-workspace enable/disable and a global master switch
- Command **Set color scope** for “all bars” vs “head and footer only”
- Accessible foreground picked from each bar’s background luminance

## Commands

Open the Command Palette (**Cmd+Shift+P** / **Ctrl+Shift+P**) and run:

| Command | What it does |
|--------|----------------|
| **AutoColorWorkspace: Enable (all windows)** | Turns global coloring on and applies in the current workspace. |
| **AutoColorWorkspace: Disable (all windows)** | Turns global coloring off and clears this extension’s keys here. |
| **AutoColorWorkspace: Enable for this workspace** | Turns coloring back on for this workspace (if global is on). |
| **AutoColorWorkspace: Disable for this workspace** | Off for this workspace only; clears extension keys. |
| **AutoColorWorkspace: Set color scope** | **All** (default): title + activity + status. **Head and footer**: title + status only. |

## Settings

| ID | Scope | Default | Meaning |
|----|--------|---------|---------|
| `autocolor-workspace.enabled` | Application | `true` | Global on/off. |
| `autocolor-workspace.workspaceDisabled` | Window | `false` | Disable only this workspace. |
| `autocolor-workspace.scope` | Window | `all` | `all` or `headFooter` (title + status only). |

## Requirements

- VS Code **1.85.0** or newer

## Install

### Visual Studio Marketplace

Search for **AutoColorWorkspace**, or open:  
[AutoColorWorkspace on the Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=WyvernSystemsLLC.autocolor-workspace)

### VSIX

1. Build or download `autocolor-workspace-0.2.1.vsix` (or the current version).
2. **Extensions → … → Install from VSIX…**

## Build a VSIX (manual upload)

```bash
npm install
npm run compile
npx vsce package
```

This produces `autocolor-workspace-<version>.vsix` in the project root. Upload via [Publisher Management](https://marketplace.visualstudio.com/manage) if you publish outside the CLI.

## Artwork

Store and marketplace icon live under `images/`. Original artwork for this extension is included in the repo under the same **MIT** license as the code.

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

- Source: [wyvernsystems/auto-color-workspace-vscode-extension](https://github.com/wyvernsystems/auto-color-workspace-vscode-extension)

### Publish (CLI)

```bash
npx vsce login <publisher-id>
npx vsce publish
# or: npx vsce publish patch
```

Ensure `publisher` in `package.json` matches your Marketplace publisher ID.
