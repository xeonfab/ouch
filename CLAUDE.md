# CLAUDE.md — Fabien's Second Brain

> Entry point. Keep this file lean: identity + rules + glossary + folder map.
> Anything data-like (team roster, concepts, projects) lives in `wiki/`.

---

## 👤 About Me

- **Fabien Riou** — building **Ouch! / FixMyLife** as an independent project (~20h/week available, alongside other professional commitments)
- Style: concise, evidence-driven, pragmatic

> Team roster / collaborators (if any) → `wiki/entities/`

---

## 🗂️ Folder Map

| Folder | Purpose |
|---|---|
| `raw/` | Immutable sources: transcripts, articles, specs, screenshots. **Read, never modify** |
| `wiki/` | 🧠 Compiled knowledge layer. **Start at [`wiki/index.md`](wiki/index.md)** |

**Wiki sub-areas** (all indexed in `wiki/index.md`):
`entities/` · `concepts/` · `patterns/` · `syntheses/` · `mocs/` · `log.md`

This wiki is scoped entirely to **Ouch! / FixMyLife** (side project, `fix-it-karma` on Lovable, public name "Ouch!"/"FixMyLife"): product, growth, legal/moderation, data model. See [`MOC_Ouch_FixMyLife`](wiki/mocs/MOC_Ouch_FixMyLife.md).

---

## 📌 Glossary

**Ouch! / FixMyLife**:
- **Score de Douleur** = pain score ranking problems for makers (45% positive-vote volume, 35% conversion rate, 20% opt-in emails)
- **Terminal Maker** = the maker-facing dashboard, ranks problems by Score de Douleur
- **Type A / Type B** (`resolutionType`) = "tiers" (a third-party maker can fix it without the named entity) vs "entite" (only the named entity can fix it) — drives which disclaimer is shown
- **Entité** = an organisation only, never a physical person (hard rule — see `wiki/concepts/` once created)
- **Cercle 1/2/3** = launch-targeting rings: freelances/creators (current) → PME (signal-gated) → grand public

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
6. **Ouch! / FixMyLife hard rules** (see [`MOC_Ouch_FixMyLife`](wiki/mocs/MOC_Ouch_FixMyLife.md) for full detail) — never violate these when producing content, code, or copy for this project:
	- An *entité* is always an organisation, never a named physical person
	- No divisive public-policy takes; civic/administrative friction only, factual and specific
	- Cards state a lived fact, never a value judgment on the entity ("j'attends mon remboursement depuis 3 semaines", not "cette entreprise est malhonnête")
	- No content deletion ever (legal obligation aside); emails alone follow GDPR retention/erasure
	- No reply threads — maker updates and "voix des concernés" are one-way
	- No special account status or active outreach for entities that appear on cards
	- Tone: always fun/playful on the victim-facing side, even for civic/institutional topics; factual/dark register stays confined to the Terminal Maker
