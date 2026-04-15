# ColorGuess 🎨

A multiplayer color-guessing game for art workshops and gallery events.

---

## Setup (5 minutes)

### Step 1 — Create the GitHub repository

1. Create a **new public** GitHub repository (e.g. `colorguess`)
2. Upload `index.html` and an empty `scores.json` file (contents: `[]`)

### Step 2 — Create a Personal Access Token

This lets the game write scores to `scores.json` directly — no server needed.

1. Go to **github.com → Settings → Developer settings → Personal access tokens → Tokens (classic)**
2. Click **Generate new token (classic)**
3. Give it a name (e.g. `ColorGuess`)
4. Set expiration to **7 days** (plenty for a one-day event)
5. Check only the **`repo`** scope
6. Click **Generate token** and copy it (starts with `ghp_`)

### Step 3 — Edit index.html

Find this block near the top of the `<script>` section:

```javascript
const GH_CONFIG = {
  owner: 'YOUR_GITHUB_USERNAME',
  repo:  'YOUR_REPO_NAME',
  file:  'scores.json',
  token: 'YOUR_PERSONAL_ACCESS_TOKEN'
};
```

Fill in your actual username, repo name, and the token you just copied.

### Step 4 — Enable GitHub Pages

**Settings → Pages → Source: main branch → / (root) → Save**

Your game is live at:
`https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/`

---

## How the leaderboard works

- When a player finishes, their score is appended to `scores.json` in your repo via the GitHub API
- Any player can refresh the leaderboard to see current standings
- The **"This Room"** tab filters by room code; **"All Time"** shows everything
- If the GitHub API is unavailable, scores save to the device's local storage automatically as a fallback
- The file stores up to 500 entries (oldest trimmed automatically)

## Running the event

1. Announce the **room code** (e.g. `ART2025`) — write it on a whiteboard
2. Share the GitHub Pages URL with students
3. Open the Leaderboard tab on a laptop/TV and hit **Refresh ↻** periodically to show standings live
4. After the event, the full `scores.json` is in your repo if you want to export results

## Security note

The token gives write access to this one repo. For a classroom event this is fine — students could theoretically submit arbitrary scores if they view source. If you want to prevent that, the proper solution is a server-side API, but for a friendly in-class game the file approach is perfect.

After the event, delete or expire the token in GitHub settings.
