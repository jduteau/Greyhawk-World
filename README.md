# Greyhawk World Wiki

A structured campaign knowledge base for running AD&D adventures set in the **World of Greyhawk (576 CY)**. Built on the [llm-wiki](https://github.com/anthropics/llm-wiki) framework, this wiki serves two consumers simultaneously: the GM browsing notes in Obsidian, and an AI world arbiter agent querying during live play.

## What's in here

The wiki covers classic modules placed in the Greyhawk setting:

- **B2 — The Keep on the Borderlands** — frontier Keep, Caves of Chaos, the Temple of Evil Chaos spy network
- **T1 — The Village of Hommlet** — Hommlet, the Welcome Wench Inn, and the Temple of Elemental Evil conspiracy

Content is organized into namespaces:

| Namespace | Contents |
|-----------|----------|
| `Locations` | Named places: villages, dungeons, buildings, regions |
| `NPCs` | Named characters the party has met or heard of |
| `Factions` | Organizations, cults, military units, conspiracies |
| `Sessions` | Individual play session records (append-only) |
| `Conspiracy` | Synthesized analysis of conspiracy threads |
| `Modules` | Module metadata and campaign placement notes |
| `World` | Greyhawk canon: geography, politics, deities |
| `Lore` | In-world documents, rumors, legends, inscriptions |
| `State` | Current session state block (overwritten each session) |

## How it works

Each page carries structured YAML frontmatter that encodes entity type, confidence level, GM-only visibility flags, and cross-references. The `Wiki/State/Current-Session.md` page is the AI arbiter's entry point at session start — it holds current party status, active location, and open conspiracy threads. Everything else is queried on demand.

Confidence levels track how solid each fact is:

- `canon` — directly from published source material
- `established` — confirmed in play and recorded in a session page
- `inferred` — logical conclusion from canon or established facts
- `emergent` — created by GM improvisation and filed after the session

Campaign facts supersede world canon where they conflict.

## Obsidian

Open the `Wiki/` folder as an Obsidian vault. All internal links use `[[Wiki/Namespace/Page]]` wikilink syntax and render as a graph in Obsidian's graph view.

## Linting

Run `/wiki lint` (via the llm-wiki skill in Claude Code) to check for orphaned pages, broken links, missing required properties, hub completeness, and campaign-specific rules like NPCs without allegiance fields or active modules with no linked session pages.

## Setting

**World of Greyhawk**, 576 CY. The campaign begins at the frontier borderlands of B2 and branches toward the Temple of Elemental Evil threat surfaced in T1. A spy network connecting the Temple of Evil Chaos to the Temple of Elemental Evil is the central conspiracy thread.
