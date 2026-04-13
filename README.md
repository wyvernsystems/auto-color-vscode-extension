# Auto Color

### Visual Studio Code example

![Visual Studio Code example — Auto Color, teal tint](images/readme-hero-vscode.png)

### Cursor example

![Cursor example — Auto Color, purple tint](images/readme-hero-cursor.png)

**Privacy:** Generic workspace name, no secrets in the tree, terminal prompts partially redacted.

## What it does

Auto Color picks a **color theme per workspace** and applies it to the window: pastel **title, activity, and status** bars and a matching **tint** on the editor, sidebar, tabs, terminal, and related UI. Your syntax theme still controls most text; this mainly changes **backgrounds** so each project looks distinct.

**What counts as a “workspace” here:** whatever VS Code or Cursor treats as the current workspace—almost always **a folder you opened** (**File → Open Folder**). That one folder (and its `.vscode/settings.json`) gets one palette. If you open **another window** with a **different** folder, that’s a **different** workspace and can have a **different** color. A **multi-root workspace** (a `.code-workspace` file with several folders) is still **one** workspace for this extension: colors and settings are stored with that workspace, and the **first** folder in the list is what the default tint is derived from (unless you use **Randomize**).

## Why it’s useful (VS Code and Cursor)

**VS Code:** With several windows open, you can see **which folder** you’re in from the bar color and overall cast instead of reading the title.

**Cursor:** Same idea when you run **multiple Cursor windows** (different repos, or one “agent” window and one “editing” window). The tint makes it harder to paste, run terminal commands, or continue the wrong chat in the wrong project.

## File it writes

The extension saves colors through **workspace settings**. That usually creates or updates:

**`.vscode/settings.json`**

Inside that file it adds a **`workbench.colorCustomizations`** object with the hex colors for this workspace. Anything else in that file is left alone. If you disable Auto Color for the workspace or turn it off globally, it **removes only the keys it added** (and a few legacy keys), not your whole settings file.

## Security

- **No network** — colors are computed locally; nothing is sent to a server.
- **No trust prompt required** — Auto Color runs without asking you to “trust” the workspace first.
- **Reporting** — see [SECURITY.md](SECURITY.md).

## Commands

Open the Command Palette (**Cmd+Shift+P** on Mac, **Ctrl+Shift+P** on Windows/Linux):

| Command | What it does |
|--------|----------------|
| **Auto Color: Enable (all windows)** | Turns the extension on everywhere. Applies colors in the current workspace if you have a folder open. |
| **Auto Color: Disable (all windows)** | Turns it off for all windows and clears this extension’s color keys from the current workspace’s `workbench.colorCustomizations`. |
| **Auto Color: Enable for this workspace** | Turns coloring back on for **this** workspace only (still requires the global switch to be on). |
| **Auto Color: Disable for this workspace** | Stops coloring **this** workspace and clears this extension’s keys here. |
| **Auto Color: Set color scope** | **All bars**: title + activity + status plus the workbench tint. **Head and footer only**: title + status only; activity bar, editor, sidebar, tabs, panel, and other tinted areas go back to your theme defaults. |
| **Auto Color: Randomize color** | Picks a new random palette and saves it in workspace settings so it stays after reload. |
| **Auto Color: Reset to default color** | Removes the random override so the color is derived from the workspace folder path again. |

## Settings UI

Open **Settings** (**Cmd+,** / **Ctrl+,**), search **Auto Color**, or browse **Extensions → Auto Color**. You get the same options as the commands: **global on/off**, **color scope** (dropdown with short descriptions), **disable for this workspace**, and **random seed**. Use the **Workspace** tab when you want scope or per-workspace options for the current folder only.

## Install

Requires **VS Code 1.85+** (Cursor is compatible). Search the Marketplace for **Auto Color** or install from a `.vsix`.

Marketplace icon: color wheel from [UXWing](https://uxwing.com/color-wheel-icon/) ([license](https://uxwing.com/license/)), resized to 128×128. Readme screenshots: `images/readme-hero-vscode.png` (Visual Studio Code example, teal) and `images/readme-hero-cursor.png` (Cursor example, purple).

Repository: [wyvernsystems/auto-color-vscode-extension](https://github.com/wyvernsystems/auto-color-vscode-extension) · [MIT](LICENSE) · [Security](SECURITY.md)
