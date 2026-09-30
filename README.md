# bluebeauty

The public web address of the Garmin watch face **Blue Beauty Earth Analog**:

| Page | URL |
|---|---|
| Share link (redirects to the Connect IQ Store) | https://leidenheit.github.io/blue-beauty-earth-analog-static/ |
| Requirements (devices, features, permissions) | https://leidenheit.github.io/blue-beauty-earth-analog-static/hardware-requirements.html |
| License | https://leidenheit.github.io/blue-beauty-earth-analog-static/license.html |

The watch face ships the first address: as the share link in its phone
settings and as the QR code in its on-watch menu. The Store entry's
description links to the requirements page.

## Why a redirect

Garmin assigns the store page's id when an entry is first uploaded, and the
beta and the release are separate entries. So the release page's address cannot
be known before the release upload, and the beta page is visible only to the
account that uploaded it. The face therefore links here, and only the target of
this redirect changes.

## The one setting: `store_url` in `_config.yml`

| Phase | `store_url` | What `/bluebeauty/` does |
|---|---|---|
| Beta test | the beta entry's page | forwards there (only the uploading account can open it) |
| Garmin review | `""` (empty) | shows a landing page: picture, name, "coming soon", links |
| Released | the release entry's page, from the developer dashboard | forwards there |

During the review the page must not forward to the beta page: Garmin's review
guidelines ask for "no broken links", and the reviewer cannot open the beta.

Edit the line, commit and push. GitHub Pages rebuilds within about a minute. A
new watch package is never needed for this.

## Rules

- **The address never changes.** An installed watch face keeps the share link
  it was installed with. Do not rename the repo, do not move the site, and keep
  the trailing slash. Without it, GitHub first redirects `/bluebeauty` to
  `/bluebeauty/`.
- **The site stays online** as long as the watch face is in the store.
- The watch table in `hardware-requirements.md` is generated. Change it in the
  watch face repo: `python tools/make_pages_devices.py` rewrites the block
  between the marker comments from `manifest.xml` and the SDK.

## Setup (once)

1. Create the **public** repo `leidenheit/bluebeauty` on GitHub. Pages is free
   only for public repos.
2. Push this repo to it: `git remote add origin https://github.com/leidenheit/bluebeauty.git`,
   then `git push -u origin main`.
3. On GitHub, open Settings > Pages and set Source to "Deploy from a branch",
   Branch `main`, folder `/ (root)`.
4. After 1-2 minutes open https://leidenheit.github.io/bluebeauty/ on the PC and
   on the phone. Both must land on the store page.

## License

The watch face and this site: GNU General Public License v3.0, see
[LICENSE](LICENSE). Copyright 2026 Attila "leidenheit" Varga.
