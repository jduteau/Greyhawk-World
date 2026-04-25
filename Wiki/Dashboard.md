---
type: hub
updated: "2026-04-25"
---

# Wiki Dashboard

Overview and health status of your LLM Wiki.
Last lint: 2026-04-25 (`/wiki lint`) | Last ingest: 2026-04-25 (Moat-House + Gundigoot) | Last query: 2026-04-25 (innkeeper + moathouse)

## Page Counts

| Namespace | Content Pages | Hub |
|-----------|--------------|-----|
| Modules | 2 | ✓ |
| Locations | 5 | ✓ |
| NPCs | 14 | ✓ |
| Factions | 10 | ✓ |
| Sessions | 0 | ✓ |
| Conspiracy | 3 | ✓ |
| World | 0 | ✓ |
| Lore | 0 | ✓ |
| State | 0 | ✓ |
| **Total** | **34** (+ 10 hub/meta = **44**) | |

## Health

- Critical: 2
- Warnings: 3
- Info: 1

## Open Issues

**Critical**
- `NPCs/Elmo.md` — `faction` set to `[[Wiki/Factions/Temple-of-Elemental-Evil]]`; Elmo opposes ToEE (pre-existing). Fix: set to `""`
- `NPCs/Gundigoot.md` — `faction` set to `[[Wiki/Factions/Temple-of-Elemental-Evil]]`; Gundigoot opposes ToEE. Fix: set to `""`

**Warnings**
- `Sessions/_index.md`, `State/_index.md`, `World/_index.md`, `Lore/_index.md` — contain template placeholder links (`[[Wiki/.../SubTopic]]`) to non-existent pages; safe to clean up
- `Locations/Moat-House.md` — Lareth the Beautiful is key antagonist but has no NPC page (no broken link, just a gap)

**Info**
- Sessions, World, Lore, State namespaces are empty — expected for campaign in progress

## Namespaces

- [[Wiki/Modules/B2-Keep-on-the-Borderlands]] · [[Wiki/Modules/T1-Village-of-Hommlet]]
- [[Wiki/Locations/Keep-on-the-Borderlands]] · [[Wiki/Locations/Caves-of-Chaos]] · [[Wiki/Locations/Village-of-Hommlet]] · [[Wiki/Locations/Welcome-Wench-Inn]] · [[Wiki/Locations/Moat-House]]
- [[Wiki/NPCs/The-Castellan]] · [[Wiki/NPCs/The-Curate]] · [[Wiki/NPCs/Evil-Priest-Spy]] · [[Wiki/NPCs/Shrine-Evil-Cleric]] · [[Wiki/NPCs/Captain-of-the-Guard]] · [[Wiki/NPCs/The-Advisor]] · [[Wiki/NPCs/The-Minotaur]] · [[Wiki/NPCs/The-Ogre]] · [[Wiki/NPCs/Elmo]] · [[Wiki/NPCs/Burne]] · [[Wiki/NPCs/Rufus]] · [[Wiki/NPCs/Jaroo-Ashstaff]] · [[Wiki/NPCs/Rannos-Davi]] · [[Wiki/NPCs/Gundigoot]]
- [[Wiki/Factions/Keep-Garrison]] · [[Wiki/Factions/Temple-of-Evil-Chaos]] · [[Wiki/Factions/Temple-of-Elemental-Evil]] · [[Wiki/Factions/Kobold-Tribe-A]] · [[Wiki/Factions/Orc-Tribe-B]] · [[Wiki/Factions/Orc-Tribe-C]] · [[Wiki/Factions/Goblin-Tribe-D]] · [[Wiki/Factions/Hobgoblin-Tribe-F]] · [[Wiki/Factions/Bugbear-Clan-H]] · [[Wiki/Factions/Gnoll-Warband-J]]
- [[Wiki/Conspiracy/Temple-Spy-Thread]] · [[Wiki/Conspiracy/ToEE-Spy-Network-Hommlet]] · [[Wiki/Conspiracy/Dual-Temple-Connection]]

## Schema

- [[Wiki/Schema]] -- Namespace conventions, page types, lint rules
