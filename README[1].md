# WaitWise — HackCache ’26 · Problem 2

**A clearer next step for every hospital visit.** WaitWise is a mobile-first, multilingual prototype for a fictional three-floor government hospital. It demonstrates how registration, a simulated OPD token, queue status and step-by-step directions could be clearer for older visitors, people with limited digital literacy and people who prefer regional languages.

## Demo features
- First-visit language choice in each language’s own script: English, Hindi, Tamil and Kannada.
- Three-step, alias-only registration (the form draft clears after submission; queued demo entries remain visible to the staff and board), assisted mode and speech input only where the browser supports it.
- Token slip, simulated queue position, “about N min” wait estimate, generated QR link, downloadable QR/slip and print/PDF.
- My Turn, manual token lookup and camera QR scanning only where the browser supports `BarcodeDetector` and camera permission.
- Always-visible Emergency access: warning signs, no-token guidance, Casualty route, and `tel:112` / `tel:108` links.
- Dijkstra route finder over an illustrative SVG hospital map, with Avoid Stairs, landmark directions, and Help Desk fallback.
- Staff console with demo PIN `2468`, calls, start/complete, hold/return, no-show/requeue, send-to-end, move-department, doctor status, pinned urgent flags, crowding markers and demo/reset controls.
- Waiting-room board with current token and next three per department; spoken announcements when a matching voice is available.
- Registration counter, three text-size levels, high contrast, reduced motion, assisted mode, optional browser notifications and a settings screen.

## Run locally
Requires Node.js 20+.

```bash
npm install
npm run dev
```

In another terminal:

```bash
npm test
npm run build
npm run preview
```


## Deploy on Netlify (Git-connected)

Connect the repository root to Netlify. The included `netlify.toml` sets the build command to `npm run build` and the publish directory to `dist`; leave the base directory blank. Netlify must install the package dependencies and run the build before publishing. Do not publish this source tree or `index.html` alone as a manual static deploy.

## Architecture
React + TypeScript + Vite; React Router; plain CSS; `qrcode`; Vitest. Queue state transitions are isolated in `src/state/queueMachine.ts`; collision-safe token allocation lives in `src/utils/tokens.ts`; route token selection in `src/utils/patientSelection.ts` never restores a previously selected token when the URL has none. State storage is guarded against blocked/corrupt localStorage and syncs open tabs using BroadcastChannel and the storage event. `src/routing/dijkstra.ts` contains the illustrative graph and shortest-path function. Wait estimates use the average of up to the last ten completed synthetic consultations, or the department’s sample baseline, plus simulated doctor delay; the result is rounded up to a five-minute increment and shown as **about N min**.

## Registration reset behavior
The alias and department are temporary form state and are not written to localStorage. After submission, the form draft is reset; the patient is redirected to the newly generated token. Opening “I have my slip” without a token starts with lookup instead of silently showing the last person. Previous fictional queue entries remain until served or the demo is reset, so staff and the board can still demonstrate a queue.

## Safety and limits
All names, tokens, patients, queues, wait estimates, doctors, alerts and maps are fictional. The prototype does not collect real personal or medical information, diagnose or triage, contact emergency services, send actual SMS/push messages, or connect to a hospital. Emergency advice says to go to Emergency/Casualty or tell nearby staff now; do not wait for a token. Only qualified staff assess emergencies. The 112/108 actions are telephone links only.

The staff PIN `2468` is a client-side demo gate and is bypassable. Production use would require secure server-side authorization, audit logs, privacy/security review, validated maps and workflows, hospital permission and a real backend. State syncs only across tabs in one browser profile; it does not synchronize between a patient’s phone and a staff computer. The floor plan is illustrative, not an official navigation map. Read-aloud and QR camera support vary by browser/device.

## Hackathon context
HackCache ’26 · Problem 2: Smart Queue Management and Accessible Navigation for Government Hospitals. Team name: Sudarshan. Team lead: Sudarshan A. Patil. Team members: Shubham and Pruthviraj. No hospital partnership, patient interviews, measured impact or production deployment is claimed.


## Team

Team name: Sudarshan. Team lead: Sudarshan A. Patil. Team members: Shubham and Pruthviraj. No hospital partnership, patient interviews, measured impact or production deployment is claimed.
