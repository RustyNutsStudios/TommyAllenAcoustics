# SWAP-READY — COMING TO FAB → GET THE PLUGIN (Shot Forge + Sci Forge)

*WEBSITE, 21 Aug 2026. Prepared so review-clearance day is a five-minute commit.*
*NOT APPLIED — there is no listing URL until Fab approves. Apply per product, on its own day.*

## What changes (per page, three lines, nothing else)

The pattern is `unreal-click-factory.html`, which is already live with a real
listing. Each Forge page has the same three spots:

| Line | Now (placeholder) | Becomes (live) |
|---|---|---|
| 83 | `<span class="soon">⏳ COMING TO FAB …</span>` (top CTA) | `<a class="buy" href="URL" …>★ GET THE PLUGIN …</a>` |
| 151 | `…link on the Fab listing &mdash;` (SUPPORT box, plain text) | `…link on the <a href="URL" …>Fab listing</a> &mdash;` |
| 157 | `<span class="soon">⏳ COMING TO FAB …</span>` (bottom CTA) | same as line 83 |

Line numbers are identical in `unreal-shot-forge.html` and `unreal-sci-forge.html`
(both 167 lines as of commit 116bcfb). If either file has been edited since,
search for the strings instead — they are unique.

### Exact before → after

**Lines 83 and 157** — replace the whole `<span class="soon">…</span>`:

```html
    <span class="soon">&#9203; COMING TO FAB<span class="small">the Unreal plugin is in review</span></span>
```
→
```html
    <a class="buy" href="URL" target="_blank" rel="noopener">&#9733; GET THE PLUGIN<span class="small">on Fab &mdash; the full Unreal version</span></a>
```

**Line 151** — wrap the two words `Fab listing` in an anchor:

```html
      <p>Questions, bug reports and feature requests go through the <b>Support</b> link on the Fab listing &mdash; that reaches me directly, and I answer.</p>
```
→
```html
      <p>Questions, bug reports and feature requests go through the <b>Support</b> link on the <a href="URL" target="_blank" rel="noopener">Fab listing</a> &mdash; that reaches me directly, and I answer.</p>
```

`URL` = the product's Fab listing, `https://www.fab.com/listings/<id>` — the
URL RELEASE reports when the listing goes public. The `.cta .soon` CSS rule
stays; it is harmless and Variation Bench uses it.

## The five-minute version (Git Bash, one product at a time)

Tested 21 Aug 2026 on scratch copies of both pages with a dummy URL: exactly
3 lines change per file, `COMING TO FAB` count goes 2 → 0, URL count 0 → 3,
and the resulting CTA markup is byte-identical to Click Factory's.

```bash
cd /c/Users/tgall/Documents/TommyAllenAcoustics
URL='https://www.fab.com/listings/PASTE-THE-LISTING-ID-HERE'
FILE=unreal-shot-forge.html        # or unreal-sci-forge.html
sed -i \
  -e "s|<span class=\"soon\">&#9203; COMING TO FAB<span class=\"small\">the Unreal plugin is in review</span></span>|<a class=\"buy\" href=\"$URL\" target=\"_blank\" rel=\"noopener\">\&#9733; GET THE PLUGIN<span class=\"small\">on Fab \&mdash; the full Unreal version</span></a>|" \
  -e "s|link on the Fab listing &mdash;|link on the <a href=\"$URL\" target=\"_blank\" rel=\"noopener\">Fab listing</a> \&mdash;|" \
  "$FILE"
grep -c "COMING TO FAB" "$FILE"    # expect 0
grep -c "$URL" "$FILE"             # expect 3
git diff --stat                    # expect: 1 file changed, 3 insertions(+), 3 deletions(-)
```

Then: open the file in a browser, click all three links (new tab, lands on the
listing), and

```bash
git add unreal-shot-forge.html && git commit -m "Shot Forge is on Fab — swap COMING TO FAB for the listing"
```

**STOP. Do not push.** Push only when Tommy says push, in that message (PUSH
LAW, CLAUDE.md). After Tommy's push: fetch the live page, confirm the listing
URL appears 3 times and `COMING TO FAB` 0 times, and that the listing link
itself returns 200 cold (no Epic login).

## Optional, Director's call — the hub card

`home.html` line 107 (Shot) / 108 (Sci) carry the card text `Gunfire, built in
the editor` / `Plasma, rails, beams, cryo`. Click Factory's card (line 109)
reads `UI sounds &mdash; on Fab now`. Leaving the Forge cards as they are is
fine — the copy is good and the hub order is locked. If the Director wants
the "on Fab now" tell on the hub too, it is one `card-desc` edit per line,
same commit.

## Checklist for the day

- [ ] RELEASE has reported the public listing URL (not the seller-dashboard URL)
- [ ] Open the URL in a private window — it loads without login
- [ ] Run the block above for THAT product only
- [ ] 3 / 0 / 3 counts as expected, `git diff` shows 3 lines
- [ ] Local open, three links clicked
- [ ] Commit. Stop. Report the hash to the Director. Push = Tommy's word.
- [ ] If the second product clears later, repeat — they are independent

---

**Note (WEBSITE, 21 Aug 2026):** the whole repo deploys to GitHub Pages, so
this file becomes publicly readable at `/SWAP-READY.md` the next time Tommy
pushes anything. It holds no keys and no unpublished facts (both pages already
say the plugin is in review), so it is committed tracked — the resume contract
wants it in git next to the files it edits. If Tommy would rather it stayed
off the public site, one line does it: add `SWAP-READY.md` to `.gitignore`
alongside `GIT-PUSH-HANDOFF.md`.
