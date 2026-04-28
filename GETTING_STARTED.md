# Getting Started — ViperCoin.io Website

Step-by-step guide for contributors working with Claude in VS Code.

---

## Prerequisites

Install the following once, then you're set for all future sessions:

1. **[VS Code](https://code.visualstudio.com/)** — the editor
2. **[Git](https://git-scm.com/downloads)** — for cloning and version control
3. **Claude Code extension for VS Code**
   - Open VS Code → Extensions (Ctrl+Shift+X)
   - Search for **Claude Code** (by Anthropic)
   - Click Install
   - Sign in with your Anthropic account when prompted
4. **Live Server extension** (optional but recommended for previewing the site)
   - Search for **Live Server** (by Ritwick Dey) → Install

---

## Step 1 — Clone the Repository

Open a terminal (VS Code terminal works: Ctrl+`) and run:

```bash
git clone https://github.com/ViperCoinADA/vipercoinio-website.git
cd vipercoinio-website
```

---

## Step 2 — Open in VS Code

```bash
code .
```

Or: File → Open Folder → select the `vipercoinio-website` folder.

---

## Step 3 — Add the Meme Images (Optional)

The meme gallery requires a `Viper Memes/` folder in the same directory as `Website v2.html`.

This folder is too large for GitHub (~469 MB, 562 images). Get it from the team (ask in Discord or obtain from the project owner).

Place it here:
```
vipercoinio-website/
└── Viper Memes/         ← add this folder here
    ├── Viper_Meme_0001.jpg
    ├── Viper_Meme_0002.jpg
    └── ...
```

The rest of the site (all 6 other pages) works perfectly without this folder.

---

## Step 4 — Open Claude Code

In VS Code, open Claude Code via the sidebar icon or:
- **Mac:** Cmd+Esc
- **Windows:** Ctrl+Esc

---

## Step 5 — Start Your Session with This Message

**Copy and paste this to Claude at the start of every session:**

```
I'm working on the ViperCoin.io website. Please start by:
1. Reading CLAUDE.md for project instructions
2. Reading CHANGELOG.md to see the most recent changes

The main file is `Website v2.html`. Once you've read those files, let me know you're ready and I'll tell you what to work on today.
```

Claude will read both files and confirm it understands the project before touching anything.

---

## Step 6 — Make Your Changes

Just describe what you want in plain English. Examples:

> "Update the holder count on the home page from 1,540+ to 1,750+"

> "Add a new team member to the About Us page — name: SnakeLord, role: Developer. Use the same style as the other team cards."

> "Change the hero section background colour to a very dark navy instead of pure black"

> "The Lore section needs real content — here's the text: [paste your lore text]"

Claude will edit `Website v2.html` and update `CHANGELOG.md` automatically.

---

## Step 7 — Preview Your Changes

**Option A — Direct browser:**
Right-click `Website v2.html` in VS Code → Open with → your browser

**Option B — Live Server (auto-refreshes):**
Right-click `Website v2.html` → "Open with Live Server"

---

## Step 8 — Save Your Work to GitHub

After reviewing the changes:

```bash
git add .
git commit -m "Brief description of what changed"
git push
```

Or use VS Code's Source Control panel (Ctrl+Shift+G) for a visual interface.

---

## Tips

- **One thing at a time** — tell Claude one task per message for cleaner results
- **Be specific** — "make the button bigger" is less useful than "increase the CTA button font size from 16px to 20px"
- **Check CHANGELOG.md** — if Claude forgot to update it, just ask: "Please update CHANGELOG.md with what you just changed"
- **Undo** — if Claude makes a mistake, use Ctrl+Z in VS Code or ask Claude to revert the change
- **Never edit v3** — `Website v3.html` is an old standalone export and is not in this repo; ignore it

---

## File Reference

| File | Purpose |
|------|---------|
| `Website v2.html` | The entire website — edit this |
| `assets/` | Logos, GIFs, fonts |
| `Images/` | NFT art, team photos, social icons |
| `Branding Assets/` | SVGs, PNGs, brand kit (reference only) |
| `CLAUDE.md` | Instructions Claude reads to understand the project |
| `CHANGELOG.md` | History of all changes |
| `README.md` | Project overview |
| `GETTING_STARTED.md` | This file |
