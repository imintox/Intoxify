# Intoxify

A Spotify playlist generator that runs entirely in your browser. Pick up to 5 artists or tracks, tune the mix, and save it to your Spotify account.

There is no backend and no build step. It is one static page (`index.html`) that talks directly to the Spotify Web API using **your own** Spotify app Client ID.

## Set up your Spotify app

1. Go to the [Spotify developer dashboard](https://developer.spotify.com/dashboard) and create an app.
2. Add a **Redirect URI** (see below for which one). It must match exactly, including the trailing slash.
3. Copy the app's **Client ID** (you do not need the client secret).
4. If you want other people to use your app, add them under **User Management**. In development mode only the owner and allowlisted users can log in, and the app owner needs Spotify Premium.
## Notes

- Never commit a client secret. This app does not need one.

