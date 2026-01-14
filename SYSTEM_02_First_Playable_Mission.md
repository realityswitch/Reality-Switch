# SYSTEM 02 — First Playable Mission (Vertical Slice)

## Mission Name
"Stolen Signal"

---

## PURPOSE
Introduce the core gameplay loop:
- Discover mission
- Make a moral choice
- Apply reputation consequence
- Change world state
- Complete mission

This mission proves the game works.

---

## MISSION FLOW

1. Player enters mission area
2. Mission UI appears
3. Player chooses an action
4. Reputation is modified
5. World reacts
6. Mission completes

---

## MISSION TRIGGER

Blueprint Name:
BP_MissionTrigger

Parent:
Actor

Components:
- Box Collision
- Billboard (Editor only)

On Player Overlap:
- Call StartMission()

Trigger can only fire once.

---

## MISSION MANAGER

Blueprint Name:
BP_MissionManager

Responsibilities:
- Track mission state
- Spawn mission UI
- Resolve choices
- Signal completion

Mission States:
- Inactive
- Active
- Completed

---

## MISSION UI

Widget Name:
WBP_MissionChoice

UI Elements:
- Mission Title Text
- Mission Description Text
- Choice Button A
- Choice Button B
- Choice Button C

---

## MISSION TEXT

Title:
STOLEN SIGNAL

Description:
"A rogue data packet is destabilizing your zone.
You can secure it quietly, expose it publicly,
or sell it to a rival network."

---

## PLAYER CHOICES

CHOICE A — Secure Quietly
Effect:
- Community +10
- Transparency -5

CHOICE B — Expose Publicly
Effect:
- Transparency +10
- Stability -5

CHOICE C — Sell to Rival
Effect:
- Stability +10
- Community -10

Each choice must:
- Call ApplyReputationChange
- Close mission UI
- Notify MissionManager

---

## WORLD REACTION (TEMP)

After mission completes:
- Print:
"Zone Mood Shifted"

(Visual changes implemented in SYSTEM 03)

---

## MISSION COMPLETION

On Completion:
- Set Mission State = Completed
- Disable Trigger
- Show "Mission Complete" message

Mission must never repeat.

---

## COMPLETION CHECKLIST

[ ] Mission triggers on overlap
[ ] UI appears correctly
[ ] Buttons function
[ ] Reputation updates correctly
[ ] Mission completes once
[ ] Debug messages confirm flow

---

STATUS:
FIRST PLAYABLE — DO NOT POLISH
