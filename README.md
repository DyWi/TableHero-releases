# TableHero — macOS releases

Built releases of the TableHero desktop app. **No source code lives here.**

This repository exists for one reason: the app's built-in updater fetches its
manifest and archive over plain HTTP with no credentials. Release assets on a
private repository require authentication, so the updater would get a `404`
and quietly report "up to date" forever. A public repository holding only the
build is the simplest way to give it something it can actually read.

The alternative was embedding a GitHub token in the app, which puts a
credential inside a binary that gets handed out.

Nothing here is secret. The app's interface is the same bundle already served
at [app.tablehero.games](https://app.tablehero.games), including its
publishable Supabase key, which is designed to be public and is protected by
row-level security. You still need an account to use the app.

## Contents of each release

| File | What it is |
|---|---|
| `TableHero.app.tar.gz` | The application |
| `TableHero.app.tar.gz.sig` | Signature the updater verifies before installing |
| `latest.json` | Manifest the updater reads |

Updates are signed. A build that does not verify against the public key
compiled into the app is refused, so being able to answer this URL is not
enough to install anything.

## Status

Early. Signed with a development certificate, not a distribution one — macOS
will warn on a copy downloaded from here, and it is not notarized or on the
App Store yet.
