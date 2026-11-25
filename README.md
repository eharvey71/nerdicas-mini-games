# Nerdica's mini-games

A static site for Firebase Hosting. No build step.

```
firebase.json            hosting config
public/
  index.html             landing page (the list of games)
  404.html               not-found page
  hollowdeep/index.html  Hollowdeep, a wireframe dungeon crawl
  regolith/index.html    Regolith, a vector moon lander
  marchlands/index.html  Marchlands, a turn-based territory war
  skerry/index.html      Skerry, a tiny top-down island quest
  farlane/index.html     Farlane, a space trading run with wireframe combat and docking
  underdeck/index.html   Underdeck, a first-person maze shooter (work in progress)
  cryptward/index.html   Cryptward, a dungeon board game (work in progress)
  stoppress/index.html   Stop the Press, a point-and-click adventure (work in progress)
```

## Deploy

1. Install the CLI if needed: `npm install -g firebase-tools`
2. Sign in: `firebase login`
3. From this folder, publish: `firebase deploy --only hosting`

The project is set in `.firebaserc` (`nerdicas-mini-games`), so the site is served at
`https://nerdicas-mini-games.web.app`.

To look before publishing: `firebase emulators:start --only hosting`,
or a preview channel: `firebase hosting:channel:deploy preview`.

## Add a game

1. Put the game in its own folder under `public/`, with its page named `index.html`.
2. Add an entry to the `GAMES` list near the top of the script in `public/index.html`:
   `slug` is the folder name; `title`, `blurb` and `tags` are the card text;
   `art` is an optional function that draws the 280x192 1-bit preview.
3. Deploy again.

## Notes

- Saves are kept in the browser, per site address. A delver from another address
  comes across with a save code: SAVE CODE at the Inn, ENTER CODE on the title screen.
- TONE (green, amber or white) is one setting for the whole site, stored in the browser as `nmg.tone`.
  The landing page and every game have a TONE key and read the same value.
- A custom domain is added in the Firebase console under Hosting.
