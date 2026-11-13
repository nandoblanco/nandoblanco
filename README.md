# Fernando Blanco

I've been vibe coding since the 90s, its just faster now.

I wrote my first code in notepad by dissecting AngelFire free pages - I now have 20+ years of professional experience and still love what I do.

My primary focus right now is custom CMS implementations and automating anything I find too tedious to do manually.

I also recently switched from VSCode Copilot to OpenCode CLI and it's been amazing... hence the plugins I'm releasing below.

## OpenCode plugins

All three plugins now support **OpenCode Desktop and the TUI**, with persistent Desktop side panels and terminal popups. Browsing, searching, and managing local data do not make LLM calls. Memory downloads its embedding model on first use, then runs inference locally on your CPU.

| Plugin                                        | What it does                                                                                                                                                                                                                                                                                           |
| :-------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **[opencode-local-memory][local-memory]**     | **Persistent memory with a Desktop and TUI Manager** (`/memory`). Stores facts and session checkpoints as local Markdown, automatically recalls relevant facts before each turn, and searches with local `all-MiniLM-L6-v2` CPU embeddings. Add, edit, delete, pin core memories, import sessions, and filter results from the Manager. Desktop: `Ctrl+Shift+M` opens or focuses the panel; `Ctrl+Alt+M` toggles it. |
| **[opencode-local-search][local-search]**     | **Replaces OpenCode Desktop's built-in session search**, including its titlebar, vertical-tabs, Home, and Search sessions dialog entry points. Searches local conversation titles, messages, tool calls, shell output, and file paths with multi-term AND ranking, `"exact phrase"`, `/regex/i`, `~fuzzy`, typo fallback, and inline filters. Results include previews and navigation to matched messages. Also adds `/search` in the TUI while preserving `/sessions`. Desktop: `Ctrl+Shift+F` opens or focuses the panel; `Ctrl+Alt+F` toggles it. |
| **[opencode-local-backup][local-backup]**     | **Automatic pre-edit file backups with a Desktop and TUI Manager** (`/backups`, `/restore`). Captures files through `execute.before` for `edit`, `write`, `patch`, `apply_patch`, and `multiedit`, resolves `<project-root>/.backups/`, and supports workspace discovery and configurable retention (`0` = never). Browse snapshots, filter results, preview unified diffs, and restore validated snapshots with an automatic pre-restore safety backup. Includes `backup_list` and `backup_restore` agent tools. Desktop: `Ctrl+Shift+B` opens or focuses the panel; `Ctrl+Alt+B` toggles it. |

Install with one command:

```sh
npx @nandoblanco/opencode-local-memory install
npx @nandoblanco/opencode-local-backup install
npx @nandoblanco/opencode-local-search install
```

Or add all three packages to `~/.config/opencode/opencode.jsonc`. A single entry per package loads its server, TUI, and Desktop support:

```json
{
	"$schema": "https://opencode.ai/config.json",
	"plugins": [
		"@nandoblanco/opencode-local-memory",
		"@nandoblanco/opencode-local-search",
		"@nandoblanco/opencode-local-backup"
	]
}
```

Desktop Managers stay open as side panels during a session and use a dialog when no session is active. The same configuration enables automatic memory recall, compaction checkpoints, pre-edit snapshots, and agent tools. No separate `cli.json` plugin entries are needed for this setup.

## VS Code extensions

Published on the [VS Code Marketplace][vscode-marketplace] and open-sourced on GitHub.

| Extension                                                                     | What it does                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| :---------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **[Localhost Opener][localhost-opener]** ([Marketplace][localhost-opener-mp]) | **Local web server URL mapper and live-reloading split preview** for MAMP, XAMPP, WampServer, Laragon, and Apache/Nginx. Maps files to `http://localhost/...` URLs via longest-prefix document root matching (`localhostOpener.addRoot` native folder picker), launches them in your browser with one click from the Activity Bar (`Ctrl+Alt+O`), and opens VS Code's Integrated Browser in a side split (`Ctrl+Alt+L`) that automatically hard-reloads past the HTTP cache whenever you save any mapped `.html`, `.css`, `.js`, or `.php` file. |
| **[Wrike Tasks][wrike-tasks]** ([Marketplace][wrike-tasks-mp])                | **Wrike REST API v4 task manager** that brings your assigned queue directly into VS Code. Features a split Activity Bar (`Recent & Starred (20)` and `Clients` with ancestor folder resolution across `parentIds` and `superParentIds`), task and client starring, stem- and typo-tolerant fuzzy search, custom workflow status updates, a comment composer with `@mention` autocomplete, manual time logging and a live Status Bar stopwatch timer (`POST /tasks/{id}/timelogs`), one-click `Copy in Markdown` export (metadata, logged time, description, and comment thread), and OAuth 2.0 (Google/SSO) + Permanent Token auth stored in the OS keychain. |

Install from the Marketplace or with one command:

```sh
code --install-extension nandoBlanco.localhost-opener
code --install-extension nandoBlanco.wrike-tasks
```

## Stack

- **Languages & runtimes:** JavaScript, TypeScript, Bun, Node.js, PHP, Python, PowerShell, SQL
- **CMS & web:** Velocity/VTL, REST Web Services API, accessible HTML/CSS (WCAG AA/AAA), Playwright
- **Agent tooling:** OpenCode V2 server, TUI, and Desktop plugins (`@opentui/core`, `@opentui/solid`, `@opencode/plugin`), local ONNX embeddings, custom agent skills

[vscode-marketplace]: https://marketplace.visualstudio.com/publishers/nandoBlanco
[localhost-opener]: https://github.com/nandoblanco/vscode-localhost-opener
[localhost-opener-mp]: https://marketplace.visualstudio.com/items?itemName=nandoBlanco.localhost-opener
[wrike-tasks]: https://github.com/nandoblanco/vscode-wrike-tasks
[wrike-tasks-mp]: https://marketplace.visualstudio.com/items?itemName=nandoBlanco.wrike-tasks

[local-memory]: https://github.com/nandoblanco/opencode-local-memory
[local-search]: https://github.com/nandoblanco/opencode-local-search
[local-backup]: https://github.com/nandoblanco/opencode-local-backup
