# FLWC Training Portal

**Family Life Worship Center — Volunteer Training**

A ministry training portal for FLWC volunteers. Sound & Tech is the first ministry live. Additional ministries are pre-built and ready to activate as training content is developed.

**Live site:** `https://kps871.github.io/FLWC-Training/`

---

## Repository Structure

```
FLWC-Training/
│
├── index.html                          # Portal home — ministry selection
│
├── sound-tech/
│   ├── index.html                      # Sound & Tech ministry home
│   ├── training/
│   │   ├── x32-anatomy.html            # X32 Front Panel — interactive zones + quiz
│   │   ├── x32-rear-panel.html         # X32 Rear Panel — interactive zones + quiz
│   │   ├── science-of-sound.html       # Frequency spectrum quiz
│   │   ├── gain-structure.html         # Gain structure quiz
│   │   ├── eq-compression.html         # EQ & compression quiz
│   │   ├── iem-mixes.html              # IEM monitor mixes quiz
│   │   └── service-flow.html           # Service flow scenario quiz
│   └── reference/
│       ├── eq-troubleshoot.html        # EQ troubleshooting — screen + print
│       ├── compression-ref.html        # Compression quick reference — screen + print
│       ├── service-checklist.html      # Service day checklist — interactive + print
│       └── how-to/
│           └── copy-channel-preset.html  # How-To: Copy a channel preset
│
├── ministry-2/ through ministry-10/
│   └── index.html                      # Placeholder pages — activate in index.html config
│
├── assets/
│   ├── styles.css                      # Shared design system
│   └── x32-board.webp                  # X32 front panel photo (used in anatomy quiz)
│
└── README.md
```

---

## Deploying to GitHub Pages

### First-time setup

**Step 1 — Rename the repo (if you haven't already)**

Go to `https://github.com/kps871/FLWC-SE-Training` → Settings → General → Repository name → change to `FLWC-Training` → Rename.

GitHub will redirect the old URL automatically. No links break.

**Step 2 — Upload the files**

Option A — GitHub web interface (simplest):
1. Go to `https://github.com/kps871/FLWC-Training`
2. Click **Add file → Upload files**
3. Drag the entire `FLWC-Training` folder contents into the upload area
4. Scroll down, add a commit message like `Initial portal build`
5. Click **Commit changes**

Option B — Git command line:
```bash
cd /path/to/FLWC-Training
git init
git remote add origin https://github.com/kps871/FLWC-Training.git
git add .
git commit -m "Initial portal build"
git branch -M main
git push -u origin main
```

**Step 3 — Enable GitHub Pages**

1. Go to the repo → **Settings → Pages**
2. Under **Source**, select **Deploy from a branch**
3. Branch: `main` / Folder: `/ (root)`
4. Click **Save**
5. Wait 1–2 minutes, then visit `https://kps871.github.io/FLWC-Training/`

---

## Activating a New Ministry

When you are ready to add a new ministry (Worship, Media, etc.):

**Step 1 — Edit `index.html`**

Find the `MINISTRIES` config array near the bottom of `index.html`:

```javascript
const MINISTRIES = [
  {
    id:     'sound-tech',
    name:   'Sound & Tech',
    icon:   '🎛',
    desc:   'Audio engineering, board operation...',
    path:   'sound-tech/index.html',
    active: true
  },
  { id:'ministry-2', name:'Ministry 2', icon:'', desc:'', path:'ministry-2/index.html', active:false },
  // ...
];
```

Change the next inactive ministry entry:

```javascript
{ id:'ministry-2', name:'Worship', icon:'🎵', desc:'Worship planning, song selection, and team preparation.', path:'worship/index.html', active:true },
```

**Step 2 — Create the ministry folder**

Create a `worship/` folder with an `index.html` modeled on `sound-tech/index.html`.

**Step 3 — Commit and push**

The ministry card appears automatically on the portal home.

---

## Adding Training Modules

Each training module is a self-contained HTML file. To add a new module:

1. Copy an existing module from `sound-tech/training/` as a starting point
2. Update the questions array, title, description, and navigation links
3. Add a card for it in `sound-tech/index.html`
4. The localStorage key (`const KEY = 'flwc-module-...'`) should be unique per module

---

## Adding How-To Guides

Copy `sound-tech/reference/how-to/copy-channel-preset.html` as a template.

The how-to guide template supports:
- Numbered step flow with connectors
- Step descriptions, action boxes, notes, and warnings
- Print stylesheet baked in — one click to print
- Breadcrumb navigation back through the hierarchy

---

## Adding Reference Pages

Copy `sound-tech/reference/eq-troubleshoot.html` as a starting point.

All reference pages include:
- Dark screen version for use at the board
- Full print stylesheet — `window.print()` button in the header
- Consistent navigation and breadcrumbs

---

## Printing Reference Pages

Every reference page has a **Print This Page** button. When printing:

- Browser navigation and dark backgrounds are hidden
- Tables, cards, and text reformat for letter-size paper
- Color coding is adapted for print (light backgrounds, dark text)
- Page margins are set to 0.75 inches

For best print results: Chrome or Edge → Print → set to Letter, color, default margins.

---

## Progress Tracking

Module quiz scores are saved to `localStorage` under keys like `flwc-module-x32-anatomy`. No server required — scores persist in the browser between sessions.

When user accounts are added in the future, this localStorage data is designed to migrate directly to a database without structural changes.

---

## Technology

- Pure HTML, CSS, and vanilla JavaScript — no frameworks, no build step
- No server required — works on GitHub Pages, any static host, or opened directly from disk
- All quiz modules self-contained — no external API calls
- Interactive anatomy modules use CSS percentage-based zone positioning — responsive at any screen size

---

## Contacts

**Tech Director / Portal Admin:** Keith  
**GitHub:** `https://github.com/kps871/FLWC-Training`  
**Live Site:** `https://kps871.github.io/FLWC-Training/`
