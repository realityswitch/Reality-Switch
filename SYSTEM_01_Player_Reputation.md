# SYSTEM 01 — Player & Reputation Core

## Purpose
Establish the player character and a persistent reputation system
that can be modified by missions, choices, and world interactions.

This system must:
- Exist independently of missions
- Be callable by any future system
- Drive visible world reactions

---

## PLAYER CHARACTER (Blueprint)

Blueprint Name:
BP_PlayerCharacter

Parent Class:
ThirdPersonCharacter

Responsibilities:
- Movement
- Camera control
- Interaction input
- Hosting the Reputation Component

---

## INPUTS

Interact Action:
Key: E (Keyboard)
Gamepad: Face Button Bottom

Purpose:
Used to interact with mission triggers, NPCs, and world objects.

---

## INTERACTION LOGIC

Method:
Line Trace from Camera Forward

Trace Distance:
500 units

On Hit:
If Actor implements "BPI_Interactable"
→ Call Interact() function

Fallback:
Print "Nothing to interact with"

---

## REPUTATION COMPONENT

Component Name:
BP_ReputationComponent

Attach To:
BP_PlayerCharacter

---

## REPUTATION VARIABLES

Float Community = 0
Float Transparency = 0
Float Stability = 0

Value Range:
-100 → +100

---

## CORE FUNCTION

Function Name:
ApplyReputationChange

Inputs:
- ReputationType (Enum)
- Delta (Float)

Logic:
Switch on ReputationType:
- Community → Community += Delta
- Transparency → Transparency += Delta
- Stability → Stability += Delta

Clamp all values to -100 / +100

---

## DEBUG FEEDBACK (TEMP)

After applying change:
Print string:
"Reputation Updated:
Community: X
Transparency: Y
Stability: Z"

---

## SAVE EXPECTATION

This system must:
- Persist for entire play session
- Be accessible by UI, missions, and world systems
- Never reset unless game restarts

---

## COMPLETION CHECKLIST

[ ] Player can move and look
[ ] Interact key works
[ ] Reputation Component exists
[ ] Reputation values change via function call
[ ] Debug text confirms updates

---

STATUS:
FOUNDATIONAL — DO NOT EXPAND YET
