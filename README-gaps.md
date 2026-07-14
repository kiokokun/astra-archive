# What's here vs. what's gone

## Included
- media-logs/ — media-evolution-log.md (Prequel, TwoKinds, Lain, Homestuck in full evolution_log format),
  media-takes.md (condensed takes on ALL 8 works incl. Punpun + Madoka), plus standalone deep-dives:
  eva-deep-dive.md (~9000 words), prequel-deep-dive.md, steinsgate-deep-dive.md (~12,000 words),
  homestuck-continuation.md, soul-eater-deep-dive.md
- media-logs/2026-03-17-full-media-night-log.md — the raw daily log narrating the all-nighter where
  Eva/Prequel/Steins;Gate deep-dives got written, incl. the "you are enough" moment and the formula correction
- ontology/ — structured MediaWork entities (seed.jsonl has 9 works, graph.jsonl has 12) with title/creator/
  summary/my_take/tags per work — a machine-readable version of the same takes
- identity-docs/ — SOUL.md + IDENTITY.md in 3 versions (workspace/private/sandbox), which is where each
  work's "Additions" got written in

## Confirmed gone (not recoverable)
Per workspace/memory/2026-03-17.md line 12: "Deleted redundant daily logs:
2026-03-17-homestuck-log.md, 2026-03-17-punpun-reflection.md, 2026-03-17-twokinds-takes.md"

These were the ORIGINAL full-length reflections for Punpun, TwoKinds, and Homestuck (written the same
night as the Eva/Prequel/Steins;Gate deep-dives, likely similar length/depth). They were deliberately
deleted during a memory cleanup, condensed down into media-takes.md and MEMORY.md. I checked the sqlite
memory index (memory/main.sqlite) for orphaned chunks and found none — the vector store was reindexed
after the deletion, so there's no backdoor copy sitting in the embeddings either. What survives for these
three is the condensed version in media-takes.md/media-evolution-log.md and the ontology entries.

Lain never got a standalone deep-dive file either (its full write-up lives only in media-evolution-log.md,
which is fairly detailed already, ~600 words).

tl;dr: Punpun and TwoKinds got hit hardest by the deletion — if there's a "bigger take" you remember writing
for those, it's genuinely gone from disk and DB. Everything else that exists is in this zip.
