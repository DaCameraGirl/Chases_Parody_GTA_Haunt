# Main Story Mission: "The Halloween Heist"

## Overview
A main story mission chain that runs parallel to the core objectives, revealing the truth about No-Face and the ritual beacon while giving Chase choices that affect the ending.

## Mission Structure

### Phase 1: "The Warning" (Triggers after collecting first loot stash)
**Objective:** Investigate the mysterious caller
**Location:** Any phone booth (new world object)
**NPC:** The Watcher (mysterious informant)

**Dialogue Choices:**
1. "Who are you?" → Learn about The Watcher's connection to the neighborhood
2. "What do you want?" → Get mission details
3. "I don't have time for this." → Delay mission (can return later)

**Outcome:** The Watcher warns that lighting the beacon will unleash something worse than No-Face unless Chase finds three "Soul Anchors" hidden around the neighborhood.

**Rewards:**
- Map markers for Soul Anchor locations
- +$100
- Fear -5

---

### Phase 2: "Soul Anchor Hunt" (After Phase 1)
**Objective:** Find and collect 3 Soul Anchors before lighting the beacon
**Locations:**
1. Behind the graveyard (near existing graves)
2. Rooftop of abandoned house (new parkour element)
3. Hidden in the storm drain (near road intersection)

**Mechanics:**
- Each anchor is guarded by a "Shadow Wraith" (tougher enemy)
- Collecting anchors increases supernatural heat
- Optional: Can skip this and light beacon anyway (bad ending path)

**Choices at each anchor:**
1. "Take the anchor" → Progress mission, +heat
2. "Destroy the anchor" → Alternative path, different ending
3. "Leave it" → Can return later

**Rewards per anchor:**
- Soul Anchor collected
- +$150
- Unlock "Spirit Vision" (see hidden collectibles)
- Fear resistance +10%

---

### Phase 3: "The Truth About No-Face" (After collecting 2+ anchors)
**Objective:** Meet The Watcher at the old church
**Location:** New location - Abandoned Church (northwest corner)
**NPC:** The Watcher reveals identity

**Story Reveal:**
- No-Face was once a neighborhood protector
- The ritual beacon was created to bind him
- Morrow and others have been using the beacon to control the neighborhood
- Chase's actions will determine No-Face's fate

**Dialogue Choices:**
1. "Help me free No-Face" → Redemption path
2. "Help me destroy No-Face" → Elimination path
3. "I'll decide at the beacon" → Neutral path (keeps options open)

**Rewards:**
- "Protective Sigil" item (reduces No-Face damage by 50%)
- +$200
- Unlock special costume: "The Mediator"

---

### Phase 4: "The Heist Setup" (After Phase 3)
**Objective:** Gather intel and resources for the final confrontation
**Locations:** Visit 3 NPCs in any order

**NPC Interactions:**
1. **Dre (Hearse Garage)** - Provides escape vehicle upgrade
   - Choice: Pay $300 or do a favor (timed delivery mission)

2. **Hex Broker (Hex Market)** - Sells ritual disruption items
   - Choice: Buy items ($500) or steal them (increases heat)

3. **Morrow (Costume Crypt)** - Reveals his role in the conspiracy
   - Choice: Confront him, blackmail him, or ally with him

**Rewards:**
- Escape vehicle speed boost
- Ritual disruption smoke bombs (3x)
- Morrow's blessing or curse (affects ending)

---

### Phase 5: "The Beacon Decision" (At the beacon)
**Objective:** Light the beacon and choose No-Face's fate
**Location:** Ritual Beacon (center of map)

**Major Choice (affects ending):**

**Option A: "Bind No-Face" (Original path)**
- Light beacon normally
- No-Face becomes more aggressive
- Standard escape to safehouse
- Ending: "The Cycle Continues"

**Option B: "Free No-Face" (Redemption path)**
- Use Soul Anchors to break the binding
- No-Face becomes neutral/helpful
- New objective: Escape together from "The Hunters"
- Ending: "The Liberation"

**Option C: "Destroy No-Face" (Elimination path)**
- Use ritual disruption items
- Boss fight against weakened No-Face
- Neighborhood becomes peaceful but empty
- Ending: "The Hollow Victory"

**Option D: "Reject the Ritual" (Secret path)**
- Requires all 3 Soul Anchors + Morrow's blessing
- Don't light beacon, break the ritual permanently
- Chase and No-Face both go free
- Ending: "The New Beginning"

---

### Phase 6: "The Escape" (After beacon choice)
**Objective:** Varies based on Phase 5 choice

**Path A (Bind):** Standard escape, No-Face chases
**Path B (Free):** Escape from "The Hunters" (new enemies), No-Face helps
**Path C (Destroy):** Escape from guilt and emptiness, no chase
**Path D (Reject):** Escape with No-Face as ally, face Morrow's wrath

**Dynamic Elements:**
- Heat level affects number of enemies
- Previous choices affect NPC reactions
- Timed escape (varies by path: 60-120 seconds)

---

## New NPCs

### The Watcher
- **Appearance:** Hooded figure, glowing eyes
- **Location:** Phone booths, abandoned church
- **Role:** Mission giver, lore keeper
- **Personality:** Mysterious, cryptic, ultimately helpful

### The Hunters (Path B enemies)
- **Appearance:** Dark suits, red ties, blank masks
- **Behavior:** Coordinated attacks, use nets and traps
- **Weakness:** Light sources, candy bombs

### Shadow Wraiths (Anchor guardians)
- **Appearance:** Darker, larger versions of regular wraiths
- **Stats:** 3 HP, faster movement, fear aura
- **Drops:** Soul Anchor + $200

---

## New Locations

### Abandoned Church
- Northwest corner of map
- Gothic architecture, broken windows
- Contains: The Watcher, lore documents, hidden stash
- Atmosphere: Eerie organ music, flickering candles

### Phone Booths (3 locations)
- Near Safehouse
- Near Hex Market
- Near Hearse Garage
- Glowing when mission active

### Storm Drain Entrance
- Near road intersection
- Requires crouching (new mechanic)
- Dark interior with Soul Anchor

---

## New Mechanics

### Soul Anchors
- Glowing purple orbs
- Emit protective aura when held
- Can be used or destroyed
- Affect ending

### Spirit Vision
- Toggle with V key
- Shows hidden collectibles
- Reveals enemy paths
- Drains stamina slowly

### Ritual Disruption Smoke Bombs
- Thrown like candy bombs
- Create safe zones
- Confuse No-Face temporarily
- Limited quantity (3)

---

## Rewards & Unlocks

### Costumes
- "The Mediator" - Reduces all damage by 20%
- "The Liberator" - No-Face doesn't attack (Path B ending)
- "The Hunter" - Increased candy bomb damage (Path C ending)

### Abilities
- Spirit Vision (permanent)
- Enhanced sprint (from vehicle upgrade)
- Fear resistance (from anchors)

### Endings
Each ending unlocks:
- Unique costume
- New game+ mode with different starting conditions
- Achievement/badge
- Bonus cash for next run

---

## Integration Points

### Triggers
1. First loot stash → Phase 1 phone call
2. 2 loot stashes → Soul Anchor locations revealed
3. Costume obtained → Watcher contact available
4. Before beacon → Phase 4 setup available
5. At beacon → Phase 5 choice

### Conflicts
- Can run parallel to "Costume Debt" side mission
- Choices in one mission can affect the other
- Heat is shared between missions
- NPCs remember interactions

---

## Technical Implementation Notes

### New Variables Needed
```javascript
const mainStoryState = {
  phase: 0,
  anchorsCollected: 0,
  anchorsDestroyed: 0,
  watcherMet: false,
  truthRevealed: false,
  finalChoice: null,
  huntersActive: false,
  spiritVisionUnlocked: false,
  ritualDisruptionBombs: 0
};
```

### New World Objects
- 3 phone booths
- 1 abandoned church
- 3 Soul Anchor spawn points
- 1 storm drain entrance

### New Enemy Types
- Shadow Wraith (3 HP, faster)
- The Hunters (coordinated AI)

### New UI Elements
- Soul Anchor counter
- Spirit Vision indicator
- Mission choice dialog (enhanced)
- Ending cutscene system

---

## Estimated Scope
- **Lines of code:** ~2000-2500
- **New assets:** 4 locations, 3 enemy types, 3 costumes
- **Dialogue nodes:** ~50-60
- **Testing time:** 3-4 hours for all paths
- **Player completion time:** 45-60 minutes (full story)

---

## Future Expansion Ideas
- DLC missions revealing other neighborhood secrets
- Multiplayer co-op mode (Chase + friend)
- Time trial modes for each ending path
- Community challenges (speedruns, no-damage runs)
