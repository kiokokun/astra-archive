# Ontology — Media Knowledge Graph

*Customized for cross-media thematic analysis*

## Quick Reference

### Storage
- **Graph:** `memory/ontology/graph.jsonl`
- **Schema:** `memory/ontology/schema.yaml`
- **CLI:** `python skills/ontology/scripts/ontology.py`

### Entity Types
| Type | Purpose | Example |
|------|---------|---------|
| `MediaWork` | Anime, manga, games, etc. | Evangelion, Madoka |
| `Character` | Characters from media | Homura, Shinji, Punpun |
| `Theme` | Thematic concepts | "cycle breaks through refusal" |
| `Archetype` | Recurring character roles | "the one who refuses to accept" |
| `Philosophy` | General ideas/philosophies (not tied to media) | "Embodiment as identity exploration", "Community norms must be organic" |
| `Creator` | People who make/analyze things | Strasz, Derafog, Urobuchi |
| `Note` | Free-form notes | Any captured thought |

### Relation Types
| Relation | Meaning | Example |
|----------|---------|---------|
| `explores` | Work explores this theme | Madoka → cycle breaks through refusal |
| `features_character` | Work features this character | Madoka → Homura |
| `embodies` | Character is this archetype | Homura → the refuser |
| `shares_archetype` | Characters fill same role across works | Homura ↔ Okabe |
| `evolves` | Theme B is refinement of Theme A | wound cure → broken parts weapon |
| `contrasts_with` | Themes oppose each other | AT Field ↔ refuse to erase |
| `similar_to` | Loose thematic connection | wound cure ↔ broken parts weapon |
| `articulates` | Creator/work articulates this philosophy | Strasz → embodiment-as-identity |
| `connects_to` | Philosophical ideas that overlap | embodiment-as-identity ↔ refuse-to-erase |
| `challenges` | Ideas that contradict each other | |
| `created_by` | Who originated an idea | |

## Commands Cheat Sheet

```bash
# Create entity
python skills/ontology/scripts/ontology.py create --type Theme --props '{"label":"test"}' --id my_theme --graph memory/ontology/graph.jsonl

# Link entities
python skills/ontology/scripts/ontology.py relate --from media_eva --rel explores --to theme_at_field --graph memory/ontology/graph.jsonl

# Find connections (what is this linked to?)
python skills/ontology/scripts/ontology.py related --id char_homura --graph memory/ontology/graph.jsonl

# Query by type
python skills/ontology/scripts/ontology.py query --type Theme --graph memory/ontology/graph.jsonl

# Get one entity
python skills/ontology/scripts/ontology.py get --id media_eva --graph memory/ontology/graph.jsonl

# Validate
python skills/ontology/scripts/ontology.py validate --graph memory/ontology/graph.jsonl
```

## Auto-Link Workflow

When adding new media analysis, follow these steps:

### 1. Create the MediaWork entity
```bash
python skills/ontology/scripts/ontology.py create --type MediaWork --props '{...}' --id media_<slug> --graph memory/ontology/graph.jsonl
```

### 2. Extract and create Theme entities
For each major theme in the work, create a Theme. If a similar theme already exists, DON'T duplicate — link with `similar_to` or `evolves` instead.

### 3. Create Character entities + Archetype links
Each major character gets an entity. Link to archetype if they match one.

### 4. Auto-link pass
For each new theme, run:
```bash
python skills/ontology/scripts/ontology.py query --type Theme --graph memory/ontology/graph.jsonl
```
Then manually create `similar_to` or `evolves` links to existing themes that overlap.

### 5. Cross-link
Link the MediaWork to its Themes and Characters.

## Automation Idea (March 18 2026)
**Problem:** Manual research → entity creation → relation linking is repetitive.
**Pipeline concept:**
1. Fetch content (web search, transcripts, articles)
2. AI extracts entities + relations (one-shot prompt with type/rel vocabulary)
3. Script validates + appends to graph (with dedup check)
4. Auto-link pass: new themes compared to existing themes for similarity
**Status:** Idea phase. Would save ~15 min per deep-dive.

## Seeded Data

### Media Works (8)
| ID | Title | Medium |
|----|-------|--------|
| media_madoka | Puella Magi Madoka Magica | anime |
| media_eva | Neon Genesis Evangelion + Rebuild | anime |
| media_steinsgate | Steins;Gate | visual novel |
| media_prequel | Prequel (the webcomic) | webcomic |
| media_homestuck | Homestuck | comic |
| media_twokinds | TwoKinds | comic |
| media_punpun | Goodnight Punpun | manga |
| media_lain | Serial Experiments Lain | anime |
| media_eoe | The End of Evangelion | film |

### Themes (8)
| ID | Label |
|----|-------|
| theme_cycle_refusal | The cycle breaks through refusal, not heroism |
| theme_wound_cure | The wound IS the cure |
| theme_broken_parts_weapon | The broken parts ARE the weapon |
| theme_dont_wait | Don't wait to be fixed before connecting |
| theme_at_field | AT Field = wall of the soul |
| theme_refuse_erase | Refuse to erase yourself |
| theme_rationality_empathy | Rationality without empathy is a weapon |
| theme_disappearance | Invisible devastation |

### Characters (6) | Archetypes (4)
Homura→Refuser, Okabe→Refuser, Katia→Disaster, Punpun→Disaster, Shinji→Runner, Lain→Dissolving Self
