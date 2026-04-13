# Changelog

All notable changes to **Auto Color** will be documented in this file.

## [1.0.2] - 2026-04-13

### Changed

- **Workspace Trust:** Removed `untrustedWorkspaces` manifest restrictions and all trust checks so Auto Color works immediately without requiring the user to trust the workspace (easier default experience). Other hardening (e.g. `crypto` random seed, path length cap, seed validation, `.vscodeignore` patterns) remains.

[1.0.2]: https://github.com/wyvernsystems/auto-color-vscode-extension/releases/tag/v1.0.2

## [1.0.1] - 2026-04-13

### Security

- **Workspace Trust:** `capabilities.untrustedWorkspaces` set to **limited**; workspace-level `auto-color.workspaceDisabled`, `scope`, and `randomSeed` are restricted until the workspace is trusted. No writes to `workbench.colorCustomizations` while untrusted; reapplies after trust is granted.
- **Commands** that mutate workspace settings require a trusted workspace (with user-visible warning otherwise). **Disable (all windows)** warns if workspace keys could not be cleared while untrusted.
- **Random seed:** `randomSeed` validated as finite; **Randomize** uses `crypto.randomBytes` instead of `Math.random`.
- **Path hash:** folder path length capped before hashing to limit CPU work on abnormal paths.
- **Packaging:** `.vscodeignore` excludes common secret filename patterns from the VSIX.
- **Repo:** [SECURITY.md](SECURITY.md), Dependabot for npm, README security summary.

[1.0.1]: https://github.com/wyvernsystems/auto-color-vscode-extension/releases/tag/v1.0.1

## [1.0.0] - 2026-04-13

### Added

- **New Marketplace extension** `WyvernSystemsLLC.auto-color` (package name `auto-color`, display name **Auto Color**).
- Commands and settings use the `auto-color.*` prefix (replaces `autocolor-workspace.*`).

### Notes

- Successor to **AutoColorWorkspace** (`WyvernSystemsLLC.autocolor-workspace`). Migrate by installing **Auto Color**, uninstalling the old extension, and updating User/Workspace JSON: `autocolor-workspace.*` → `auto-color.*` if you had overrides.

[1.0.0]: https://github.com/wyvernsystems/auto-color-vscode-extension/releases/tag/v1.0.0

---

Earlier releases shipped as **AutoColorWorkspace**; history below retains original setting/command names for reference.

## [0.2.1] - 2026-04-13

### Added

- Marketplace **icon** (`images/icon.png`) and README **hero** image (`images/readme-hero.png`)

### Changed

- **README** expanded for Marketplace / repo details (features, tables, artwork note)
- **galleryBanner** tint updated to complement the new artwork

[0.2.1]: https://github.com/wyvernsystems/auto-color-vscode-extension/releases/tag/v0.2.1

## [0.2.0] - 2026-04-13

### Added

- Per-bar **shades** of the same workspace hue (title / activity / status lightness steps)
- Setting `autocolor-workspace.scope`: `all` (default) or `headFooter` (title + status only)
- Command **AutoColorWorkspace: Set color scope** (Quick Pick)

### Removed

- **Reset colors (this workspace)** command (use **Disable for this workspace** or clear keys in settings if needed)

[0.2.0]: https://github.com/wyvernsystems/auto-color-vscode-extension/releases/tag/v0.2.0

## [0.1.0] - 2026-04-11

### Added

- Automatic workspace chrome colors (title bar, activity bar, status bar) from folder-path hash
- Golden-ratio–based pastel palette (golden-angle hue, φ-weighted saturation/lightness)
- Persistence via `workbench.colorCustomizations` in workspace `.vscode/settings.json`
- Commands: global enable/disable, per-workspace enable/disable, reset colors for this workspace
- Settings: `autocolor-workspace.enabled`, `autocolor-workspace.workspaceDisabled`

[0.1.0]: https://github.com/wyvernsystems/auto-color-vscode-extension/releases/tag/v0.1.0
