# Terra Nihil mod structure

Total conversion of EU4 (v1.37.5.0) focused on North America. This is a scaffold: files are placeholders
(comment-only) that mark where content goes. Existing `descriptor.mod` is preserved.

## Naming conventions
- All files, scripted effects/triggers, modifiers, events and keys use the `tn_` prefix.
- Event namespaces: `tn_government`, `tn_species`, `tn_magic`, `tn_confed`, `tn_horde`.
- Localisation files: `localisation/tn_*_l_english.yml` (UTF-8 BOM).
- One file per feature area so content can be added without merge conflicts.

## Government paths (Gang / Cult / Corporation)
| Area | Location |
|---|---|
| Government types | `common/governments/tn_governments.txt` |
| Reforms | `common/government_reforms/tn_{gang,cult,corporation}_reforms.txt` |
| Mechanics | `common/government_mechanics/tn_{gang,cult,corporation}_mechanics.txt` |
| Unique ideas | `common/ideas/tn_{gang,cult,corporation}_ideas.txt` |
| Decisions / events | `decisions/tn_*_decisions.txt`, `events/tn_government_events.txt` |

## Species system
EU4 has no native species concept; species sits beside religion and culture.
- Definitions/interactions (design reference): `common/species/`
- Implementation: scripted triggers/effects `common/scripted_{triggers,effects}/tn_species_*.txt`
  (e.g. `tn_is_primordian_culture`), species flags on countries/provinces, modifiers in `common/event_modifiers/`.
- Cultures in `common/cultures/` and religions in `common/religions/` should each map to a species.
- Culture groups `tn_<id>_group` (one per species: human, puella_magi, primordian, zombie, demihuman, dzorapsid, ultranian, karriyan); flags `tn_species_<id>`.
- Content: `decisions/tn_species_decisions.txt`, `events/tn_species_events.txt`.

## Magic system
- `common/spells/general.txt` – broadly available spells.
- `common/spells/{species,religion,culture,nation}_spells.txt` – unique spells.
- Availability gated by `tn_magic_triggers.txt`; casting effects in `tn_magic_effects.txt`;
  surfaced as decisions (`decisions/tn_magic_decisions.txt`) and events.

## Regional mechanics
- **American Confederation** (eastern/northern US, HRE-like, modelled on Post Finem's Italian Federation):
  `common/imperial_reforms/`, `common/subject_types/`, scripted effects/triggers `tn_american_confederation_*`,
  `decisions/tn_american_confederation_decisions.txt` (formables), `missions/`, `events/`.
- **Harikura Horde** (CK2 China-esque, for Primordian-culture nations): same files with `tn_harikura_horde_*`.

## Other content
Religions, cultures, decisions, missions (`missions/`), formables (`decisions/tn_formables.txt`), events,
tags (`common/country_tags/`), countries, history, map, gfx, interface are all stubbed.
Empty dirs contain `.gitkeep`.
