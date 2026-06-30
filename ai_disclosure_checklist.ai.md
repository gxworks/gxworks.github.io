<!--
ai-disclosure: ai-generated
ai-model: big-pickle
ai-tool: opencode
ai-reviewer: Roland Horsch
ai-review-date: 2026-06-24
ai-prompt-summary: AI disclosure conventions checklist derived from repo practice
-->

            AI disclosure: ai-generated — see source comments for details

# AI disclosure checklist

Use this when adding or reviewing a file in this repo.

## Every file

- [ ] If the file has no AI involvement at all, verify nothing needs to change
      (the repo default is `none`).
- [ ] If the file has AI involvement, `ai-disclosure` level is set explicitly
      (never inherited from repo default)

## Fully AI-generated files

Files whose entire content came from an AI model.

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

- [ ] Multi-session files: each session has `ai-session-date` + `ai-prompt-summary`
      pair; `ai-review-date` appears once above all sessions
- [ ] Model and provider/tool match the current repo defaults (e.g. `big-pickle`, `opencode`),
      or are overridden per session

## AI-assisted files

Files where some sections were written or edited by an AI, but not the entire file.

- [ ] No `_AI` / `.ai` suffix (reserved for fully AI-generated)
- [ ] Header at top of file with full metadata fields
- [ ] `ai-reviewer: (see Git history)` in header (not compulsory — a named person is still valid)
- [ ] `ai-review-date: YYYY-MM-DD (last review for this file)` in header
- [ ] Local annotation near each changed section uses `ai-session-date` +
      `ai-prompt-summary` pair (no reviewer/date at local level)

      | Language | Mechanism |
      |---|---|
      | Java (`.java`) | `// ai-session-date:` / `// ai-prompt-summary:` inline comments |
      | Shell (`.sh`) | `# ai-session-date:` / `# ai-prompt-summary:` inline comments |
      | HTML (`.html`) | `<!-- ai-session-date: -->` / `<!-- ai-prompt-summary: -->` comments + visible hint near header |
      | Markdown (`.md`) | `<!-- ai-session-date: -->` / `<!-- ai-prompt-summary: -->` comments + visible hint near header |
      | Other | Key-value comments matching the language's comment syntax |

- [ ] **Visible hint** (HTML/MD only): small unobtrusive line near the page title
      stating the disclosure level and directing to source comments

## Repo default

- [ ] `AI_DISCLOSURE.md` lists `disclosure-default: none`
- [ ] An exception is noted: `AGENTS.md` (carries no suffix or header, as required by
      the tooling)
