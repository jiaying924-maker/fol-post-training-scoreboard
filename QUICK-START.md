# Quick Start: Post-Training Scoring

## Setup (One Time)

1. **Use the enhanced file:**
   - Open `FOL FINAL BOARD - POST-TRAINING.html` (the new version with post-training features)
   - Or replace your original with the enhanced version

2. **That's it!** — The file works exactly like before during training

---

## During Event (Aug 3-4)

✅ Everything works as before:
- Scores load from your Google Sheet
- Teams earn points
- Trees grow on the leaderboard
- All live updates happen in real-time

---

## After Event — Add Post-Training Marks

### Step 1: Freeze Training Scores
1. Open the **Forest** tab
2. Click **⚙️ Admin** button
3. Enter password: `fol2026`
4. Click **🔒 Freeze Training Scores**
   - Your event scores are now locked in as the baseline
   - Status shows: "✓ Training scores frozen — now in post-training phase"

### Step 2: Award Post-Training Marks
1. In the Admin Panel, find each team
2. For each point to award:
   - Click **+1** to add a point
   - Click **-1** to deduct a point
3. Changes appear instantly on the leaderboard
4. All data auto-saves

### Step 3: View Updated Leaderboard
1. Close Admin Panel
2. View the **Forest** tab
3. Teams now show combined scores:
   - Training points + Post-Training points = Total

---

## Example

**During Event:**
- CSC Training: 45 pts
- BM Training: 38 pts

**After Freeze:**
1. Click "🔒 Freeze Training Scores"

**Post-Event Activities (Days 3-7):**
1. CSC submits post-training work: click +5 on CSC
2. BM participates in challenge: click +8 on BM

**New Totals:**
- CSC: 45 (training) + 5 (post-training) = **50 pts**
- BM: 38 (training) + 8 (post-training) = **46 pts**

---

## Common Questions

**Q: Can I undo a point?**
A: Yes, click -1 to reverse it. Click +1 / -1 multiple times if needed.

**Q: What if I make a mistake and freeze too early?**
A: Refresh the page and use your Google Sheet scores to restore training data. Post-training is additive only.

**Q: Can teams see their post-training scores?**
A: Yes! The leaderboard shows the combined total. They can see training vs post-training breakdown if you hover over their scores in the admin panel.

**Q: How do I export the results?**
A: 
- Take a screenshot of the leaderboard
- Or open browser Console (F12) and run:
  ```javascript
  console.log(state)
  ```
  Then copy-paste the output to save as text

**Q: Can I add marks after the next event starts?**
A: Yes! The system supports multiple phases. The post-training marks stay separate until you choose to reset.

---

## Files in Your Project

📁 `C:\Users\Jemim\OneDrive\Desktop\AI WENNIE\`

- **FOL FINAL BOARD - POST-TRAINING.html** ← Use this file
- **POST-TRAINING-SCORING-GUIDE.md** ← Detailed guide (this file)
- **TECHNICAL-CHANGES.md** ← For developers/technical details
- **QUICK-START.md** ← Quick reference (you're reading it!)

---

## Password

- **Admin Password:** `fol2026`
- Can be changed by editing the file (search for `const ADMIN_PW`)

---

## Troubleshooting

**Scores not saving?**
- Make sure you're not in private/incognito mode
- Check if localStorage is enabled in your browser settings

**Lost data after refresh?**
- Data is stored in browser cache — clearing cache will erase it
- Always freeze/backup important scores

**Admin panel won't open?**
- Make sure browser has JavaScript enabled
- Try refreshing the page
- Check browser console (F12) for errors

**Post-training marks show but leaderboard doesn't update?**
- Refresh the page
- Close and reopen the Forest tab
- Check that you clicked the right team's +1 button

---

## Pro Tips

💡 **Backup Important Scores**
- Before resetting, take a screenshot or export via console
- Keep a spreadsheet backup of important milestones

💡 **Use the History**
- Admin Panel shows all changes with timestamps
- Useful for auditing and records

💡 **Test Before Event**
- Try adding/removing points before the real event
- Familiarize yourself with the workflow

💡 **Multiple Sessions**
- Scores persist across browser sessions
- Safe to close and reopen the page

---

## Next Steps

1. ✅ Replace your current file with `FOL FINAL BOARD - POST-TRAINING.html`
2. ✅ Test the admin panel (optional)
3. ✅ Run your event normally (no changes needed)
4. ✅ When training ends, freeze scores
5. ✅ Start adding post-training marks as needed

---

**Questions?** Check `POST-TRAINING-SCORING-GUIDE.md` for detailed documentation.
