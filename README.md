# ashburn-studios.com

Static site for Ashburn Studios. One page, no build step: `index.html` plus `assets/`.
Hosted on GitHub Pages; the domain is registered at Squarespace and points here.

## Editing

- Copy and layout live in `index.html`. Colors and fonts are the `:root` tokens at the top of the `<style>` block.
- Key art comes from the Plant-Game repo (`Assets/Art/`). Screenshots and the three gameplay loops
  (`assets/screens/`, `assets/video/`) were pulled from the Steam store page; replace them whenever the
  store assets change.
- Steam links: full game app `5393120`, demo app `5393170`.

Open `index.html` in a browser to preview. Nothing needs installing.

## Publishing (first time)

1. In GitHub Desktop: File > Add local repository, pick this folder, then Publish repository.
   Name it `ashburn-studios`, uncheck "Keep this code private" (Pages on a free account needs a public repo),
   and push.
2. On github.com open the repo > Settings > Pages. Under "Build and deployment" set Source to
   "Deploy from a branch", branch `main`, folder `/ (root)`. Save.
3. On the same Pages screen, under "Custom domain", enter `ashburn-studios.com` and save. GitHub will
   check DNS (step 4) and offer "Enforce HTTPS" once the records resolve. Tick it.
   The `CNAME` file in this repo keeps that setting from being lost on later pushes.

## Squarespace DNS

Squarespace > Domains > ashburn-studios.com > DNS settings. Delete any default Squarespace A records on
the root (they point at Squarespace's own hosting), then add:

| Type  | Host | Value                  |
|-------|------|------------------------|
| A     | @    | 185.199.108.153        |
| A     | @    | 185.199.109.153        |
| A     | @    | 185.199.110.153        |
| A     | @    | 185.199.111.153        |
| CNAME | www  | char279.github.io      |

DNS can take up to an hour to propagate. Check with:

```
nslookup ashburn-studios.com
```

It should return the four 185.199.x.153 addresses. Then go back to GitHub Pages settings and
tick "Enforce HTTPS".

## Later updates

Edit, commit, push `main`. GitHub Pages redeploys in about a minute.
