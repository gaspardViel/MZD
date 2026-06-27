# `CURRICULUM.md` format

The learning **topology** of the workspace: which **axes** exist, which lessons sit on each, what is still **orphan**, and what has gone **dormant**. Maintained by the `/curriculum` skill; read by teach to pace lessons (its Axes and Zone Of Proximal Development sections).

## Structure

### Active axes

One entry per axis:

- **Name** — the single **leading word**.
- **Mode** — `knowledge` | `skills` | `wisdom`. Governs whether interleaving paces the axis (skills only).
- **Serves the mission by** — one line tying the axis to a facet of `MISSION.md`.
- **Lessons** — the lesson numbers tagged to this axis, in order.

### Orphans

Lessons not yet on any axis — weak-fit lessons held in quarantine. List the lesson number and a one-line note on its concern, so clusters become visible before they are named.

### Dormant

Retired axes, kept for reference. Same shape as an active axis, plus the learning-record that retired it. Excluded from ZPD/spacing selection; reversible.

## Example

```markdown
# Curriculum

## Active axes

### `skill-craft` — mode: knowledge
Serves the mission by: making the operator fluent in writing the skills that produce MZD content.
Lessons: 0001, 0002, 0003, 0010, 0011, 0012, 0013

### `coordination` — mode: skills
Serves the mission by: orchestrating the multi-source fetch and scheduled runs that feed the briefs.
Lessons: 0004, 0006, 0007, 0008, 0009

### `gouvernance` — mode: wisdom
Serves the mission by: rendering the MZD's real structure legible to volunteers.
Lessons: 0005, 0014, 0015, 0016

## Orphans
_(none yet)_

## Dormant
_(none yet)_
```
