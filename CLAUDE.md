# CLAUDE.md: Generative Syntax Workbench (GSW)

Offline web app (TypeScript, React, SVG, Vite) that analyses Arabic, English and French sentences in the generative frameworks (SS57, ST65, EST, GB, PP, MP stages, Cartography), outputs labelled bracketings and builds animated trees step by step. Owner and linguistic authority: Rachid Bouziane.

## Read before working

- `docs/SPEC.md`: the specification. Sections marked [FIXED] are owner decisions.
- `docs/PHASES.md`: phases, acceptance criteria, parallel tracks. Work one phase at a time.
- `knowledge/reference/GSW_Knowledge_Reference.md`: the linguistic reference (read chapters as needed, not all at once).
- `knowledge/notation/GSW_bracket_notation.md`: the bracket grammar.

## Commands

- Validate knowledge: `python tools/validate_knowledge.py` (needs `pip install jsonschema`)
- Rebuild the reference after editing JSON or prose: `python tools/build_reference.py`
- Full check (after Phase 0): `npm run verify`

## Rules that matter most

- IMPORTANT: Never hard-code linguistic inventories, labels or Arabic terms in code. Read them from `knowledge/data/*.json`. To add one, edit the JSON and its schema, then run the validator.
- Never change a gold example or an analysis to make a test pass. Flag it and ask the owner.
- Show uncertainty: `status`, `alternatives`, `verification`, `ar_status: proposed` must be visible in the UI.
- No en dash or em dash anywhere (UI strings, exports, docs, commit messages). Use a hyphen, comma or semicolon.
- Colours: maroon and green tokens only (`knowledge/data/visual_tokens.json`); no blue anywhere, including focus rings and library defaults.
- Arabic UI first; Arabic trees drawn right to left (first spoken word at far right); bracket strings stored in logical order without direction marks; never split an Arabic word across SVG tspans; bundle the Amiri font.
- Arabic terms per course decision ق41: Merge = النظم (الخارجي، الداخلي، المجموعي، الزوجي); Projection = الإسقاط; Sisterhood = علاقة التآخي; al-Jurjani = نظرية النظم.
- Exports carry no names of tools or platforms and no embedded metadata.
- Start each phase in plan mode. Ask questions with your recommended answer for each. End each phase with `npm run verify` output, screenshots and a short report.
- Commit after each coherent unit. Keep `docs/DECISIONS.md` and `docs/CHANGELOG.md` current.
- When compacting, always preserve: the current phase, the list of modified files, failing tests, and open questions for the owner.
