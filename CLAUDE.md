# CLAUDE.md — {{Your Name}}'s Second Brain

> Entry point. Keep this file lean: identity + rules + glossary + folder map.
> Anything data-like (team roster, concepts, projects) lives in `wiki/`.

---

## 👤 About Me

- **{{Your Full Name}}** — {{Your Role}} at **Agicap** (Lyon fintech, treasury SaaS)
- Based in {{City}}, {{native language}} / {{fluent languages}}
- Scope: **{{Product Lines you own — e.g., AP · AR · PAY}}**
- Manager: **{{Manager Name}}** ({{Their Role}})
- Style: {{adjust — e.g., concise, evidence-driven, pragmatic}}

> Full team roster, Slack IDs, and PM scope → [`wiki/entities/Product_Team.md`](wiki/entities/Product_Team.md) *(create this page as you onboard people)*

---

## 🗂️ Folder Map

| Folder | Purpose |
|---|---|
| `raw/` | Immutable sources: transcripts, articles, specs, screenshots. **Read, never modify** |
| `wiki/` | 🧠 Compiled knowledge layer. **Start at [`wiki/index.md`](wiki/index.md)** |

**Wiki sub-areas** (all indexed in `wiki/index.md`):
`entities/` · `concepts/` · `patterns/` · `syntheses/` · `mocs/` · `log.md`

*Optional additions (add if relevant to your scope):*
- `Code/` — repos you touch often, with a nested `CLAUDE.md`
- `reporting/` — weekly 1-1s, quarterly objectives
- `Payment/` (or domain folder) — spec-heavy reference material

---

## 📌 Glossary

**Product lines at Agicap**: AP = Accounts Payable · AR = Accounts Receivable · PAY = Payments · TRY = Treasury · DI = Data Integration

**Squads / systems you encounter** (fill in what's relevant to your scope):
- SIM = Supplier Invoice Management
- P2P = Purchase-to-Pay
- PA = "Plateforme Agréée" (French e-invoicing portal)
- *(add your own — acronyms you use daily)*

---

## 🔄 Wiki Workflows (Karpathy pattern)

- **Ingest** a new source → `wiki-ingest` skill (raw → summary → index → related pages → log)
- **Health check** → `wiki-clean` skill (contradictions, orphans, stale, missing pages, duplicates, compounding)

> Every wiki page carries `last_reviewed: YYYY-MM-DD` front-matter. Bump on edit. Full health check via `python3 wiki/wiki_clean.py` (stale, duplicates, contradictions, compounding). Use `--json` for machine-readable output, `--days 90` for custom staleness threshold. Backlinks via `python3 wiki/backlinks.py`.

---

## 🧠 Rules for Claude

1. **Load the right context** before answering — start at `wiki/index.md` for anything knowledge-related
2. **Language**: respond in the language I use. **Wiki content + CLAUDE.md are always in English**. Raw sources stay in original language
3. **Format**: short, direct, actionable. Emojis for clarity
4. **Deliverables**: always propose a concrete output (file, table, plan) — not just analysis
5. ⚠️ **Wiki-first — MANDATORY** for any synthesis, summary, or doc to share:
	1. Read `wiki/index.md`
	2. Read matching pages in `wiki/syntheses/`, `wiki/entities/`, `wiki/concepts/`, `wiki/patterns/`
	3. **Only open `raw/` if the wiki is missing a specific piece of information**
	→ Going directly to `raw/transcripts/` for shareable content is **FORBIDDEN**
