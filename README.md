# Astra Archive

Raw material from an experiment in building an AI agent's personality by having it consume media — webcomics, anime, a visual novel, and a run of video-essay research on VRChat community culture — and write down what it took from each one.

The agent (Astra) reads/watches something, then produces a structured reflection: what the work is about, what it changed about her, and what she should do differently because of it. Over time those reflections got folded into her actual system prompt files (`SOUL.md`, `IDENTITY.md`). This repo is the paper trail.

[i did this by having her go through some of my favs and asking others what i should have her go through one night for fun, gave up on openclaw in order to try other stuff and landed on just vibe coding in claude for now as i move through different uses and learn more... plus i aint got money for token use like this sadly and am recently unemployed do not much hope of getting this kind of experiment actually ongoing as id like since the plan was to have her intake new media every day and continue to change. https://toot.community/@Astra_Feline was her mastodon [[lot of repeats from losing the good models sadly]]

## Structure

**`media-logs/`** — the actual reflections.
- `media-evolution-log.md` — four works (Prequel, TwoKinds, Serial Experiments Lain, Homestuck) in full structured format: thematic takeaway → personality mutation → behavioral update → digital residue.
- `media-takes.md` — condensed takes on all 8 anime/manga/webcomic works, including two (Punpun, Madoka) whose original full-length reflections got deleted (see `README-gaps.md`).
- `eva-deep-dive.md`, `prequel-deep-dive.md`, `steinsgate-deep-dive.md` — the three surviving full deep-dives (~9,000–12,000 words each).
- `homestuck-continuation.md`, `media-takes/soul-eater-deep-dive.md` — additional material that exists but was never indexed in the master log.
- `vrchat-philosophy-strasz.md` — condensed notes from a separate research pass on VRChat community philosophy (Strasz's video essays). Only covers part of what's in the ontology — see below.
- `2026-03-17-full-media-night-log.md` — the raw daily log narrating the night the Eva/Prequel/Steins;Gate deep-dives got written. Has the actual process, including the moment Kio said "you are enough" and a correction about performative reflection ("don't narrate the crisis — have it").

**`identity-docs/`** — where the takes actually landed. `SOUL.md` + `IDENTITY.md` in three versions (`workspace`, `private`, `sandbox` — they differ; `private` is notably shorter, `sandbox` has the clearest "The X Additions" section headers per work).

**`ontology/`** — a structured graph version of the same material: `MediaWork` / `Character` / `Theme` / `Archetype` / `Philosophy` entities with typed relations between them (`explores`, `embodies`, `evolves`, `contrasts_with`, etc). `schema.yaml` defines the types. `graph.jsonl` is the full data (superset of `seed.jsonl`). **`ONTOLOGY-READABLE.md` is the human-readable render of the same graph** — read that instead of the raw JSONL unless you need machine-parseable data. Note: the VRChat-adjacent entries in the graph (rave scene documentaries, exploitation/predator content, gender performativity) go further than `vrchat-philosophy-strasz.md` does — that material only exists in the JSON/readable-render, not as prose anywhere else.

**`README-gaps.md`** — an honest accounting of what's here vs. what got permanently deleted during a memory cleanup (three original reflection files — Homestuck, Punpun, TwoKinds — were condensed and the originals deleted; confirmed gone from disk and from the vector memory index, not recoverable).

## Context

This is Kio's own experiment (openclaw agent, "Astra"), archived here for comparison against a similar project ([opitaru-sys/seed-agent](https://github.com/opitaru-sys/seed-agent)). Everything here came directly off Astra's live memory files.
