---
type: hub
updated: "2026-05-06"
---

# Wiki Dashboard

Overview and health status of your LLM Wiki.
Last lint: 2026-05-06 (`/wiki lint --fix`) | Last ingest: 2026-05-06 (Session 2 recap)

## Page Counts

| Namespace | Content Pages | Hub |
|-----------|--------------|-----|
| Modules | 8 | ✓ |
| Locations | 8 | ✓ |
| NPCs | 34 | ✓ |
| PCs | 5 | ✓ |
| Factions | 11 | ✓ |
| Sessions | 2 | ✓ |
| Conspiracy | 6 | ✓ |
| World | 1 | ✓ |
| Lore | 0 | ✓ |
| State | 1 | ✓ |
| **Total** | **76** (+ 12 hub/meta = **88**) | |

By type: entity 58 · knowledge 16 · project 2 · hub 11 · schema 1

## Health

- Critical: 0
- Warnings: 0
- Info: 2 (false-positive credential rule on game text; empty Lore hub — expected pre-campaign)

## Open Issues

**Info (no action needed)**
- Various location/NPC pages: "secret" in game text triggers cred-leak rule — not actual credentials (secret door, secret compartment, secret store, etc.)
- Lore _index hub is empty — expected until in-world documents are discovered in play
- Schema.md placeholder links (`[[Wiki/Entity/Name]]`, `[[Wiki/...]]`, etc.) — template examples, not real refs

## Namespaces

- [[Wiki/Modules/B2-Keep-on-the-Borderlands]] · [[Wiki/Modules/T1-Village-of-Hommlet]] · [[Wiki/Modules/A0-Danger-at-Darkshelf-Quarry]] · [[Wiki/Modules/A1-4-Scourge-of-the-Slavelords]] · [[Wiki/Modules/WG4-Forgotten-Temple-of-Tharizdun]] · [[Wiki/Modules/G1-3-Giants]] · [[Wiki/Modules/D1-3-Underdark]] · [[Wiki/Modules/Q1-Queen-of-the-Demonweb-Pits]]
- [[Wiki/Locations/Keep-on-the-Borderlands]] · [[Wiki/Locations/Caves-of-Chaos]] · [[Wiki/Locations/Village-of-Hommlet]] · [[Wiki/Locations/Welcome-Wench-Inn]] · [[Wiki/Locations/Moat-House]] · [[Wiki/Locations/Church-of-St-Cuthbert]] · [[Wiki/Locations/Burne-Rufus-Tower]] · [[Wiki/Locations/Veluna]]
- [[Wiki/NPCs/Sherlane]] · [[Wiki/NPCs/The-Curate]] · [[Wiki/NPCs/Evil-Priest-Spy]] · [[Wiki/NPCs/Shrine-Evil-Cleric]] · [[Wiki/NPCs/Captain-of-the-Guard]] · [[Wiki/NPCs/The-Advisor]] · [[Wiki/NPCs/The-Minotaur]] · [[Wiki/NPCs/The-Ogre]] · [[Wiki/NPCs/Chief-Ishka]] · [[Wiki/NPCs/Kobold-Shaman]] · [[Wiki/NPCs/Elmo]] · [[Wiki/NPCs/Burne]] · [[Wiki/NPCs/Rufus]] · [[Wiki/NPCs/Jaroo-Ashstaff]] · [[Wiki/NPCs/Rannos-Davi]] · [[Wiki/NPCs/Gundigoot]] · [[Wiki/NPCs/Lareth-the-Beautiful]] · [[Wiki/NPCs/Lubash]] · [[Wiki/NPCs/Zert]] · [[Wiki/NPCs/Spugnoir]] · [[Wiki/NPCs/Furnok-of-Ferd]] · [[Wiki/NPCs/Kobort-and-Turuko]] · [[Wiki/NPCs/Gremag]] · [[Wiki/NPCs/Terjon]] · [[Wiki/NPCs/Calmert]] · [[Wiki/NPCs/Y-dey]] · [[Wiki/NPCs/Nira-Melubb]] · [[Wiki/NPCs/Brother-Smyth]] · [[Wiki/NPCs/Marta]] · [[Wiki/NPCs/Edric]] · [[Wiki/NPCs/Eclavdra]] · [[Wiki/NPCs/Edralve]] · [[Wiki/NPCs/Eckhardt]] · [[Wiki/NPCs/Marten]]
- [[Wiki/PCs/Thomas]] · [[Wiki/PCs/Aldric]] · [[Wiki/PCs/Conrad]] · [[Wiki/PCs/Lance]] · [[Wiki/PCs/Michael]]
- [[Wiki/Factions/Keep-Garrison]] · [[Wiki/Factions/Temple-of-Evil-Chaos]] · [[Wiki/Factions/Temple-of-Elemental-Evil]] · [[Wiki/Factions/Kobold-Tribe-A]] · [[Wiki/Factions/Orc-Tribe-B]] · [[Wiki/Factions/Orc-Tribe-C]] · [[Wiki/Factions/Goblin-Tribe-D]] · [[Wiki/Factions/Hobgoblin-Tribe-F]] · [[Wiki/Factions/Bugbear-Clan-H]] · [[Wiki/Factions/Gnoll-Warband-J]] · [[Wiki/Factions/Brotherhood-of-Slave-Lords]]
- [[Wiki/Sessions/Session-1-Hommlet-to-the-Keep]] · [[Wiki/Sessions/Session-2-The-Caves-and-the-Kobold-Parley]]
- [[Wiki/Conspiracy/Temple-Spy-Thread]] · [[Wiki/Conspiracy/ToEE-Spy-Network-Hommlet]] · [[Wiki/Conspiracy/Dual-Temple-Connection]] · [[Wiki/Conspiracy/Lareth-Shrine-Command-Chain]] · [[Wiki/Conspiracy/T1-B2-Cross-Module-Thread]] · [[Wiki/Conspiracy/Lolth-Overarching-Conspiracy]]
- [[Wiki/World/Archclericy-of-Veluna]]

## Schema

- [[Wiki/Schema]] — Namespace conventions, page types, lint rules
