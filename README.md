# Intoxify

A Spotify playlist generator that runs entirely in your browser. Pick up to 5 artists or tracks, tune the mix, and save it to your Spotify account.

There is no backend and no build step. It is one static page (`index.html`) that talks directly to the Spotify Web API using **your own** Spotify app Client ID.

## Set up your Spotify app

1. Go to the [Spotify developer dashboard](https://developer.spotify.com/dashboard) and create an app.
2. Add a **Redirect URI** (see below for which one). It must match exactly, including the trailing slash.
3. Copy the app's **Client ID** (you do not need the client secret).
4. If you want other people to use your app, add them under **User Management**. In development mode only the owner and allowlisted users can log in, and the app owner needs Spotify Premium.

## Run it on GitHub Pages

1. Push this repo to GitHub.
2. Open **Settings → Pages**, set the source to **Deploy from a branch**, and pick `main` and `/ (root)`.
3. Your site will be at `https://<your-username>.github.io/<repo-name>/`.
4. Add that exact URL (with the trailing slash) as a Redirect URI in your Spotify app.
5. Open the site, paste your Client ID, and click **Connect Spotify**.

## Run it locally

Spotify login does not work from a `file://` page. Serve the folder instead:

```bash
python3 -m http.server 8888
```

Then open `http://127.0.0.1:8888/` and add `http://127.0.0.1:8888/` as a Redirect URI in your Spotify app. Use `127.0.0.1`, not `localhost`, because Spotify requires the loopback IP for plain http.

## How it works

- Login uses Spotify's PKCE flow, so no secret is ever stored. Your Client ID and tokens stay in your browser's `localStorage`.
- Seeds are found with Spotify search. The mix blends the seed artists' tracks with genre searches based on your seeds' genres.
- Playback uses Spotify's embedded player.
- Spotify no longer gives development-mode apps recommendations, related artists or audio features, so discovery is genre-based rather than true similarity.
- "Save to Spotify" creates a private playlist in your account. Spotify's development-mode rules have changed several times, so this can fail depending on your app's status.

## Notes

- Never commit a client secret. This app does not need one.
- Add a `LICENSE` file if you want others to be able to reuse the code. Without one, the default is all rights reserved.
