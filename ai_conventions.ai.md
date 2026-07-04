<!--
ai-disclosure: ai-generated
ai-model: big-pickle
ai-tool: opencode
ai-reviewer: Roland Horsch
ai-review-date: 2026-07-01 (last review for this file)
ai-prompt-summary: comprehensive summary of AI disclosure conventions derived from repo practice
-->

            AI disclosure: ai-generated — see source comments for details

# AI Disclosure Conventions

## Repo default

`AI_DISCLOSURE.md` declares `disclosure-default: none` — files without
a disclosure header are presumed human-authored.

## When disclosure is required

Any file with AI involvement (fully generated or assisted) must carry
an explicit `ai-disclosure` value. This is never inherited from the
repo default.

## File suffixes

| Suffix | Meaning |
|---|---|
| `_AI` or `.ai` | Fully AI-generated |
| (no suffix) | AI-assisted or fully human |

Exception: `AGENTS.md` carries no suffix and no disclosure header.

## AI involvement levels

`none` · `ai-assisted` · `ai-generated` · `autonomous`

## Metadata keys

All use `key: value` in the host language's comment syntax.

| Key | Required |
|---|---|
| `ai-disclosure` | Always (never inherited) |
| `ai-model` | Recommended (default: `big-pickle`) |
| `ai-tool` | Recommended (default: `opencode`) |
| `ai-provider` | If applicable |
| `ai-reviewer` | Yes, in file headers |
| `ai-review-date` | Yes, in file headers (with `(last review for this file)` suffix) |
| `ai-session-date` | Per session, before its summary |
| `ai-prompt-summary` | Per session |

## Session tracking

Each AI session that contributed to a source file is recorded within
the file. At minimum each session has `ai-prompt-summary`;
`ai-session-date` may be omitted for single-session files.
Extra keys (e.g. `ai-model` when a different tool was used) can appear
between `ai-session-date` and `ai-prompt-summary`.

### Header vs local

- Sessions that affect the **file as a whole** go in the header block.
- Sessions that only affect **specific sections** are annotated as local
  comments near the changed lines, using the same key pair.
- `ai-reviewer` and `ai-review-date` appear mainly in the file header,
  usually not in local annotations.

### Examples

Multi-session header:

```
ai-disclosure: ai-generated
ai-model: big-pickle
ai-tool: opencode
ai-reviewer: (see Git history)
ai-review-date: 2026-06-23 (last review for this file)
ai-session-date: 2026-05-07
ai-prompt-summary: initial content
ai-session-date: 2026-06-23
ai-prompt-summary: updated section X
```

Single-session header (date omitted):

```
ai-disclosure: ai-generated
ai-model: big-pickle
ai-tool: opencode
ai-reviewer: Roland Horsch
ai-review-date: 2026-05-29 (last review for this file)
ai-prompt-summary: tab-spaced print() utility
```

## Visible hint (HTML / Markdown)

A small line near the page header states the AI involvement level and directs
readers to the source comments:

```html
<sup>AI disclosure: LEVEL &mdash; see source comments for details</sup>
```

## Per-language mechanisms

See `src/main/webapp/ai_disclosure_examples.ai.html` for complete examples.

| Language | Mechanism |
|---|---|
| Java | `// ai-disclosure:` comment block at top of file |
| HTML | visible hint near header + `<html ai-disclosure="...">` + `<meta name="ai-disclosure">` + HTML comments for other keys |
| Markdown | HTML comment block using the same key-value format |
| Shell | `#` comment lines |
| Other | Key-value comments matching the language's comment syntax |

## AI-assisted local annotations

Near each changed section, using the same key pair as the header:

```
// ai-session-date: 2026-06-26
// ai-prompt-summary: specific change description
```

Date may be omitted for single-session local edits.

## Related files

- [`AI_DISCLOSURE.md`](AI_DISCLOSURE.md) — repo-level default
- [`src/main/webapp/ai_disclosure_examples.ai.html`](ai_disclosure_examples.ai.html) — examples per language
- [`src/main/webapp/ai_disclosure_details.ai.html`](ai_disclosure_details.ai.html) — rationale and conventions discussion
- [`src/main/webapp/ai_disclosure_checklist.ai.md`](ai_disclosure_checklist.ai.md) — operational checklist
