# Chase's Halloween Heat

Single-file Three.js parody game: part haunted open world, part family roast, part Halloween chase movie.

## What is in this repo

- `index.html` is the entire playable game.
- `.github/workflows/static.yml` deploys the repo to GitHub Pages.
- `.nojekyll` tells GitHub Pages to serve the files directly instead of trying to run a Jekyll build.
- `404.html` redirects missing project URLs back to the game.

## Current game loop

1. Collect 6 loot stashes around the neighborhood.
2. Reach the ritual beacon.
3. Return to the safehouse before No-Face finishes the chase.

Optional strategy systems:

- Streetlamps lower fear and can slowly heal you.
- Eggs stun No-Face.
- Loot stashes now read as cash bags and snack bundles instead of glowing orange pickups.
- Costume Crypt is walk-in and lets Chase swap Halloween costumes.
- A procedural spooky background music loop starts when the run begins.
- Shops still handle egg, sprint, and stun upgrades.

## Controls

- `WASD` move
- `Shift` sprint
- `Left click` or `Space` throw egg
- `Right drag` orbit camera
- `E` interact with stores, beacon, and safehouse
- `R` restart after win or loss

## Local test

From the repo folder:

```powershell
py -3.11 -m http.server 8000
```

Then open:

```text
http://127.0.0.1:8000/
```

## GitHub Pages

Primary game URL:

```text
https://dacameragirl.github.io/Chases_Parody_GTA_Haunt/
```

If that still shows `404`, check this in GitHub:

1. Open `Settings -> Pages`.
2. Confirm the site source is either:
   `Deploy from a branch` with branch `main` and folder `/root`, or
   `GitHub Actions` using `.github/workflows/static.yml`.
3. If it is still on legacy branch deploy and keeps failing, switch it to `GitHub Actions`.
4. Wait for the latest deployment to finish, then reload the URL above.

## Why the old version felt broken

The earlier prototype had three main problems:

- text encoding was corrupted
- controls depended too much on pointer lock
- visuals were being pushed before the game loop was stable

This pass fixes those first, then adds atmosphere and mission structure on top.
