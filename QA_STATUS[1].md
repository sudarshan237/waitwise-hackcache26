# WaitWise QA / release status — 25 October 2026

## Latest changes
- Team is shown consistently as **Sudarshan**; lead **Sudarshan A. Patil**; members **Shubham and Pruthviraj**.
- Registration form state clears after creating a token. A fresh registration begins with an empty alias and the default department; only the newly created token is opened.
- Opening `/patient` without a token now shows token lookup rather than silently restoring the previous selection; the lookup field also clears when `?token` is removed. Explicit `?token=...` links select only the matching queue entry. Global urgent-help flags use `NO-TOKEN` unless a valid token is explicitly open on the patient route, avoiding attribution to an earlier selection.
- Token allocation checks the existing queue case-insensitively, so a stale counter cannot produce duplicate tokens.
- The eight-slide pitch deck has been rendered to PNGs and visually checked. Page footer and slide numbers are separated on slides 2–8; the cover is intentionally unnumbered. The wait formula fits its box.

## Checks completed
- TypeScript parser: all source and test files were parsed; no syntax diagnostics.
- Locale dictionaries are checked against English for key parity in the included Vitest suite; all four locale dictionaries include English, Hindi, Tamil and Kannada.
- Route graph static test covers all supported non-stair origin/destination pairs with Avoid Stairs enabled; it must return zero stair edges.
- Queue transition, wait estimate, locale coverage, token allocation and explicit-token selection tests are included.
- ZIP integrity and file manifest must be verified again for the final download bundles.

## Not verified — do not overclaim
- `npm install` timed out in this environment because the external registry did not finish downloading. Thus a dependency-backed `npm run build` and the full `npm test` suite have **not** completed here.
- No browser-level smoke test of the newest React build was completed.
- GitHub write permissions were rejected by the connected integration. The upgraded source is not pushed to GitHub and the new build is not deployed.
- `https://mellifluous-klepon-602121.netlify.app` still serves the older standalone prototype until the upgraded source is committed and deployed.

## Release gate
Upload the contents of the source ZIP to the ROOT of `sudarshan237/waitwise-hackcache26`, wait for a successful Render Static Site or Netlify build, and open the resulting public URL in a private browser window on phone and laptop. Refresh `/staff`, `/board`, `/wayfinder`, and `/patient`. Only then call that URL production-verified.

## Safety and persistence
All patient names, queues, doctors, wait estimates, notices and maps are fictional/simulated. `2468` is a bypassable demo gate. Draft registration values are not stored. Registered fictional queue entries intentionally remain in the queue so staff and board screens can demonstrate multiple arrivals; the new registration form and no-token patient lookup do not reuse previous form state.
