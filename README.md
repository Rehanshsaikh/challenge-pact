# Pact

A challenge tracker for two people. One HTML page, one JSON file, no server.

- **Home** — every challenge, both streaks, and a *Mark today done* button.
- **A challenge** — day-by-day grid for each of you, hours logged, progress.
- Add, log, undo, delete. Everything is stored in `data.json` in this repo.

```
index.html   the whole app
data.json    the whole database
```

## Put it on GitHub

Using the account **rshaikh0530@gmail.com**.

```bash
cd /Users/rehanshaikh/PROJECTS/challenge-pact
git init
git add index.html data.json README.md .gitignore
git commit -m "Pact"
git branch -M main
git remote add origin https://github.com/<your-username>/challenge-pact.git
git push -u origin main
```

Then on GitHub: **Settings → Pages → Source: `main`, folder `/ (root)` → Save.**

A minute later it's live at `https://<your-username>.github.io/challenge-pact/`.
Open that link on any phone, any computer — that's the app.

## Let it save

Reading needs nothing. **Saving needs a token**, because GitHub does not accept a
change to a repo from an anonymous visitor — that is GitHub's rule, not a setting
we can turn off. So make **one** token and use the **same one** on both phones.

1. <https://github.com/settings/personal-access-tokens/new>
2. Repository access → **Only select repositories** → `challenge-pact`
3. Permissions → Repository → **Contents** → **Read and write**
4. Generate, copy.
5. Open the app → **Sync** at the bottom → paste → **Connect**.
6. Send her the same token; she does step 5 on her phone.

The token lives in each browser's local storage and only ever goes to GitHub.
It is not in the repo — GitHub auto-revokes tokens that get committed, which is
why it can't be baked into the page.

Once connected, every change is a commit to `data.json`. Her screen picks up
your changes within about 15 seconds.

## Worth knowing

- **A GitHub Pages repo is public.** Anyone who finds the URL can read
  `data.json` — your names, challenge titles, hours. Nobody can change it
  without the token. If that's not okay, don't use Pages: just open
  `index.html` from your own machine, where it stores in the browser instead.
- **No token is fine too.** The app works with everything kept in that one
  browser. The footer tells you which mode you're in.
- **If you both log at the same moment, nothing is lost.** Each change is sent
  as "add this entry" rather than as a whole file, and a save re-reads the
  file and replays the change on top, retrying if GitHub says someone got
  there first.
- **Backup** at the bottom downloads the JSON, any time.
- `index.legacy.html` is the original single-file version, kept for reference.
