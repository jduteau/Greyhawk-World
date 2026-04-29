---
wiki-version: 1.1
last-updated: 2026-04-26
maintained-by: llm-wiki
type: schema
---

# Wiki Schema
AD&D campaign world knowledge base. Setting: World of Greyhawk, 576 CY.
Serves two consumers: the GM (browsing Obsidian) and the world arbiter
agent (querying during play). Write every page to serve both.

## Namespace Conventions

- Top-Level: Wiki/Locations, Wiki/NPCs, Wiki/PCs, Wiki/Factions, Wiki/Sessions, Wiki/Conspiracy, Wiki/World, Wiki/Lore, Wiki/Modules, Wiki/State
- Page Naming: Title Case, hyphens for multi-word (`Wiki/Projects/My-Project`)
- Max Depth: 3 levels (e.g., `Wiki/NPCs/Person/NPCName`)
- Hub Pages: Every namespace level has a hub page listing its children
- Folder Hierarchy: Namespaces map to folders (e.g., `Wiki/Factions/ScarletWizards.md`)

### Namespace Definitions

| Namespace | Contains | Page Type |
|-----------|----------|-----------|
| `Wiki/Locations` | Places: villages, dungeons, regions, buildings | entity |
| `Wiki/NPCs` | Named characters the party has met or heard of | entity |
| `Wiki/PCs` | Player characters, active and retired | entity |
| `Wiki/Factions` | Organizations, cults, power groups, conspiracies | entity |
| `Wiki/Sessions` | Individual play session records | project |
| `Wiki/Conspiracy` | Synthesized analysis of conspiracy threads | knowledge |
| `Wiki/World` | Greyhawk canon: geography, politics, deities | knowledge |
| `Wiki/Lore` | In-world documents, rumors, legends, inscriptions | knowledge |
| `Wiki/Modules` | Module metadata and campaign placement notes | knowledge |
| `Wiki/State` | Current session state block (overwritten each session) | knowledge |


## Page Types and Required Properties

### When to Use Each Type

**entity** — Use for anything with identity and persistence in the
world: a named person, a named place, a named organization. If it
has a name and the party could encounter it, it is an entity.
Subtype is determined by the entity-type field.

**project** — Use for sessions only. A session is a discrete play
event with a date, a location, and outcomes. Not used for anything
else in this wiki.

**knowledge** — Use for synthesized analysis, world reference
material, in-world documents, and module metadata. If it is a fact
about the world rather than a named thing in the world, it is
knowledge. Subtype is determined by the domain field.

**feedback** — Not used in this wiki.

**hub** — One per namespace. Structural index page only.

### Entity

An entity is a named, persistent thing in the world: a person,
place, or organization. Every named NPC, location, faction, and
player character gets its own entity page.

**How to classify during ingest:**

- Named player character (controlled by a player, not the GM) → entity-type: pc
- Named person, creature, or character (GM-controlled) → entity-type: npc
- Named place (village, dungeon, room, region, building) → entity-type: location
- Named group, cult, church, guild, army, conspiracy → entity-type: faction

**Required YAML frontmatter (all entities):**

```yaml
type: entity
entity-type: pc | npc | location | faction
name: [canonical name]
status: active | dead | destroyed | cleared | unknown
source: [module code e.g. "T1" | "emergent" | "world-canon" | "player-created"]
confidence: canon | established | inferred | emergent
created: YYYY-MM-DD
updated: YYYY-MM-DD
```

---

#### entity-type: pc

Player characters. One page per character. Covers active, dead, and
retired PCs. These pages are player-facing by default; use `gm_only:
true` only for content the player themselves does not know (e.g., a
dominated PC whose player is unaware of the compulsion).

**Required YAML frontmatter (additional fields):**

```
player: [player name or handle]
race: [AD&D race e.g. "Human", "Half-Elf"]
class: [AD&D class or multi-class e.g. "Fighter", "Fighter/Magic-User"]
level: [integer, or slash-separated for multi-class e.g. "3/2"]
alignment: [AD&D alignment e.g. "Lawful Good"]
deity: [patron deity, or omit if none]

# Ability Scores
str: [integer]
str_exceptional: [integer 01-00, omit if not applicable]
int: [integer]
wis: [integer]
dex: [integer]
con: [integer]
cha: [integer]

# Combat Stats
hp_current: [integer]
hp_max: [integer]
ac: [integer — descending AC; lower is better]
thac0: [integer]

# Advancement
xp_current: [integer]
xp_next_level: [integer]
first_session: [integer]

# Status
pc_status: active | dead | missing | retired
last_location: "[[Wiki/Locations/...]]"
```

**Required sections:**

- **Description** — appearance, personality, notable traits
- **Background** — origin, motivation, what drove them to adventure
- **Saving Throws** — table of current saves; update on level-up:

  | Save | Target |
  |------|--------|
  | Aimed Magic Items | |
  | Breath Weapons | |
  | Death / Paralysis / Poison | |
  | Petrification / Polymorph | |
  | Spells / Unlisted | |

- **Equipment & Inventory** — weapons, armor, significant gear; update each session
- **Spells Known / Memorized** — classes with spells only; for Magic-Users, list
  spellbook contents separately from currently memorized spells; update each session
- **Special Abilities** — class features, racial abilities, proficiencies,
  anything non-standard; note source (class, race, magic item)
- **Party Relationships** — how this PC relates to other PCs and significant NPCs;
  tag changes [Session N]
- **History** — significant events in session order; tag [Session N]
- **Advancement Log** — level-ups, XP milestones, notable gains; tag [Session N]
- **Cross-References**

---

#### entity-type: npc

Additional required fields:

```yaml
npc_status: alive | dead | missing | unknown
npc_scope: world | regional | local
last_location: "[[Wiki/Locations/...]]"
allegiance_known: [what the party believes]
allegiance_true: [GM truth — may differ from above]
faction: "[[Wiki/Factions/...]]"
first_session: [integer]
gm_only: true   # add when allegiance_true differs from allegiance_known
```

**npc_scope definitions:**

- `world` — continental or planar significance, sourced from world
  canon. Rulers of major states, archmages, demigods. The party
  may never meet them directly. Exempt from missing-session-history
  lint checks.
- `regional` — significant within a region but below world scale.
  Local lords, prominent merchants, faction officers. May or may
  not be encountered directly.
- `local` — specific to a module or adventure location. Named NPCs
  the party will meet: innkeepers, guards, rivals, allies.

**Required sections:**

- **Description** — appearance, manner, memorable traits
- **Role** — function in the world
- **Party Relationship** — current standing; update each change;
  tag changes [Session N]
- **What the Party Knows** — information revealed in play;
  this section mirrors the player wiki
- **GM Truth** — actual allegiance, hidden motives, connections;
  mark this section gm_only
- **History** — significant events in session order; tag [Session N]
- **Cross-References**

---

#### entity-type: location

Additional required fields:

```yaml
region: [Greyhawk region e.g. "Viscounty of Verbobonc"]
location_status: pristine | active | partially-cleared | cleared | destroyed | unknown
layer: world | regional | campaign
```

**Required sections:**

- **Overview** — what this place is, why it matters
- **Geography** — physical description, access routes, features
- **Current Status** — what the party has done here; update each visit
- **Known Inhabitants** — NPCs and creatures with links
- **Party History** — chronological visits; tag [Session N]
- **GM Notes** — secrets, hooks; mark section gm_only
- **Cross-References**

---

#### entity-type: faction

Additional required fields:

```yaml
alignment: [AD&D alignment e.g. "LE"]
scale: local | regional | continental | planar
known_to_party: true | partial | false
faction_type: religious | criminal | political | military | conspiracy | other
```

**Required sections:**

- **Overview** — purpose, reach, history
- **Leadership** — known leaders; distinguish party-known from GM-truth
- **Goals** — stated goals and true goals; true goals gm_only
- **Party Relationship** — current standing; tag changes [Session N]
- **Conspiracy Connections** — links up/down/sideways in the web
- **GM Notes** — future plans, hooks; mark section gm_only
- **Cross-References**

---

### Project

Used for sessions only.

**Required YAML frontmatter:**

```yaml
type: project
status: completed | active | abandoned
session_number: [integer]
title: [short descriptive title]
date_played: YYYY-MM-DD
campaign_date: [in-world CY date if tracked]
party_level: [average level at session start]
primary_location: "[[Wiki/Locations/...]]"
created: YYYY-MM-DD
updated: YYYY-MM-DD
```

**Required sections:**

- **Summary** — 2-3 sentences; what happened, what changed
- **Narrative** — full session blog post from session scribe;
  paste directly; immutable once filed; never edit
- **Key Events** — bullet list of significant moments;
  cross-reference all NPCs, Locations, Factions affected
- **World State Changes** — what changed as a result of this session;
  feeds the update pass on other pages after ingest
- **Open Threads** — leads, questions, unresolved situations;
  link to Conspiracy or NPC pages where they live
- **Party Status at End** — location, resources, immediate plans
- **Cross-References**

Sessions are immutable once filed. Never overwrite session content.

---

### Knowledge

Used for conspiracy analysis, world canon, in-world lore, and
module metadata.

**How to classify during ingest:**

- Analysis of how factions/NPCs connect, conspiracy threads → domain: conspiracy
- Facts from published Greyhawk sources (geography, politics, gods) → domain: world
- In-world documents, rumors, legends, inscriptions → domain: lore
- Module catalogue entry and campaign placement notes → domain: module
- Current session state block → domain: state

**Required YAML frontmatter (all knowledge pages):**

```yaml
type: knowledge
domain: conspiracy | world | lore | module | state
confidence: canon | established | inferred | emergent
created: YYYY-MM-DD
updated: YYYY-MM-DD
```

---

#### domain: conspiracy

Additional required fields:

```yaml
conspiracy_tier: surface | intermediate | deep | planar
conspiracy_status: active | party-disrupted | resolved | unknown
party_awareness: unaware | partial | significant | full
```

**Required sections:**

- **The Thread** — who is behind it, what they want, how it connects
- **Known Evidence** — facts the party has discovered; session refs
- **Hidden Evidence** — GM-only facts not yet discovered; gm_only
- **Key Actors** — NPCs and Factions with links
- **Connections** — links to other Conspiracy pages
- **Status** — what the party has done to this thread
- **Cross-References**

---

#### domain: world

Additional required fields:

```yaml
world_category: geography | polity | deity | history | calendar | culture
canon_source: [e.g. "World of Greyhawk Boxed Set 1983"]
canon_date: [CY date e.g. "576 CY"]
```

**Required sections:**

- **Overview** — what this world entity is
- **Relevance to Campaign** — how it connects to active content;
  grows as campaigns develop
- **Cross-References**

---

#### domain: lore

Additional required fields:

```yaml
lore_type: rumor | document | legend | prophecy | inscription
reliability: reliable | unreliable | planted | unknown
discovered_session: [integer]
source_location: "[[Wiki/Locations/...]]"
```

**Required sections:**

- **Content** — the actual text or account, written in in-world voice
- **GM Analysis** — what is true, false, misleading; gm_only
- **Connections** — what this lore points toward
- **Cross-References**

---

#### domain: module

Additional required fields:

```yaml
module_code: [e.g. "T1"]
module_title: [full title]
module_author: [e.g. "Gary Gygax"]
published: [year]
level_range: [e.g. "1-3"]
canonical_placement: [Greyhawk location as written]
campaign_placement: [your actual placement if different]
campaign_status: not-started | active | completed | partially-completed
party_progress: [brief note]
```

**Required sections:**

- **Campaign Role** — what this module contributes to the arc
- **Source Material Notes** — GM decisions, divergences from text
- **Linked Content** — wikilinks to all Location, NPC, Faction,
  and Conspiracy pages that originated from this module
- **Sequence** — what comes before and after; links to other modules
- **Cross-References**

---

#### domain: state

The current session state block. Lives at Wiki/State/Current-Session.md.
This page is OVERWRITTEN (not appended) after each session.
It is the only page in the wiki that is not append-only.

```yaml
domain: state
confidence: established
```

**Content format:**

```
Party:
- [[Wiki/PCs/Name]] (Class Level) — [current HP]/[max HP] HP, AC [n]
- [[Wiki/PCs/Name]] (Class Level) — [current HP]/[max HP] HP, AC [n]

Location: [[Wiki/Locations/...]]

Situation: [one sentence]

Active Threads:
- [[Wiki/Conspiracy/...]]
- [[Wiki/Conspiracy/...]]

Last Session: [[Wiki/Sessions/Session-NN-Title]]
```

This page feeds the world arbiter at session start. Keep it minimal.

---

### Hub

Standard hub page. One per namespace. No changes from base schema.

```yaml
type: hub
namespace: Wiki/NamespaceName
```

---

## Confidence Levels

| Level | Meaning |
|-------|---------|
| `canon` | Directly stated in published source material. Do not contradict without explicit campaign decision. |
| `established` | Confirmed in play, recorded in a Session page. Authoritative for this campaign. |
| `inferred` | Logical conclusion from canon or established facts. Flag when asserting. |
| `emergent` | Created by GM improvisation during play. Treat as established once filed and verified. |

Campaign facts supersede world canon where they conflict.

---

## Visibility Flags

```yaml
gm_only: true       # GM-facing content only. Never exposed in player wiki.
                    # Apply to: allegiance_true, GM Notes, GM Truth,
                    # Hidden Evidence, unrevealed conspiracy tiers,
                    # module content not yet encountered by the party.
                    # On PC pages: use only for content the player
                    # themselves does not know (e.g., active charm/domination).

player_known: true  # Explicitly revealed to characters in play.
                    # Appears in both GM wiki and player wiki.
```

Default (no flag): GM wiki only, not yet in player wiki.

PC pages are player-facing by default; `gm_only` is the exception,
not the rule.

## Ingest Source Routing

Identify the source type and apply these rules before extracting.

**Character sheet / PC creation:**

- Create a `Wiki/PCs/` entity page with `entity-type: pc`
- Set `confidence: established`
- Set `source: player-created`
- Do NOT apply `gm_only` to ability scores, saves, class abilities,
  inventory, or history — these are player-facing by default
- Exception: apply `gm_only: true` to any section containing GM
  knowledge the player does not have (rare; e.g., active domination)
- Update the `Wiki/PCs` hub to include the new page
- Update Wiki/State/Current-Session.md to link the new PC page

**Module text (T1, B2, G1, etc.):**

- Create entity pages for all named NPCs, locations, factions
- Create knowledge/module page for the module itself
- Set confidence: canon on all pages
- Set gm_only: true on allegiance_true for all NPC pages
- Rooms and areas not yet visited: set location_status: pristine
- Do NOT create session pages from module text

**Session transcript:**

- Create a session (project) page
- Update `party_relationship` on all NPCs encountered
- Update `location_status` on all locations visited
- Update `hp_current`, `xp_current`, and `level` on all active PC pages
- Append to **History** section on PC pages for significant events; tag [Session N]
- Append to **Advancement Log** on PC pages for any level gained; tag [Session N]
- Update `last_location` on all PC pages to match end-of-session location
- Tag all new content [Session N]
- Overwrite Wiki/State/Current-Session.md with updated state block
- File World State Changes as update candidates for affected pages

**Linking thread documents:**

- Create or update conspiracy (knowledge) pages
- Set confidence: established
- Cross-reference all NPCs and factions involved

**World canon sources (1983 Boxed Set, Bloch Campaign Guide, etc.):**

- Create world (knowledge) pages only
- Set confidence: canon
- Create NPC entity pages for named rulers and significant figures; set npc_scope: world or regional as appropriate
- Do NOT overwrite established campaign facts with world canon
- Campaign layer supersedes world layer where they conflict

**Monster statistics:**

- Generic monster types (gnolls, orcs, giant frogs) belong in the rules wiki, not this world wiki
- Named or unique creatures get an NPC entity page with entity-type: npc
- Monster factions (a gnoll warband) get a Faction entity page; individual members do not get their own pages

---

## Append and Contradiction Rules

- APPEND ONLY — never delete or overwrite existing content
- Exception: Wiki/State/Current-Session.md is overwritten each session
- Tag all session additions: [Session N]
- If new information contradicts existing content, flag explicitly:

```
> ⚠️ CONTRADICTION [Session N]: [description of conflict]
```

Do not silently resolve contradictions. Surface them for human review.

---

## Cross-Reference Rules

- Every wiki page MUST have at least one `[[Wiki/...]]` link to another wiki page
- Hub pages MUST list ALL child pages in their namespace
- When a page mentions an entity that has its own page, use `[[Wiki/Entity/Name]]` link syntax
- Tags: use `#tag` for lightweight categorization (e.g., `#docker`, `#deploy`, `#critical`)
- External links: `[Text](URL)` for URLs outside the wiki

## Content Format Rules

- Flat Markdown (no outliner `- ` prefix required on every line)
- Properties: YAML frontmatter between `---` fences at the top of the file
- Sections: standard `## Heading` syntax
- Code blocks: fenced with triple backticks
- NEVER store credentials, passwords, or API tokens in wiki pages

## L1/L2 Architecture

- The standard llm-wiki L1 memory path is disabled for this wiki.
- No credentials or sensitive data exist in campaign knowledge.
- All content including session state lives in the git-tracked vault.

### L1 equivalent = Wiki/State/Current-Session.md

- Loaded explicitly at session start by the world arbiter.
- Contains: party status (HP, AC, class, level, links to PC pages),
  current location, active threads, pointer to last session page.

### L2 = Everything else in the wiki

- Queried on demand. Locations, NPCs, PCs, Factions, Sessions, Conspiracy, World, Lore, Modules.

### Boundary Rules

- If the arbiter needs it at the start of every session to orient itself → it belongs in the state page.
- Everything else → L2, queried when needed.

## Ingest Workflow

1. Identify source type (character sheet | module | session | linking thread | world canon)
2. Apply source routing rules above
3. Extract: named entities, facts, relationships, dates, decisions
4. Classify each item by namespace and page type using definitions above
5. Scan wiki: identify existing pages to update, new pages to create
6. Target: 5-15 page touches per ingest
7. Create new pages with all required properties
8. Existing pages: APPEND only — never overwrite (exception: Wiki/State/Current-Session.md)
9. Update hub pages to include new child pages
10. Add cross-references between all affected pages
11. Set `updated` on all changed pages
12. Git commit after ingest

## Lint Rules

**Standard rules:**

- **Orphan Detection** — pages with 0 incoming links (hubs excluded)
- **Stale Detection** — `updated` > 180 days AND confidence is canon
  or established
- **Missing Properties** — pages missing type-specific required properties
- **Broken References** — links to non-existent pages
- **Hub Completeness** — hub pages missing children in their namespace
- **Credential Leak** — scan for token/password/secret patterns
- **Empty Pages** — only properties, no content
- **Cross-Ref Minimum** — fewer than 1 outgoing link

**Campaign-specific rules:**

- NPC page missing `allegiance_true` field → flag
- NPC page with `npc_scope: local` and no session history after 5 sessions of play → flag (world and regional scope exempt)
- Location page missing `location_status` → flag
- Session page missing World State Changes section → flag
- Conspiracy page with fewer than 3 linked NPC or Faction pages → flag
- NPC marked `npc_status: dead` appearing in sessions after their death session → flag
- PC page missing `hp_current` or `ac` → flag
- PC page missing **Saving Throws** section → flag
- PC page with `pc_status: active` not updated within last 3 sessions → flag (character state may be stale)
- PC page with `pc_status: dead` appearing in sessions after their death session → flag
- State block listing a PC name with no corresponding `Wiki/PCs/` page → flag
- Contradiction flags (⚠️) present → surface for human review
- Pages with `confidence: inferred` not updated in 10+ sessions → flag as potentially stale
- Module page with `campaign_status: active` and no linked Session pages → flag
