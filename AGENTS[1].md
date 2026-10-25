# Agent rules

1. Treat `SPEC.md` as the source of truth; do not silently add a backend, real clinical data, or unsupported claims.
2. Use Vite + React + TypeScript, plain CSS, React Router, `qrcode`, and Vitest. Keep the app modular.
3. Never touch an unrelated repo or project. Work only in `sudarshan237/waitwise-hackcache26` for release.
4. Use fictional data and alias-only registration. Do not ask for phone numbers, Aadhaar/ABHA, symptoms, or real medical records.
5. Emergency route stays available globally and before registration. No diagnosis/triage; do not imply the app contacts responders or staff automatically.
6. Label queues, estimated waits, maps, doctor status, alerts and sample values SIMULATED. Every estimate is “about” and rounded up to a 5-minute increment.
7. Demo PIN 2468 is bypassable client-side gating. State that real deployments need server-side auth, authorization, and audit logs.
8. Keep keyboard focus, semantic labels, >=18px base body text where practical, >=48px targets, contrast, reduced-motion support, and 360px mobile layout. Hindi/Tamil/Kannada text must wrap.
9. Do not tell-read-aloud controls are supported if no voice exists; only show local camera scanning where supported.
10. After changes, run `npm run build`, `npm test`, test every deep link, then review the diff. Fix causes; do not weaken tests to make them pass.
11. Never fabricate a test, deployment, URL, metric, interview, partnership or user outcome. Call out blockers plainly.
12. Keep unused features out. No PWA/offline promises, cross-device sync, production auth, real SMS/push or real hospital integrations.
