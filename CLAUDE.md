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

## NEVER PUSH UNLESS EXPLICITLY ASKED
- **Do not `git push` unless the user asks for it in that message.** Push = live on a
  public site, and it is the user's site, not yours. There is no standing permission.
- This applies even though the key is passphrase-free and the push would "just work".
  Being able to push unattended is not the same as being allowed to.
- Committing locally is fine. Pushing is the user's call, every time.
- Same for anything else outward-facing. Ask, wait for a clear yes, then act.

## Standard workflow for edits
1. Make the edit to the relevant `.html` file.
2. Test it — actually drive the thing and verify it does what it should.
3. Let the user listen / look before calling it done. They are the ear on audio tools.
4. `git add -A && git commit -m "..."` — commit locally.
5. **Stop.** Ask before pushing. Only `git push` once the user says so.

## Pages / structure
- Entry: `index.html`. Other pages: `home.html`, `about.html`, `games.html`, `itch.html`.
- Audio tools: `sweep-generator.html`, `noise-generator.html`, `mls-generator.html`,
  `shot-forge.html`, `babel.html`, `click-factory.html`.
- Shared files under `assets/` and `images/`.
