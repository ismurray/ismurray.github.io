# ian-murray.com — personal portfolio

Personal portfolio site for Ian Murray, served at
[ian-murray.com](https://ian-murray.com) via **GitHub Pages** from this
repo's default branch. The `CNAME` file is what binds the custom domain;
DNS for `ian-murray.com` is at GoDaddy and points at GitHub's Pages IPs
(`185.199.108–111.153`).

> Originally forked from
> [RyanFitzgerald/devportfolio](https://github.com/RyanFitzgerald/devportfolio).
> The `upstream` remote still points there — **be careful with `gh pr
> create`**, which defaults to a fork's parent. Run
> `gh repo set-default ismurray/ismurray.github.io` in any fresh clone.

## Table of contents

- [Layout](#layout)
- [Local development](#local-development)
- [What is published](#what-is-published)
- [Related sites](#related-sites)

## Layout

| Path | Purpose |
|---|---|
| `index.html` | The portfolio page itself (single page) |
| `404.html` | Custom not-found page (GitHub Pages serves it automatically) |
| `arcane-ascension/` | Landing page + privacy policy for the Arcane Ascension game |
| `app-ads.txt` | AdMob authorized-sellers declaration — **must stay at the site root** |
| `css/`, `js/`, `libs/`, `images/` | Compiled/vendored front-end assets that ship with the site |
| `scss/` | Sass **source** for `css/` — not published |
| `gulpfile.js`, `package.json` | Build tooling — not published |
| `CNAME` | Binds `ian-murray.com` to this Pages site |
| `_config.yml` | Jekyll config; its only real job is the `exclude` list |

## Local development

```bash
npm install
npm run watch     # gulp: compiles scss/ -> css/ and minifies js/
```

Then open `index.html` directly, or serve the directory with
`python3 -m http.server`.

Committing compiled `css/` and `js/` is intentional — GitHub Pages does not
run the gulp build, so the compiled output has to be in the repo.

## What is published

GitHub Pages runs Jekyll and publishes **everything not excluded** by
`_config.yml`. That list is load-bearing: before it existed,
`ian-murray.com/README.md`, `/package.json` and `/gulpfile.js` were all
publicly fetchable.

If you add tooling, config, or notes to the repo root, add them to
`exclude` in `_config.yml` too. Verify with:

```bash
curl -sSI https://ian-murray.com/README.md      # expect 404
curl -sSI https://ian-murray.com/app-ads.txt    # expect 200 — AdMob crawls this
curl -sS   https://ian-murray.com/no-such-page | head -5   # expect 404.html
```

`app-ads.txt` matters: AdMob crawls the developer-website domain listed on
the Play Console and App Store Connect listings, and the file must be at
the domain root — a subdirectory does not count.

## Related sites

| Site | Repo | Host |
|---|---|---|
| [ian-murray.com](https://ian-murray.com) | this one | GitHub Pages |
| [ismurray.com](https://ismurray.com) (ismurray LLC) | `ismurray/ismurray-com` | Cloudflare Workers |
| [arcane-ascension.com](https://arcane-ascension.com) (the game) | `antiyoy_but_with_wizards` | Firebase Hosting |

The game's privacy policy is mirrored in three places (here, the LLC site,
and the game's web build). Keep them in sync when it changes.
