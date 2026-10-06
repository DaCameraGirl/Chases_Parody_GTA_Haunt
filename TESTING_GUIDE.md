# Testing Guide: The Halloween Heist Main Story

## Quick Start Testing

### Prerequisites
1. Open `index.html` in a modern web browser (Chrome, Firefox, Edge)
2. Start the game by clicking "Start the Night"
3. Collect your first loot stash to trigger the main story

---

## Phase 1: The Warning

### How to Trigger
- Collect any loot stash (the glowing cash/candy bundles)
- Wait 3 seconds
- You'll receive a phone message: "Pick up. Any phone booth. Now."

### What to Test
1. **Phone Booth Locations:**
   - Near Safehouse (-18, 22)
   - Near Hex Market (-2, -28)
   - Near Hearse Garage (28, -12)

2. **Visual Indicators:**
   - Phone booths should glow cyan/turquoise
   - Glowing ring at base should be visible
   - Light should pulse

3. **Interaction:**
   - Walk up to any phone booth (within 1.8 units)
   - Press `E` to answer
   - Dialogue should appear with The Watcher

4. **Dialogue Choices:**
   - "Who are you?" → Learn backstory
   - "What do you want from me?" → Get mission details
   - "I don't have time for this." → Delay mission (can return later)

5. **Expected Outcomes:**
   - Accept mission: +$100, Fear -5, Soul Anchor locations revealed
   - Delay: Can return to any phone booth later
   - Reject: Mission ends (can restart by collecting more loot)

---

## Phase 2: Soul Anchor Hunt

### Locations
1. **Graveyard Anchor** (-35, -30)
   - Behind the existing graves
   - Guarded by Shadow Wraith

2. **Rooftop Anchor** (31, 12)
   - Near existing house
   - Guarded by Shadow Wraith

3. **Storm Drain Anchor** (8, -8)
   - Near road intersection
   - Guarded by Shadow Wraith

### What to Test

#### Visual Elements
- Purple/magenta glowing orbs
- Rotating rings (outer and inner)
- Floating particles orbiting the core
- Pulsing light effect

#### Shadow Wraiths
- **Stats:** 3 HP, faster than regular wraiths
- **Appearance:** Dark purple/black with glowing aura
- **Behavior:** Patrols around anchor, chases player within 6 units
- **Damage:** 12 HP per hit, +8 Fear
- **Defeat:** Hit with 3 candy bombs

#### Combat Testing
1. Approach anchor (Shadow Wraith should chase)
2. Throw candy bombs (Space or Left Click)
3. Each hit should show damage counter
4. After 3 hits, wraith disappears
5. Reward: +$200

#### Anchor Interaction
1. Defeat the Shadow Wraith first
2. Walk up to anchor (within 2 units)
3. Press `E` to interact
4. Choose one of three options:

**Option A: Take the anchor**
- +$150 cash
- Fear -10
- Supernatural heat +15
- First anchor unlocks Spirit Vision (Press `V`)

**Option B: Destroy the anchor**
- +$100 cash
- Supernatural heat +25
- The Watcher gets angry
- Alternative story path

**Option C: Leave it**
- Can return later
- No immediate effects

#### Spirit Vision (Unlocked after first anchor)
- Press `V` to toggle on/off
- Drains stamina slowly (8 per second)
- Makes collectibles glow brighter
- Shows enemy paths (future feature)
- Auto-disables when stamina reaches 0

---

## Phase 3: The Truth About No-Face

### How to Trigger
- Collect or destroy 2+ Soul Anchors
- Wait 2 seconds
- Receive phone message from The Watcher
- New location appears: Abandoned Church (-38, 38)

### What to Test

#### Church Location
- Northwest corner of map
- Purple zone marker
- "Abandoned Church" label
- Radius: 2.8 units

#### Interaction
1. Walk to church zone
2. Press `E` to interact
3. Dialogue with The Watcher appears

#### Story Choices (Affects Ending)

**Path A: "Help me free No-Face" (Redemption)**
- Unlocks "Grinning Saint" costume
- +$200 cash
- Sets path to 'free'
- Future: No-Face becomes ally

**Path B: "Help me destroy No-Face" (Elimination)**
- Grants 3 Ritual Disruption Bombs
- +$200 cash
- Sets path to 'destroy'
- Future: Boss fight at beacon

**Path C: "I'll decide at the beacon" (Neutral)**
- +$150 cash
- Keeps all options open
- Can choose at beacon later

---

## Known Issues & Limitations

### Current Implementation
✅ Phase 1: The Warning (Complete)
✅ Phase 2: Soul Anchor Hunt (Complete)
✅ Phase 3: The Truth (Complete)
⏳ Phase 4: The Heist Setup (Designed, not implemented)
⏳ Phase 5: The Beacon Decision (Designed, not implemented)
⏳ Phase 6: The Escape (Designed, not implemented)

### What Works
- Phone booth system
- Soul Anchor spawning and collection
- Shadow Wraith combat
- Spirit Vision toggle
- Dialogue system integration
- Path selection
- Rewards and unlocks

### What's Not Yet Implemented
- Phase 4-6 (see MISSION_DESIGN.md for details)
- Abandoned Church visual model (uses zone marker)
- Hunter enemies (Phase 6)
- Final beacon choices
- Multiple endings
- New game+ mode

---

## Testing Checklist

### Basic Flow
- [ ] Start game
- [ ] Collect first loot stash
- [ ] Receive phone message
- [ ] Find and interact with phone booth
- [ ] Accept mission from The Watcher
- [ ] Locate all 3 Soul Anchors
- [ ] Defeat Shadow Wraiths (3 HP each)
- [ ] Collect or destroy anchors
- [ ] Unlock Spirit Vision (after first anchor)
- [ ] Test Spirit Vision toggle (V key)
- [ ] Trigger Phase 3 (after 2+ anchors)
- [ ] Visit Abandoned Church
- [ ] Choose story path

### Combat Testing
- [ ] Shadow Wraith takes 3 candy bomb hits
- [ ] Damage counter displays correctly
- [ ] Wraith disappears after defeat
- [ ] Reward ($200) is granted
- [ ] Can collect anchor after wraith defeated

### UI Testing
- [ ] Phone booth prompt appears
- [ ] Soul Anchor prompt appears
- [ ] Church prompt appears
- [ ] Dialogue choices display correctly
- [ ] Toast notifications show
- [ ] Radio messages play
- [ ] Spirit Vision indicator (future)

### Integration Testing
- [ ] Main story runs alongside "Costume Debt" side mission
- [ ] Heat system affects both missions
- [ ] Cash/rewards accumulate correctly
- [ ] No-Face behavior unchanged (for now)
- [ ] Existing game mechanics still work

---

## Debug Commands (For Testing)

### Force Trigger Phase 1
Open browser console (F12) and run:
```javascript
triggerMainStoryPhase1();
```

### Force Trigger Phase 3
```javascript
mainStoryState.anchorsCollected = 2;
triggerMainStoryPhase3();
```

### Unlock Spirit Vision
```javascript
mainStoryState.spiritVisionUnlocked = true;
showToast("Spirit Vision unlocked! Press V");
```

### Add Cash for Testing
```javascript
state.cash += 1000;
showToast("Debug: +$1000");
```

### Spawn Shadow Wraith at Player Location
```javascript
spawnShadowWraith(chase.position.x, chase.position.z, 'test');
```

---

## Performance Notes

### Expected Performance
- 60 FPS on modern hardware
- 30-45 FPS on older systems
- Mobile: 20-30 FPS (not optimized)

### Performance Impact
- Shadow Wraiths: Low (3 max)
- Soul Anchors: Low (3 max)
- Phone Booths: Minimal (3 static)
- Spirit Vision: Minimal (simple shader effect)

### Optimization Tips
- Reduce particle count if laggy
- Disable Spirit Vision if stamina management is too hard
- Shadow Wraiths despawn after defeat (no memory leak)

---

## Troubleshooting

### "Phone booth doesn't glow"
- Make sure you collected a loot stash first
- Check console for errors (F12)
- Verify `mainStoryState.phoneBoothsActive === true`

### "Can't interact with Soul Anchor"
- Defeat the Shadow Wraith first
- Make sure you're within 2 units
- Check if anchor was already collected

### "Spirit Vision won't activate"
- Must collect at least 1 Soul Anchor first
- Check stamina level (needs >0)
- Press V key (not E)

### "Dialogue won't close"
- Press Escape key
- Click "Walk away" button
- Check if dialogue is marked as closable

### "Shadow Wraith won't die"
- Requires 3 candy bomb hits
- Make sure you have candy bombs (check HUD)
- Aim carefully (hitbox is generous but not infinite)

---

## Future Expansion Testing (When Implemented)

### Phase 4: The Heist Setup
- Visit Dre, Hex Broker, Morrow
- Make choices that affect ending
- Gather resources for final confrontation

### Phase 5: The Beacon Decision
- 4 different paths at beacon
- Each path leads to different ending
- Test all combinations

### Phase 6: The Escape
- Dynamic escape based on path chosen
- Hunter enemies (Path B)
- No-Face as ally (Path B)
- Timed escape sequences

---

## Reporting Issues

When reporting bugs, please include:
1. Browser and version
2. Steps to reproduce
3. Expected vs actual behavior
4. Console errors (F12 → Console tab)
5. Screenshots if visual bug

---

## Success Criteria

The main story mission is working correctly if:
✅ Phone booths trigger after first loot
✅ Dialogue system works smoothly
✅ Shadow Wraiths can be defeated
✅ Soul Anchors can be collected/destroyed
✅ Spirit Vision unlocks and toggles
✅ Phase 3 triggers after 2+ anchors
✅ Story paths can be selected
✅ No game-breaking bugs
✅ Performance remains stable
✅ Integrates with existing game systems

---

## Next Steps for Development

1. Implement Phase 4 (NPC interactions)
2. Implement Phase 5 (Beacon choices)
3. Implement Phase 6 (Dynamic escape)
4. Add Hunter enemy type
5. Create multiple endings
6. Add ending cutscenes
7. Implement New Game+ mode
8. Polish visual effects
9. Add sound effects for new elements
10. Optimize for mobile devices
