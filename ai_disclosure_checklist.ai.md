<!--
ai-disclosure: ai-generated
ai-model: big-pickle
ai-tool: opencode
ai-reviewer: Roland Horsch
ai-review-date: 2026-06-24 (last review for this file)
ai-prompt-summary: AI disclosure conventions checklist derived from repo practice
-->

            AI disclosure: ai-generated — see source comments for details

# AI disclosure checklist

Use this when adding or reviewing a file in this repo.

## Every file

- [ ] Files with no authorial AI involvement do not have the disclosure header - in
      this repository (the repo default is `none`). If the file is contributed
      and known to have AI involvement without stating that, the header should
      be added.
- [ ] If the file has AI involvement, `ai-disclosure` value is set explicitly
      (never inherited from repo default)
- [ ] Session tracking: each session block has at least `ai-prompt-summary`; `ai-session-date`
      precedes the summary and may be omitted for single-session files. For multiple
      sessions extra keys between the date and the summary may be added (e.g.
      different AI tool). At least the header should have `ai-review-date`, noting
      the latest review of the file.

## Fully AI-generated files

Files whose entire content came from an AI model (apart from reviewing edits).

- [ ] File name ends with `_AI` or `.ai`
- [ ] Header includes each of: `ai-disclosure`, `ai-model`,
      `ai-reviewer`, `ai-review-date`, `ai-prompt-summary`
- [ ] Convention-specific mechanism present:

      | Language | Required mechanism |
      |---|---|
      | Java (`.java`) | `// ai-disclosure:` comment block at top |
      | HTML (`.html`) | `<html ai-disclosure="..." ai-model="..." ...>` +
        `<meta name="ai-disclosure" content="...">`<br>HTML comments for `ai-reviewer`,
        `ai-review-date`, `ai-session-date`, `ai-prompt-summary` |
      | Markdown (`.md`) | HTML comment block at top using the same key-value format |
      | Other | Key-value comments matching the language's comment syntax |

- [ ] Model and provider/tool match the current repo defaults (e.g. `big-pickle`, `opencode`),
      or are overridden per session.

## AI-assisted files (authorial AI involvement)

Files where some sections were authored by an AI, but not the entire file.

- [ ] No `_AI` / `.ai` suffix (reserved for fully AI-generated)
- [ ] Header at top of file with full metadata fields
- [ ] `ai-reviewer: (see Git history)` in header (not compulsory — a named person is still valid)
- [ ] `ai-review-date: YYYY-MM-DD (last review for this file)` in header (parenthetical applies to file-level headers only)
- [ ] Local annotation near each changed section uses at least `ai-session-date` + `ai-prompt-summary`

      | Language | Mechanism |
      |---|---|
      | Java (`.java`) | `// ai-session-date:` / `// ai-prompt-summary:` inline comments |
      | Shell (`.sh`) | `# ai-session-date:` / `# ai-prompt-summary:` inline comments |
      | HTML (`.html`) | `<!-- ai-session-date: -->` / `<!-- ai-prompt-summary: -->` comments + visible hint near header |
      | Markdown (`.md`) | `<!-- ai-session-date: -->` / `<!-- ai-prompt-summary: -->` comments + visible hint near header |
      | Other | Key-value comments matching the language's comment syntax |

- [ ] **Visible hint** (HTML/MD only): small unobtrusive line near the page title
      stating the AI involvement level and directing to source comments

## Repo default

- [ ] `AI_DISCLOSURE.md` lists `disclosure-default: none`
- [ ] Obvious exceptions (as required by the build tools etc.), e.g.: `AGENTS.md` (carries no suffix or header).
