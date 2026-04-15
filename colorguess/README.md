# ColorGuess 🎨

A multiplayer color-guessing game for art workshops and gallery events.  
Players match color names to their correct colors using a color wheel — highest score wins!

---

## Quick Start (GitHub Pages)

### Step 1 — Upload to GitHub
Upload `index.html` to a new public GitHub repository.

### Step 2 — Set up Firebase (free, takes ~5 minutes)

The leaderboard requires a free Firebase Realtime Database. Without it, the game still works — scores just won't be shared between devices.

1. Go to [console.firebase.google.com](https://console.firebase.google.com)
2. Click **Add project** → give it any name → Continue
3. In the left sidebar: **Build → Realtime Database → Create Database**
   - Choose any region
   - Start in **test mode** (fine for a one-day event)
4. Click the gear icon → **Project settings → Your apps → Add app → Web (</> icon)**
5. Copy the `firebaseConfig` object that appears

### Step 3 — Paste your config into index.html

Find this block near the bottom of `index.html`:

```javascript
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT.firebaseapp.com",
  databaseURL: "https://YOUR_PROJECT-default-rtdb.firebaseio.com",
  ...
};
```

Replace it with your actual config from Step 2.

### Step 4 — Enable GitHub Pages

In your repo: **Settings → Pages → Source: main branch → / (root)** → Save

Your game will be live at:  
`https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/`

---

## How to Play

1. Students open the URL on their phones
2. Each player enters their **name** and a shared **room code** (e.g. `ART2025` — you announce this)
3. Each player gets **3 random color names** to match
4. Use the **color wheel** + **brightness slider** to find the closest match, then tap "Lock In My Guess"
5. Up to **100 points** per color, **300 points** total
6. Scores submit automatically — tap "Leaderboard" to see rankings live

---

## Multiplayer Tips for Your Event

- **Announce the room code** before students start (write it on a whiteboard)
- **Project the leaderboard** on a screen: open the game on a laptop, go to Leaderboard, refresh periodically
- Students can play **multiple rounds** — each submission appears on the board
- The **"This Room"** tab filters to your session's room code; **"All Time"** shows everything

---

## About the Color List

All 140+ colors are from the **W3C CSS Named Colors** standard — the canonical list used by every web browser and the same source ColorGuesser uses. Near-white colors are excluded for fairer gameplay.

---

## Tech Notes

- Single `index.html` file — no build step, no server
- Firebase free tier handles thousands of concurrent connections
- Works offline (except leaderboard) if Firebase isn't configured
