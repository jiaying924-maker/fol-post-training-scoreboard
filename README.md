# FOL 2026 — Post-Training Scoreboard

A standalone web application for managing and tracking post-training scores for the UR® Frontline of Love 2026 event.

## Features

✅ **Load Scores**
- Import from browser localStorage (FOL dashboard)
- Paste JSON score data
- Load sample data for testing

✅ **Award Post-Training Marks**
- Add/subtract points to each team
- Quick buttons: +1, +5, -1
- Automatic recalculation

✅ **Live Leaderboard**
- Real-time rankings
- Shows training + post-training breakdown
- Team colors and tier badges

✅ **Change History**
- Timestamped log of all changes
- Team, delta, and resulting score
- Easy history review

✅ **Export Data**
- Download scores as JSON
- Backup and archival support
- Share results easily

## Quick Start

### 1. Open the Application
```
FOL POST-TRAINING SCOREBOARD.html
```
Open in any modern web browser (Chrome, Firefox, Safari, Edge)

### 2. Load Your Scores

**Option A: From FOL Dashboard**
- Click "📂 Load from Browser"
- Requires FOL dashboard to be opened first

**Option B: From JSON**
- Click "📄 Load from JSON"
- Paste score array: `[26, 30, 25, 20, 22, 22, 21, 15, 15, 22]`
- Click "✓ Import"

**Option C: Sample Data**
- Click "🎯 Load Sample Data"
- For testing and demo

### 3. Award Points
- Use +1, +5, -1 buttons for each team
- Changes appear instantly on leaderboard
- Data auto-saves to browser

### 4. Export Results
- Click "📥 Export Data"
- Downloads JSON with all scores and history

## Teams

| # | Team | Code |
|---|------|------|
| 1 | 🏢 CSC | CSC |
| 2 | 🌿 BM | BM |
| 3 | 🌿 RU | RU |
| 4 | 🌿 GL | GL |
| 5 | 🌿 GY | GY |
| 6 | 🌿 SS2 | SS2 |
| 7 | 🌿 PC | PC |
| 8 | 🌿 CL | CL |
| 9 | 🌿 MA | MA |
| 10 | 🌿 SU | SU |

## Score Tiers

Trees grow based on combined score (training + post-training):

| Tier | Range | Tree |
|------|-------|------|
| 🌱 Seed | 0–10 pts | Seedling |
| 🌿 Sapling | 11–25 pts | Young growth |
| 🌳 Young Tree | 26–40 pts | Developing |
| 🌲 Giant Tree | 41–60 pts | Established |
| 🍎 Fruitful Tree | 61–80 pts | Productive |
| 🌟 Tree of Life | 81–100 pts | Ultimate |

## Data Storage

### Browser localStorage
- Scores stored locally in `fol2026-posttraining`
- Persists across page refreshes
- No server required
- Works offline

### Export Format
```json
{
  "timestamp": "2026-08-06T...",
  "trainingScores": [26, 30, 25, ...],
  "postTrainingScores": [5, 3, 8, ...],
  "combined": [31, 33, 33, ...],
  "teams": ["🏢 CSC", "🌿 BM", ...],
  "history": [...]
}
```

## Workflow

### Before Event
- Open and test the application
- Familiarize with the UI
- Try adding/removing sample points

### During Event
- Use main FOL dashboard for live scoring
- This app is for post-event use

### After Event
1. Open FOL POST-TRAINING SCOREBOARD.html
2. Load your event training scores
3. Freeze them as the baseline
4. Award post-training marks as teams complete activities
5. Export results for records

## Browser Requirements

- Modern browser (Chrome, Firefox, Safari, Edge)
- JavaScript enabled
- localStorage enabled (not private/incognito mode)
- No internet required

## Troubleshooting

**"No data found" error?**
- Make sure FOL dashboard was opened first
- Check localStorage is enabled

**Scores not saving?**
- Refresh page to reload
- Try a different browser
- Check if in private/incognito mode

**Can't import JSON?**
- Verify format: `[45, 38, 52, ...]` (array of 10 numbers)
- Check no extra characters
- Ensure all values are numbers

## Documentation

- **EXTRACT-SCORES-GUIDE.md** — How to extract scores from FOL dashboard
- **QUICK-START.md** — 2-minute quick reference
- **POST-TRAINING-SCORING-GUIDE.md** — Complete user guide
- **TECHNICAL-CHANGES.md** — For developers

## License

Event-specific tool for UR® Frontline of Love 2026

## Support

For issues or questions, refer to the documentation files included in this repository.

---

**Built with:** HTML5, CSS3, Vanilla JavaScript  
**No dependencies** • No build tools • Works anywhere

Open `FOL POST-TRAINING SCOREBOARD.html` to get started! 🌳
