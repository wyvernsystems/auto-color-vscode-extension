# Changelog

All notable changes to **AutoColorWorkspace** will be documented in this file.

## [0.2.1] - 2026-04-13

### Added

- Marketplace **icon** (`images/icon.png`) and README **hero** image (`images/readme-hero.png`)

### Changed

- **README** expanded for Marketplace / repo details (features, tables, artwork note)
- **galleryBanner** tint updated to complement the new artwork

[0.2.1]: https://github.com/wyvernsystems/auto-color-workspace-vscode-extension/releases/tag/v0.2.1

## [0.2.0] - 2026-04-13

### Added

- Per-bar **shades** of the same workspace hue (title / activity / status lightness steps)
- Setting `autocolor-workspace.scope`: `all` (default) or `headFooter` (title + status only)
- Command **AutoColorWorkspace: Set color scope** (Quick Pick)

### Removed

- **Reset colors (this workspace)** command (use **Disable for this workspace** or clear keys in settings if needed)

[0.2.0]: https://github.com/wyvernsystems/auto-color-workspace-vscode-extension/releases/tag/v0.2.0

## [0.1.0] - 2026-04-11

### Added

- Automatic workspace chrome colors (title bar, activity bar, status bar) from folder-path hash
- Golden-ratio–based pastel palette (golden-angle hue, φ-weighted saturation/lightness)
- Persistence via `workbench.colorCustomizations` in workspace `.vscode/settings.json`
- Commands: global enable/disable, per-workspace enable/disable, reset colors for this workspace
- Settings: `autocolor-workspace.enabled`, `autocolor-workspace.workspaceDisabled`

[0.1.0]: https://github.com/wyvernsystems/auto-color-workspace-vscode-extension/releases/tag/v0.1.0
