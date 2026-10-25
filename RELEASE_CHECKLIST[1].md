# WaitWise release checklist

## Code
- [ ] `npm install` completes with no dependency or lockfile errors.
- [ ] `npm run build` passes TypeScript and Vite build.
- [ ] `npm test` passes queue transition, wait formula, route connectivity/step-free, and locale parity suites.
- [ ] Open each route directly and refresh: `/`, `/register`, `/patient`, `/wayfinder`, `/emergency`, `/staff`, `/counter`, `/board`, `/about`.
- [ ] At 360px, no page-level horizontal overflow; long Hindi/Tamil/Kannada strings wrap.
- [ ] Tab sync tested in three tabs in the same browser; do not claim cross-device sync.
- [ ] Reset Demo confirmation works; Judge Demo clears flags, creates one synthetic flag and sets A-112 to exactly 3 ahead.
- [ ] QR and slip downloads work; camera scan is shown only when supported and permitted.
- [ ] Emergency panel, 112/108 links and “no token needed” guidance visible throughout.

## Hosting
- [ ] Source repo is public and root contains readable source or a source archive with clear run instructions.
- [ ] Render static or Netlify deploy succeeds; publish directory `dist`.
- [ ] Production page opens in private/incognito session without account sign-in.
- [ ] `/staff`, `/board`, `/wayfinder`, `/patient` direct URLs/refresh return the app rather than 404.
- [ ] Live URL checked on phone and laptop; no console errors or missing assets.
- [ ] Do not publish until the deployment you intend judges to see has been verified.

## Submission assets
- [ ] Public GitHub URL.
- [ ] Public live demo URL.
- [ ] Pitch deck in PDF/PPTX and any required short description.
- [ ] Up-to-5-minute demo video showing patient, staff and board screens.
- [ ] No fabricated metrics, user tests, partnerships or production claims.
