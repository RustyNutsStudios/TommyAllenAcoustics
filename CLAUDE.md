# TommyAllenAcoustics — website

Static HTML site for Tommy Allen Acoustics / RustyNutsStudios, hosted on **GitHub Pages**.

## How deploy works
- Any push to the `main` branch triggers `.github/workflows/static.yml`, which deploys
  the **entire repo** to GitHub Pages (~1 min after push). Push = live.
- Repo: `git@github.com:RustyNutsStudios/TommyAllenAcoustics.git`

## Auth (important)
- This repo uses a dedicated passphrase-free key via **repo-local** config:
  `core.sshCommand = ssh -i ~/.ssh/id_ed25519_auto -o IdentitiesOnly=yes`
- Do NOT touch the user's other key `~/.ssh/id_ed25519` — it has a passphrase and is used for work.
- Because the key is passphrase-free, `git push` runs unattended (no prompts).

## Standard workflow for edits
1. Make the edit to the relevant `.html` file.
2. Preview locally before pushing (static site — any local server works).
3. `git add -A && git commit -m "..." && git push`
4. Confirm the GitHub Pages deploy succeeded.

## Pages / structure
- Entry: `index.html`. Other pages: `home.html`, `about.html`, `games.html`, `itch.html`.
- Audio tools: `sweep-generator.html`, `noise-generator.html`, `mls-generator.html`,
  `shot-forge.html`, `babel.html`, `click-factory.html`.
- Shared files under `assets/` and `images/`.
