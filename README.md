# AutoColorWorkspace

AutoColorWorkspace gives each project a distinct, readable VS Code chrome color so you can tell workspaces apart at a glance.

It works in both **VS Code** and **Cursor**.

## What it does

- Picks a deterministic pastel color from your workspace folder path
- Applies colors to the title bar, activity bar, and status bar
- Writes to your workspace settings (`.vscode/settings.json`) so colors persist across restarts
- Merges safely with your existing `workbench.colorCustomizations`

## Install

### Marketplace

Search for **AutoColorWorkspace** in Extensions, or use:
[AutoColorWorkspace on the Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=WyvernSystemsLLC.autocolor-workspace)

### From a VSIX file

1. Download or build a `.vsix` file (for example `autocolor-workspace-0.1.0.vsix`)
2. In VS Code: **Extensions → ... → Install from VSIX...**

## Requirements

- VS Code **1.85.0** or newer

## Usage

- Runs automatically on startup and when workspace folders change
- In multi-root workspaces, color is based on the first workspace root
- Use Command Palette (**Cmd+Shift+P** / **Ctrl+Shift+P**) for manual controls

## Commands

| Command | Effect |
|--------|--------|
| **AutoColorWorkspace: Enable (all windows)** | Turns on global coloring and applies in the current workspace. |
| **AutoColorWorkspace: Disable (all windows)** | Turns off global coloring and clears this extension's color keys here. |
| **AutoColorWorkspace: Enable for this workspace** | Re-enables coloring in this workspace if global is on. |
| **AutoColorWorkspace: Disable for this workspace** | Disables coloring only for this workspace. |
| **AutoColorWorkspace: Reset colors (this workspace)** | Removes only this extension's color keys from this workspace. |

## Settings

| ID | Scope | Default | Meaning |
|----|--------|---------|---------|
| `autocolor-workspace.enabled` | Application | `true` | Global on/off switch. |
| `autocolor-workspace.workspaceDisabled` | Window | `false` | Disable only this workspace. |

## Build a VSIX for manual upload

If you want to upload manually (instead of `vsce publish`), build a package first:

```bash
npm install
npm run compile
npx vsce package
```

This generates `autocolor-workspace-<version>.vsix` in the project root.

Then upload it in the Marketplace portal:

1. Open [Visual Studio Marketplace Publisher Management](https://marketplace.visualstudio.com/manage)
2. Select your publisher
3. Choose **New extension**
4. Upload the generated `.vsix` file

## Changelog

See [CHANGELOG.md](CHANGELOG.md).

## License

[MIT](LICENSE)

## For Developers

### Local development

```bash
npm install
npm run compile
```

Press **F5** in this repo to launch an Extension Development Host.

### Repository and git notes

- Source repo: [wyvernsystems/auto-color-workspace-vscode-extension](https://github.com/wyvernsystems/auto-color-workspace-vscode-extension)
- If this machine is configured with a dedicated Wyvern Systems SSH key, pushes from this repo can be tied to that account.

### Marketplace publishing (CLI path)

1. Ensure `publisher` in `package.json` matches your Marketplace publisher ID
2. Create an Azure DevOps PAT with **Marketplace (Manage)** scope
3. Log in and publish:

```bash
npx vsce login <publisher-id>
npx vsce publish
```

For a patch release, you can run:

```bash
npx vsce publish patch
```
