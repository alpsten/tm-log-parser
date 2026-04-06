# Terraforming Mars — Game Log Parser

A client-side web app that extracts every card played from a Terraforming Mars game log and presents it as a sortable table with CSV export.

**Live app:** https://alpsten.github.io/tm-log-parser

## Features

- Paste a raw game log and instantly see every card played, in order
- Automatic repair of encoding issues (garbled UTF-8/Windows-1252 names)
- Medal emoji stripped from player names automatically
- **Player name aliases** — map in-game nicknames to real names (e.g. `Daddy Cool` → `Emil Alpsten`), saved in the browser between sessions
- Sortable table (click any column header)
- Export results as a `.csv` file
- Runs entirely in the browser — no server, no data sent anywhere

## How to use

1. Open your Terraforming Mars game and copy the full game log
2. Paste it into the input field
3. Click **Parse Log**
4. Optionally add player name aliases in the aliases panel
5. Click **Export CSV** to download the results

## Deployment

This is a single `index.html` file with no dependencies or build step.

To host on GitHub Pages:

```bash
git init
git add index.html
git commit -m "feat: initial TM log parser"
gh repo create tm-log-parser --public --source=. --remote=origin --push
gh api repos/$(gh api user --jq .login)/tm-log-parser/pages \
  --method POST \
  -f source='{"branch":"main","path":"/"}'
```

The app will be live at `https://alpsten.github.io/tm-log-parser` within ~30 seconds.

## TODO

- Card Type column (Green/Blue/Red/Corporation/Prelude)
- Filter table by player
- Generation column
