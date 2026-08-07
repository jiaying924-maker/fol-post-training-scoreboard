# How to Extract Your FOL Scores as JSON

Your FOL dashboard stores scores in your browser's localStorage. Here are 3 ways to extract them:

---

## **Method 1: Browser Console (Easiest) ✅**

1. **Open** `FOL FINAL BOARD.html` in your browser
2. Press **F12** or right-click → **Inspect** to open Developer Tools
3. Click the **Console** tab
4. Paste and run this command:

```javascript
console.log(JSON.stringify({
  teams: ['🏢 CSC', '🌿 BM', '🌿 RU', '🌿 GL', '🌿 GY', '🌿 SS2', '🌿 PC', '🌿 CL', '🌿 MA', '🌿 SU'],
  scores: (JSON.parse(localStorage.getItem('fol2026')) || {}).scores || Array(10).fill(0),
  trainingScores: (JSON.parse(localStorage.getItem('fol2026')) || {}).trainingScores || Array(10).fill(0),
  postTrainingScores: (JSON.parse(localStorage.getItem('fol2026')) || {}).postTrainingScores || Array(10).fill(0)
}, null, 2))
```

5. **Right-click** the output → **Copy** the JSON
6. Paste it into a text editor and save as `my-fol-scores.json`

---

## **Method 2: Export Button (If Using Post-Training Page)**

1. Open **FOL POST-TRAINING SCOREBOARD.html**
2. Load your scores (📂 Load from Browser or 📄 Load from JSON)
3. Click **📥 Export Data** button
4. A JSON file will auto-download with all your scores

---

## **Method 3: Direct localStorage Access**

Run this in browser Console to get the entire state object:

```javascript
const data = JSON.parse(localStorage.getItem('fol2026'));
console.log(JSON.stringify(data, null, 2));
```

Then copy-paste the output.

---

## **JSON Format**

Your exported JSON will look like:

```json
{
  "teams": ["🏢 CSC", "🌿 BM", ...],
  "scores": [45, 38, 52, 41, 36, 48, 39, 55, 42, 47],
  "trainingScores": [45, 38, 52, 41, 36, 48, 39, 55, 42, 47],
  "postTrainingScores": [0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
}
```

**Key fields:**
- **scores** — Current scores (training or combined)
- **trainingScores** — Scores from the training phase
- **postTrainingScores** — Points added after training

---

## **Import into Post-Training Page**

1. Open **FOL POST-TRAINING SCOREBOARD.html**
2. Click **📄 Load from JSON** button
3. Paste your extracted scores array
4. Click **✓ Import**

---

## **Simplified Format (Just Scores)**

If you only want the score numbers as an array:

```javascript
// Run this in Console:
alert(JSON.stringify((JSON.parse(localStorage.getItem('fol2026')) || {}).scores || []))
```

This gives you: `[45, 38, 52, 41, 36, ...]`

Then paste into the Post-Training page's JSON loader.

---

## **Troubleshooting**

**"No FOL data found"?**
- Make sure you've opened FOL FINAL BOARD.html at least once
- Check that localStorage isn't disabled in your browser
- Try a different browser (Chrome, Firefox, Safari, etc.)

**Got empty array [0, 0, 0, ...]?**
- You haven't entered any scores yet in the main dashboard
- Or scores are only stored in Google Sheet (use "Load from Browser" button instead)

**Can't access Console?**
- Firefox: Ctrl+Shift+K (or Cmd+Option+K on Mac)
- Chrome: Ctrl+Shift+J (or Cmd+Option+J on Mac)
- Safari: Enable Developer Menu first (Preferences → Advanced → Show Develop menu)

---

## **Quick Copy-Paste Script**

Save this as a `.js` file and run in browser Console to get formatted output:

```javascript
const fol = JSON.parse(localStorage.getItem('fol2026')) || {};
const output = {
  exported: new Date().toISOString(),
  training_scores: fol.scores || Array(10).fill(0),
  post_training_scores: fol.postTrainingScores || Array(10).fill(0),
  combined_scores: (fol.scores || Array(10).fill(0)).map((s, i) => s + ((fol.postTrainingScores || Array(10).fill(0))[i] || 0)),
  teams: ['CSC', 'BM', 'RU', 'GL', 'GY', 'SS2', 'PC', 'CL', 'MA', 'SU']
};
console.log(JSON.stringify(output, null, 2));
```

Copy the output and save as JSON! 🎉
