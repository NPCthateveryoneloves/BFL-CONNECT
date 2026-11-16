# BFL Connect

A fan site for Bangladeshi football. `index.html` reads `data.json` and re-checks it every 5 minutes. A free scheduled job refreshes `data.json` from public sources, so the site keeps itself current.

## Put it online for free (about 5 minutes)

1. Create a free GitHub account and a new **public** repository, for example `bfl-connect`.
2. Upload everything in this folder, including the hidden `.github` folder (drag the whole folder into the GitHub upload page).
3. In the repository go to **Settings → Pages**, set Source to **Deploy from a branch**, branch **main**, folder **/ (root)**, and save.
4. Your site appears at `https://YOUR-NAME.github.io/bfl-connect/` within a minute or two.
5. Go to **Actions → Update data → Run workflow** once to check the updater. After that it runs every 30 minutes by itself.

Netlify Drop (app.netlify.com/drop) also hosts the folder for free, but only GitHub gives you the automatic refresh.

## How the updating works

- `scripts/update.py` reads the league table from the newest season page on Wikipedia that has matches played. If the new season has no matches yet, it keeps the previous season's final table.
- It also pulls recent headlines from a Google News search feed.
- If a source is down or changes layout, the old data stays in place and the site keeps working.
- `index.html` fetches `data.json` on load, every 5 minutes, and when the tab becomes visible again.

## Limits to know about

- Standings and headlines update automatically. Live scores and fixture lists do not, because free public sources for them need an API key or have terms that forbid copying. The Match centre shows the leaders until you add matches to the `matches` list in `data.json` (`home`, `away`, `hs`, `as`, `status`, `date`, `comp`).
- Wikipedia is edited by volunteers, so the table can trail official results by hours or days.
- The community button and the fan poll are placeholders. Connect a form or forum link to the button when you are ready.
