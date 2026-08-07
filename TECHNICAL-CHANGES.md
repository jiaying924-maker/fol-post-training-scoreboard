# Technical Changes to FOL 2026 Dashboard

## State Structure Updates

### New State Properties
```javascript
trainingScores: Array(10).fill(0)      // Snapshot of scores when frozen
postTrainingScores: Array(10).fill(0)  // Points added after training
trainingPhase: 'live'                  // 'live' | 'frozen' | 'post-training'
scoreHistory: []                       // Existing history of changes
postTrainingHistory: []                // New history for post-training changes
```

---

## New Functions

### Score Management
- `getCombinedScores()` — Returns training + post-training scores
- `freezeTrainingScores()` — Saves current scores, transitions to post-training phase
- `resetPostTrainingScores()` — Clears post-training marks (with confirmation)
- `addPostTrainingScore(teamIdx, points)` — Award/deduct points to a team

### UI Rendering
- `renderPostTrainingPanel()` — Displays admin control panel with score adjustment buttons
- `clearPostTrainingHistory()` — Clears the change log

---

## Modified Functions

### getScores()
**Before:**
```javascript
function getScores() { return LIVE_SCORES || state.scores; }
```

**After:**
```javascript
function getScores() {
  const base = LIVE_SCORES || state.scores || Array(10).fill(0);
  // If training phase is frozen or post-training, use frozen training scores + post-training scores
  if (state.trainingPhase === 'frozen' || state.trainingPhase === 'post-training') {
    const trainingScores = state.trainingScores || base;
    const postTrainingScores = state.postTrainingScores || Array(10).fill(0);
    return trainingScores.map((t, i) => t + postTrainingScores[i]);
  }
  return base;
}
```

**Impact:** Leaderboard automatically shows combined scores after training is frozen.

### refreshAdminSelect()
**Before:** Rendered team scores with live data

**After:** Calls `renderPostTrainingPanel()` to show post-training controls

### checkAdminPw()
**Before:** Called `refreshAdminSelect()`

**After:** Calls `renderPostTrainingPanel()` for cleaner post-training UI

### openAdminModal()
**Before:** Called `refreshAdminSelect()` on open

**After:** Calls `renderPostTrainingPanel()` on open

---

## Admin Panel Interface

### New Controls (Post-Training Phase)

**Phase Indicator Button:**
- During LIVE: Shows "🔒 Freeze Training Scores" button
- After frozen: Shows status badge "✓ Training scores frozen — now in post-training phase"

**Per-Team Controls:**
For each team:
- Display: Training | Post-Training | Total
- Buttons: +1 and -1 to adjust post-training marks

**History Management:**
- "Clear History" — Remove change log
- "Reset All Post-Training" — Clear post-training scores

---

## Data Flow

### During Training Phase
```
Google Sheet (live) 
    ↓
LIVE_SCORES variable 
    ↓
getScores() → state.scores
    ↓
Forest Leaderboard display
```

### After Freeze
```
Current Scores 
    ↓
freezeTrainingScores() 
    ↓
state.trainingScores = saved baseline
state.trainingPhase = 'frozen'
    ↓
Admin adds post-training marks 
    ↓
state.postTrainingScores += points
    ↓
getScores() combines both 
    ↓
Forest Leaderboard shows total
```

---

## Browser Storage

### LocalStorage Key
- `fol2026` — Contains entire state object

### Persistence
All changes auto-save via `save()` function:
```javascript
function save() {
  try { localStorage.setItem('fol2026', JSON.stringify(state)); } catch(e) {}
}
```

Called after:
- `addPostTrainingScore()`
- `freezeTrainingScores()`
- `resetPostTrainingScores()`
- `clearPostTrainingHistory()`

---

## Backward Compatibility

✅ **Fully backward compatible**
- Existing state objects migrate automatically
- Missing properties default to empty arrays
- Training phase defaults to 'live' (backward compatible)
- Google Sheet integration unchanged
- All existing features work as before

### Migration Behavior
If user loads old state without new properties:
```javascript
state.trainingScores || Array(10).fill(0)     // Defaults to empty
state.postTrainingScores || Array(10).fill(0) // Defaults to empty
state.trainingPhase || 'live'                  // Defaults to live mode
```

---

## API / Integration Points

### getScores() - Critical Function
- Returns array of 10 numbers (one per team)
- Used by:
  - `renderGame()` — Forest view
  - `getSortedTeams()` — Leaderboard ranking
  - `renderHomeLeaderboard()` — Home page top-5
  - All tree growth calculations

### Event Handlers
Admin panel buttons:
- `freezeTrainingScores()` — Onclick handler
- `addPostTrainingScore(teamIdx, points)` — Onclick handler with parameters
- `clearPostTrainingHistory()` — Onclick handler
- `resetPostTrainingScores()` — Onclick handler with confirmation

---

## Testing Checklist

- [ ] Admin panel loads and displays all 10 teams
- [ ] +1 / -1 buttons correctly add/subtract points
- [ ] Freeze button works and shows confirmation status
- [ ] Leaderboard updates immediately after score changes
- [ ] Tree graphics grow based on combined scores
- [ ] Data persists after page refresh
- [ ] Historical tracking records all changes with timestamps
- [ ] Clear history removes change log but keeps scores
- [ ] Reset post-training resets scores with confirmation
- [ ] Works in different browsers (Chrome, Firefox, Safari, Edge)

---

## Files Modified

- `FOL FINAL BOARD.html` — Main dashboard with post-training features
- `FOL FINAL BOARD - POST-TRAINING.html` — Copy in project directory

## Files Created

- `POST-TRAINING-SCORING-GUIDE.md` — User guide
- `TECHNICAL-CHANGES.md` — This file
