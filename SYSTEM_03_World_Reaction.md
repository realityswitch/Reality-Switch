# SYSTEM 03 — World Reaction System

## PURPOSE
Visually and atmospherically reflect player reputation
in the game world.

The world must feel different based on player choices.

---

## WORLD CONTROLLER

Blueprint Name:
BP_WorldReactionController

Parent:
Actor

Placed:
Once per level

Responsibilities:
- Read player reputation
- Adjust lighting, fog, and mood
- Broadcast world state changes

---

## INPUT SOURCE

Source:
BP_ReputationComponent (from player)

Access Method:
Get Player Character
→ Get Reputation Component

Update Frequency:
- On mission completion
- On reputation change event

---

## MOOD STATES

Define 3 World Mood States:

ENUM:
E_WorldMood

Values:
- Balanced
- Uplifted
- Unstable

---

## MOOD LOGIC

If:
Community > 20 AND Stability > 10
→ Mood = Uplifted

If:
Community < -20 OR Stability < -20
→ Mood = Unstable

Else:
→ Mood = Balanced

---

## VISUAL REACTIONS (TEMP VALUES)

Uplifted:
- Directional Light Intensity +10%
- Light Color slightly warmer
- Sky brightness increased

Balanced:
- Default lighting

Unstable:
- Directional Light Intensity -15%
- Light Color slightly colder
- Fog density increased

---

## UI FEEDBACK

On Mood Change:
Display small HUD text:
"World Mood: Uplifted / Balanced / Unstable"

Duration:
2 seconds

---

## DEBUG (TEMP)

Print:
"World Mood Changed → [Mood Name]"

---

## COMPLETION CHECKLIST

[ ] Controller placed in level
[ ] Reputation read correctly
[ ] Mood changes based on values
[ ] Lighting reacts immediately
[ ] UI text confirms change

---

STATUS:
ATMOSPHERE CORE — ITERATE LATER
