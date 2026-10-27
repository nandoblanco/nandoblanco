# Fernando Blanco

I've been vibe coding since the 90s, its just faster now.

I wrote my first code in notepad by dissecting AngelFire free pages - I now have 20+ years of professional experience and still love what I do.

My primary focus right now is custom CMS implementations and automating anything I find too tedious to do manually.

I also recently switched from VSCode Copilot to OpenCode CLI and it's been amazing... hence the plugins I'm releasing below.

## OpenCode plugins

These plugins run on your machine with no external services. Their TUI popups read local files and SQLite directly inside the terminal, so browsing and searching cost zero tokens.

| Plugin                                        | What it does                                                                                                                                                                                                                                                                                           |
| :-------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **[opencode-local-memory][local-memory]**     | **Local-first, automatic persistent memory** (`topics/*.md`, `sessions/*.md`) paired with local `all-MiniLM-L6-v2` CPU embeddings (`vectors.json`). Auto-bootstraps on first run, automatically injects relevant facts before each turn, records decisions and compaction checkpoints as you work, and includes an 80%-wide split-pane `/memory` TUI browser (`Ctrl+M`, plus `/memory-add`) with 0ms lexical + hybrid semantic search, interactive filter pills (`^t` type, `^g` topic, `^r` regex, `^l` resync), and clipboard copy. |
| **[opencode-local-search][local-search]**     | **Local-first, zero-token interactive session search** (`/search`, `Ctrl+F`) that automatically indexes your local `opencode.db` (V2 and V1 schemas) across titles, messages, tool calls, shell output, and file paths. Supports session-level multi-term AND ranking, `"exact phrase"`, `/regex/i`, `~fuzzy` and automatic Levenshtein typo fallback, interactive filter pills (`^p` project/all scope, `^g` role, `^t` date, `^r` mode, `^l` refresh), and `Tab`-selectable snippet cards that jump straight to the exact matched message in the transcript. |
| **[opencode-local-backup][local-backup]**     | **Local-first, automatic pre-edit file backups** (`execute.before` hook on `edit`, `write`, `patch`, `apply_patch`, `multiedit`) with smart `<project-root>/.backups/` resolution, unlimited-depth workspace discovery (`rootDir`), and configurable retention auto-pruning (`0` = never). Includes an 80%-wide split-pane `/backups` TUI browser (`Ctrl+Alt+B`, `/restore`) with filter pills (`^t` tool, `^g` date, `^r` retention, `^d` prune), hunk-filtered unified diff preview, a 3-option `Enter` menu (restore with automatic `pre-restore` safety snapshot, open backup file, or launch `code --diff`), and `backup_list`/`backup_restore` agent tools. |

Install with one command:

```sh
npx @nandoblanco/opencode-local-memory install
npx @nandoblanco/opencode-local-backup install
npx @nandoblanco/opencode-local-search install
```

Or add the TUI plugins to `~/.config/opencode/cli.json` (all three support `"dialogWidth": "80%"`):

```json
{
	"plugins": [
		"@nandoblanco/opencode-local-memory",
		"@nandoblanco/opencode-local-search",
		"@nandoblanco/opencode-local-backup"
	]
}
```

For automatic per-turn memory recall, compaction checkpoints, pre-edit file snapshots, and agent tools (`memory_store`, `memory_search`, `memory_checkpoint`, `backup_list`, `backup_restore`), also add `"@nandoblanco/opencode-local-memory"` and `"@nandoblanco/opencode-local-backup"` to `~/.config/opencode/opencode.jsonc`.

## VS Code extensions

Published on the [VS Code Marketplace][vscode-marketplace] and open-sourced on GitHub.

| Extension                                                                     | What it does                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| :---------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **[Localhost Opener][localhost-opener]** ([Marketplace][localhost-opener-mp]) | **Local web server URL mapper and live-reloading split preview** for MAMP, XAMPP, WampServer, Laragon, and Apache/Nginx. Maps files to `http://localhost/...` URLs via longest-prefix document root matching (`localhostOpener.addRoot` native folder picker), launches them in your browser with one click from the Activity Bar (`Ctrl+Alt+O`), and opens VS Code's Integrated Browser in a side split (`Ctrl+Alt+L`) that automatically hard-reloads past the HTTP cache whenever you save any mapped `.html`, `.css`, `.js`, or `.php` file. |
| **[Wrike Tasks][wrike-tasks]** ([Marketplace][wrike-tasks-mp])                | **Wrike REST API v4 task manager** that brings your assigned queue directly into VS Code. Features a split Activity Bar (`Recent & Starred (20)` and `Clients` with ancestor folder resolution across `parentIds` and `superParentIds`), task and client starring, stem- and typo-tolerant fuzzy search, custom workflow status updates, a comment composer with `@mention` autocomplete, one-click `Copy in Markdown` export (metadata, description, and comment thread), and OAuth 2.0 (Google/SSO) + Permanent Token auth stored in the OS keychain. |

Install from the Marketplace or with one command:

```sh
code --install-extension nandoBlanco.localhost-opener
code --install-extension nandoBlanco.wrike-tasks
```

## Stack

- **Languages & runtimes:** JavaScript, TypeScript, Bun, Node.js, PHP, Python, PowerShell, SQL
- **CMS & web:** Velocity/VTL, REST Web Services API, accessible HTML/CSS (WCAG AA/AAA), Playwright
- **Agent tooling:** OpenCode V2 server and TUI plugins (`@opentui/core`, `@opentui/solid`), local ONNX embeddings, custom agent skills

[vscode-marketplace]: https://marketplace.visualstudio.com/publishers/nandoBlanco
[localhost-opener]: https://github.com/nandoblanco/vscode-localhost-opener
[localhost-opener-mp]: https://marketplace.visualstudio.com/items?itemName=nandoBlanco.localhost-opener
[wrike-tasks]: https://github.com/nandoblanco/vscode-wrike-tasks
[wrike-tasks-mp]: https://marketplace.visualstudio.com/items?itemName=nandoBlanco.wrike-tasks

[local-memory]: https://github.com/nandoblanco/opencode-local-memory
[local-search]: https://github.com/nandoblanco/opencode-local-search
[local-backup]: https://github.com/nandoblanco/opencode-local-backup
