---
type: hub
updated: "2026-04-25"
---

# Wiki Dashboard

Overview and health status of your LLM Wiki.
Last lint: 2026-04-25 (`/wiki lint`) | Last status: 2026-04-25 | Last ingest: 2026-04-25 (Lolth overarching conspiracy + NPC section expansion)

## Page Counts

| Namespace | Content Pages | Hub |
|-----------|--------------|-----|
| Modules | 8 | ✓ |
| Locations | 7 | ✓ |
| NPCs | 30 | ✓ |
| Factions | 11 | ✓ |
| Sessions | 0 | ✓ |
| Conspiracy | 6 | ✓ |
| World | 0 | ✓ |
| Lore | 0 | ✓ |
| State | 0 | ✓ |
| **Total** | **62** (+ 11 hub/meta = **73**) | |

By type: entity 48 · knowledge 14 · hub 10 · schema 1

## Health

- Critical: 4 (false positives) + 0 real
- Warnings: 10 NPCs missing standard sections (Party Relationship, What The Party Knows, GM Truth, Description)
- Info: 4 (empty namespace hubs — expected)

## Open Issues

**Critical (false positives — no action needed)**
- Keep-on-the-Borderlands, Gnoll-Warband-J: "secret" keyword triggered cred-leak rule — game text, not credentials
- Sessions, World, Lore, State _index: flagged as empty — expected for pre-campaign namespaces

**Warnings — NPCs with missing standard sections**
- `Lubash` — missing: Party Relationship, What The Party Knows, GM Truth
- `Nira-Melubb` — missing: Party Relationship, GM Truth
- `Calmert` — missing: Party Relationship, What The Party Knows
- `Spugnoir` — missing: GM Truth
- `Terjon` — missing: GM Truth
- `Edric` — missing: Party Relationship, What The Party Knows
- `Marta` — missing: GM Truth
- `Furnok-of-Ferd` — missing: GM Truth
- `Brother-Smyth` — missing: Party Relationship, What The Party Knows, GM Truth
- `Y-dey` — missing: Description, Party Relationship, What The Party Knows, GM Truth
- `Kobort-and-Turuko` — missing: Description, What The Party Knows, GM Truth

**Info**
- Schema.md has placeholder link `[[Wiki/Entity/Name]]` — expected (template example)

## Namespaces

- [[Wiki/Modules/B2-Keep-on-the-Borderlands]] · [[Wiki/Modules/T1-Village-of-Hommlet]] · [[Wiki/Modules/A0-Danger-at-Darkshelf-Quarry]] · [[Wiki/Modules/A1-4-Scourge-of-the-Slavelords]] · [[Wiki/Modules/WG4-Forgotten-Temple-of-Tharizdun]] · [[Wiki/Modules/G1-3-Giants]] · [[Wiki/Modules/D1-3-Underdark]] · [[Wiki/Modules/Q1-Queen-of-the-Demonweb-Pits]]
- [[Wiki/Locations/Keep-on-the-Borderlands]] · [[Wiki/Locations/Caves-of-Chaos]] · [[Wiki/Locations/Village-of-Hommlet]] · [[Wiki/Locations/Welcome-Wench-Inn]] · [[Wiki/Locations/Moat-House]] · [[Wiki/Locations/Church-of-St-Cuthbert]] · [[Wiki/Locations/Burne-Rufus-Tower]]
- [[Wiki/NPCs/Sherlane]] · [[Wiki/NPCs/The-Curate]] · [[Wiki/NPCs/Evil-Priest-Spy]] · [[Wiki/NPCs/Shrine-Evil-Cleric]] · [[Wiki/NPCs/Captain-of-the-Guard]] · [[Wiki/NPCs/The-Advisor]] · [[Wiki/NPCs/The-Minotaur]] · [[Wiki/NPCs/The-Ogre]] · [[Wiki/NPCs/Elmo]] · [[Wiki/NPCs/Burne]] · [[Wiki/NPCs/Rufus]] · [[Wiki/NPCs/Jaroo-Ashstaff]] · [[Wiki/NPCs/Rannos-Davi]] · [[Wiki/NPCs/Gundigoot]] · [[Wiki/NPCs/Lareth-the-Beautiful]] · [[Wiki/NPCs/Lubash]] · [[Wiki/NPCs/Zert]] · [[Wiki/NPCs/Spugnoir]] · [[Wiki/NPCs/Furnok-of-Ferd]] · [[Wiki/NPCs/Kobort-and-Turuko]] · [[Wiki/NPCs/Gremag]] · [[Wiki/NPCs/Terjon]] · [[Wiki/NPCs/Calmert]] · [[Wiki/NPCs/Y-dey]] · [[Wiki/NPCs/Nira-Melubb]] · [[Wiki/NPCs/Brother-Smyth]] · [[Wiki/NPCs/Marta]] · [[Wiki/NPCs/Edric]] · [[Wiki/NPCs/Eclavdra]] · [[Wiki/NPCs/Edralve]]
- [[Wiki/Factions/Keep-Garrison]] · [[Wiki/Factions/Temple-of-Evil-Chaos]] · [[Wiki/Factions/Temple-of-Elemental-Evil]] · [[Wiki/Factions/Kobold-Tribe-A]] · [[Wiki/Factions/Orc-Tribe-B]] · [[Wiki/Factions/Orc-Tribe-C]] · [[Wiki/Factions/Goblin-Tribe-D]] · [[Wiki/Factions/Hobgoblin-Tribe-F]] · [[Wiki/Factions/Bugbear-Clan-H]] · [[Wiki/Factions/Gnoll-Warband-J]] · [[Wiki/Factions/Brotherhood-of-Slave-Lords]]
- [[Wiki/Conspiracy/Temple-Spy-Thread]] · [[Wiki/Conspiracy/ToEE-Spy-Network-Hommlet]] · [[Wiki/Conspiracy/Dual-Temple-Connection]] · [[Wiki/Conspiracy/Lareth-Shrine-Command-Chain]] · [[Wiki/Conspiracy/T1-B2-Cross-Module-Thread]] · [[Wiki/Conspiracy/Lolth-Overarching-Conspiracy]]

## Schema

- [[Wiki/Schema]] -- Namespace conventions, page types, lint rules
