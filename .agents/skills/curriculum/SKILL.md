---
name: curriculum
description: Revise the axes of a teach workspace — promote a cluster of orphan lessons into a new axis, or retire an axis whose mission facet is spent.
disable-model-invocation: true
argument-hint: "(run inside a teach workspace)"
---

Run this inside a `teach` workspace to revise its **axes** — the learning tracks recorded in `CURRICULUM.md`. teach _detects_ axes and flags them at lesson time; this skill is where you _decide_. Every change here is a deliberate act, confirmed by the user, then captured in a `learning-record`.

First read `CURRICULUM.md`, `MISSION.md`, the axis tags across `./lessons/`, and `./learning-records/`, so you reason from the real topology — not from what you remember.

Two rituals. Pick by why you were invoked.

## Promote — orphans into a new axis

Run when ≥2 orphans share a nameable concern (teach will have flagged a seed leading word).

1. **Name.** Propose the leading word for the axis and confirm it with the user. A good name is one compact, pretrained word the orphan lessons already rhyme with. _Completion: the user has agreed a single leading word._
2. **Ground against the mission.** Ask whether the axis serves a facet of the current `MISSION.md`.
   - **Yes** → write its _"serves the mission by…"_ line into `CURRICULUM.md`.
   - **No** → stop. A non-attachable axis is the signal the mission has **grown**. Switch to teach's mission-change ritual (update `MISSION.md`, confirm with the user, add a learning-record), _then_ return here.
   _Completion: the axis has a mission line, or the mission has been revised to make room for it._
3. **Sweep.** Tag every orphan that fits the new axis; leave the rest orphaned. Do **not** re-tag lessons already on other axes — unless the user explicitly asks, and then reconsider them one at a time, confirming each move. _Completion: every swept orphan carries the new axis tag, and the orphan list in `CURRICULUM.md` reflects exactly what remains._
4. **Set the mode.** Record the axis's dominant mode — `knowledge`, `skills`, or `wisdom` — in `CURRICULUM.md`. This governs whether interleaving paces it (teach's ZPD rule). _Completion: the axis has a mode._
5. **Record.** Add a `learning-record` capturing the birth: the lessons that seeded the axis, its name, and its mission link. _Completion: a numbered record exists in `./learning-records/`._

## Retire — an axis into dormancy

Run when a mission facet is achieved or dropped — **never** because an axis has merely gone cold. A cold axis is the _target_ of spacing, not a candidate for death.

1. **Confirm the facet is spent.** Check the axis's mission line against the current `MISSION.md`. If the facet is still live, do not retire — stop. _Completion: the user confirms the facet is achieved or abandoned._
2. **Mark dormant.** Move the axis to the dormant section of `CURRICULUM.md`. Keep its lessons and their tags intact — dormancy excludes the axis from ZPD/spacing selection but preserves it as reference, and is reversible. _Completion: the axis sits under dormant and no longer appears among active axes._
3. **Record.** Add a `learning-record` capturing the retirement and the mission change that drove it.

## The principle

The mission drives the topology: **mission grows → an axis is born; a facet is spent → an axis sleeps.** Activity never promotes or retires an axis — only the mission does, and only with the user's confirmation.
