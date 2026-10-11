# Touch Grass

A single-page web app that gets people off their screens. Players take on eight small outdoor quests, send a photo as proof, and earn "blades" (points). Claude checks each photo, and enough blades unlock vouchers.

## How it works

1. Pick a quest (shoes off, tree hug, golden hour, and more).
2. Upload a photo as proof.
3. Claude judges the photo. Screenshots, photos of screens and indoor shots are rejected.
4. A pass earns blades and a "Verified" stamp.
5. Reach 30, 80 or 140 blades to claim a voucher.

## Run it

It is one static file with no build step. Open `index.html` in a browser.

The photo judge, progress saving and voucher claiming use runtime features of Claude Artifacts (`sample`, `db`, `user`). Outside Claude, the page still loads and saves progress to `localStorage`, but the judge is unavailable, so quests cannot be verified. To run it standalone, replace the `sample` call in `submit()` with a call to your own vision model endpoint.

## Project layout

| File | Purpose |
| --- | --- |
| `index.html` | The whole app: markup, styles and script |
| `README.md` | This file |

## Customize

- **Quests:** edit the `TASKS` array in `index.html`. Each quest has an `id`, `title`, `desc`, `pts` and a `need` string that tells the judge what the photo must show.
- **Vouchers:** edit the `VOUCHERS` array (`need` is the blade threshold).
- **Look:** colors and fonts are CSS variables at the top of the stylesheet, with light and dark themes.

## Notes

- Photos are sent to the judge and are not stored. Only quest completion and claimed voucher codes are saved.
- Voucher codes are generated in the browser and are demo codes. Connect real sponsor codes before launch.
