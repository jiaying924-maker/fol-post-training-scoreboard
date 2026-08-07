# FOL 2026 — Post-Training Scoring Guide

## Overview
Your enhanced dashboard now supports two-phase scoring:
1. **Training Phase** — Live scoring during the event (Aug 3-4)
2. **Post-Training Phase** — Continue adding marks until the next event

All scores persist in your browser's local storage, so they survive page refreshes and sessions.

---

## How It Works

### Phase 1: Training (LIVE)
- Scores load from your Google Sheet in real-time
- Displayed on the Forest Leaderboard as teams earn points
- Trees grow based on cumulative points (Seed → Sapling → Young Tree → Giant Tree → Fruitful Tree → Tree of Life)

### Phase 2: Freeze & Post-Training
Once training ends, you freeze the current scores:
- Click **🔒 Freeze Training Scores** in the Admin Panel
- This saves all training-phase scores as a baseline
- You can now add post-training marks without affecting the original training data
- Total score = Training Score + Post-Training Marks

---

## Using the Admin Panel

### Password
- Default password: `fol2026`
- Used to unlock score management features

### Freezing Training Scores
1. Open Admin Panel (⚙️ Admin button on Forest tab)
2. Enter password to unlock
3. Click **🔒 Freeze Training Scores**
   - This transitions from LIVE phase to POST-TRAINING phase
   - Current training scores are saved
   - Status indicator shows: "✓ Training scores frozen — now in post-training phase"

### Adding Post-Training Marks
Once frozen, each team shows:
- **Training:** [original score during event]
- **Post-Training:** [marks added after event]
- **Total:** [Training + Post-Training combined]

For each team:
- Click **+1** to award 1 post-training point
- Click **-1** to subtract 1 post-training point

### Viewing Score Changes
The history automatically tracks:
- Timestamp of each change
- Team name
- Points added (+) or removed (-)
- Resulting total score

### Resetting Data
- **Clear History** — removes the change log (keeps scores)
- **Reset All Post-Training** — resets post-training marks to 0 (keeps training scores)

---

## Score Display

### Leaderboard Shows
- **During Training:** Training points only
- **After Freeze:** Training + Post-Training combined

### Tree Growth Tiers
Trees display based on total combined score:
- 🌱 **Seed** — 0–10 pts
- 🌿 **Sapling** — 11–25 pts
- 🌳 **Young Tree** — 26–40 pts
- 🌲 **Giant Tree** — 41–60 pts
- 🍎 **Fruitful Tree** — 61–80 pts
- 🌟 **Tree of Life** — 81–100 pts

---

## Data Storage

### Where Scores Are Saved
- **Google Sheet** (during training) — your real-time scoring source
- **Browser LocalStorage** — backup and post-training marks

### Automatic Backups
- All post-training changes auto-save to your browser
- History is logged with timestamps
- Data persists even if you close the page

### What Gets Saved
```
{
  scores: [current training scores],
  trainingScores: [frozen scores after training],
  postTrainingScores: [marks added after training],
  trainingPhase: "frozen" | "post-training",
  scoreHistory: [...],
  postTrainingHistory: [...]
}
```

---

## Workflow Example

**Day 2, 5 PM:** Event ends, teams have scored during training
1. Open Admin Panel → Unlock with password
2. Click **🔒 Freeze Training Scores**
   - CSC: 45 pts, BM: 38 pts, RU: 52 pts, etc.
   - These scores are now frozen as the training baseline

**Day 3-7:** Continue adding post-training marks
- CSC participates in post-event challenges: +5 pts
- BM submits follow-up work: +8 pts
- Status now shows:
  - CSC: Training 45 + Post-Training 5 = **50 pts total**
  - BM: Training 38 + Post-Training 8 = **46 pts total**

**Before Next Event:**
- Review combined scores on the Forest Leaderboard
- Export or screenshot for records
- All history is preserved

---

## FAQ

**Q: Can I go back to LIVE scoring?**
A: The training phase transition is one-way. If you need to return to live scoring, refresh and reload your Google Sheet scores.

**Q: What if scores change on my Google Sheet after freezing?**
A: Once frozen, post-training mode uses your saved training scores. The Sheet becomes the source for new training sessions only.

**Q: Can I add negative points?**
A: Yes, use the **-1** button to deduct points. Scores cannot go below 0.

**Q: Where's the team-by-team breakdown?**
A: In the Admin Panel, each team shows:
  - Training score (frozen)
  - Post-training score (current)
  - Total (combined)

**Q: Can I export the post-training history?**
A: Yes, use your browser's developer console:
  ```javascript
  console.log(JSON.stringify(state.postTrainingHistory, null, 2))
  ```

---

## Keyboard Shortcuts
- Press **Esc** to close the Admin modal
- **Enter** to submit password in Admin login

---

## Support
If scores don't save:
1. Check that your browser allows localStorage (not in private/incognito mode)
2. Ensure you're not running out of storage space
3. Try clearing browser cache and reloading

For technical issues with the sheet integration, verify:
- Your Google Sheet's CSV publication URL is correct
- The sheet has columns: "team" and "score"
- Team codes match: CSC, BM, RU, GL, GY, SS2, PC, CL, MA, SU
