# Nerdica's mini-games

A static site for Firebase Hosting. No build step.

```
firebase.json            hosting config
public/
  index.html             landing page (the list of games)
  404.html               not-found page
  hollowdeep/index.html  the game
```

## Deploy

1. Install the CLI if needed: `npm install -g firebase-tools`
2. Sign in: `firebase login`
3. Pick or create a Firebase project. The project ID becomes the address,
   `https://<project-id>.web.app`, so choose it with that in mind.
   Create one in the Firebase console, or run `firebase projects:create`.
4. From this folder, link it: `firebase use --add` and choose the project.
5. Publish: `firebase deploy --only hosting`

To look before publishing: `firebase emulators:start --only hosting`,
or a preview channel: `firebase hosting:channel:deploy preview`.

## Deploy on push (GitHub Actions)

`.github/workflows/deploy.yml` deploys `main` to the live site. It is skipped
until both of these exist in the repo settings (Settings, Secrets and variables, Actions):

- Variable `FIREBASE_PROJECT_ID`: the Firebase project ID.
- Secret `FIREBASE_SERVICE_ACCOUNT`: the JSON key of a service account that can
  deploy to Hosting (Firebase console, Project settings, Service accounts,
  Generate new private key).

Alternatively run `firebase init hosting:github` in this folder. It creates the
service account and secret for you and writes its own workflow files; delete
`deploy.yml` afterwards so the site is not deployed twice.

## Add a game

1. Put the game in its own folder under `public/`, with its page named `index.html`.
2. Add an entry to the `GAMES` list near the top of the script in `public/index.html`:
   `slug` is the folder name; `title`, `blurb` and `tags` are the card text;
   `art` is an optional function that draws the 280x192 1-bit preview.
3. Deploy again.

## Notes

- Saves are kept in the browser, per site address. A delver from another address
  comes across with a save code: SAVE CODE at the Inn, ENTER CODE on the title screen.
- The landing page uses the phosphor colour last chosen with HUE in Hollowdeep.
- A custom domain is added in the Firebase console under Hosting.
