# Security

## Scope

Auto Color only reads workspace folder paths and extension settings, computes colors locally, and updates `workbench.colorCustomizations` via the official VS Code configuration API. It does not open network connections, execute shell commands, or read project source files.

## Workspace Trust

The extension does **not** require you to mark a folder as “trusted” for Auto Color to run. It applies the same way whether VS Code / Cursor opened the repo in Restricted Mode or full trust. (If the editor itself blocks certain workspace writes in restricted scenarios, that is platform behavior outside this extension.)

## Reporting issues

Report suspected vulnerabilities via [GitHub Issues](https://github.com/wyvernsystems/auto-color-vscode-extension/issues). Include editor version, extension version, and steps to reproduce.
