# Rose of Leary Timer

A tiny static site that shows how long it has been since anyone at school mentioned the Rose of Leary.

- **Public page:** `index.html` shows only the elapsed time. It reloads `data.json` every minute.
- **Admin page:** `admin.html` lets you log a mention ("It was just mentioned"), backdate one, add notes, undo, and remove entries.
- **Data:** `data.json` holds the mentions log. The timer counts from the newest entry.

## How saving works

The site is hosted on GitHub Pages, which only serves static files. The admin page saves by committing a new `data.json` through the GitHub API, using a fine-grained access token that you paste into the admin page once. The token stays in that browser's local storage. After a save, GitHub Pages redeploys and the public timer picks up the change within about a minute.

### Creating the token

1. Go to <https://github.com/settings/personal-access-tokens/new>.
2. Name it `Rose of Leary admin` and choose an expiration.
3. Repository access: **Only select repositories** → this repository.
4. Permissions → Repository permissions → **Contents: Read and write**.
5. Generate it and paste it into the admin page under "Connection to GitHub".

When the token expires, make a new one and paste it in again.

### Without the admin page

You can also edit `data.json` directly on github.com: add an entry at the top of `history` and set `lastMentioned` to the same time (ISO format, e.g. `2026-10-28T13:53:00.000Z`).
