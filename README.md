# Fernando Blanco

I've been vibe coding since the 90s, its just faster now.

I wrote my first code in notepad by disecting AngelFire free pages - I now have 20+ years of professional experience and still love what I do.

My primary focuse right now is custon CMS implementaions and automating anything I find too tedious to do manually.

I also recently switched from VSCode Copilot to OpenCode CLI and it's been amazing... hence the plugins I'm releasing below.

## OpenCode plugins

These plugins run on your machine with no external services. Their TUI popups read local files and SQLite directly inside the terminal, so browsing and searching cost zero tokens.

| Plugin                                        | Commands                       | What it does                                                                                                                                                                                                                                                                                           |
| :-------------------------------------------- | :----------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **[opencode-local-memory][local-memory]**     | `/memory`<br>`/memory-add`     | Persistent Markdown memory (`topics/*.md`, `sessions/*.md`) paired with local `all-MiniLM-L6-v2` embeddings (`vectors.json`). Injects relevant facts before each turn, records decisions and preferences as you work, writes session checkpoints on compaction, and includes a split-pane TUI browser. |
| **[opencode-session-search][session-search]** | `/search`<br>`/session-search` | Zero-dependency TUI popup that indexes your local `opencode.db` (V2 and V1 schemas). Supports multi-term AND queries, regex, bounded Levenshtein typo tolerance, and inline filters (`role:`, `date:`, `file:`, `tool:`), then jumps straight to the matched message in the transcript.                |

Add both TUI plugins to `~/.config/opencode/cli.json`:

```json
{
	"plugins": ["opencode-local-memory", "opencode-session-search"]
}
```

For automatic per-turn memory recall, compaction checkpoints, and agent tools (`memory_store`, `memory_search`, `memory_checkpoint`), also add `"opencode-local-memory"` to `~/.config/opencode/opencode.jsonc`.

## Stack

- **Languages & runtimes:** JavaScript, TypeScript, Bun, Node.js, PHP, Python, PowerShell, SQL
- **CMS & web:** Velocity/VTL, REST Web Services API, accessible HTML/CSS (WCAG AA/AAA), Playwright
- **Agent tooling:** OpenCode V2 server and TUI plugins (`@opentui/core`, `@opentui/solid`), local ONNX embeddings, custom agent skills

[local-memory]: https://github.com/nandoblanco/opencode-local-memory
[session-search]: https://github.com/nandoblanco/opencode-session-search
