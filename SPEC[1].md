# WaitWise — Specification

## Purpose
- HackCache '26 · Problem 2: Smart Queue Management and Accessible Navigation for Government Hospitals.
- Promise: “A clearer next step for every hospital visit.”
- Team: Sudarshan (team name); lead Sudarshan A. Patil; members Shubham and Pruthviraj.
- Audience: older adults, slow walkers, people who prefer local languages, and people who need clearer instructions.

## Mandatory boundaries
- Fictional hospital, tokens, patients, doctor status, queue and floor plan only.
- Collect a fictional alias only; never request actual phone, Aadhaar/ABHA, identity, symptoms or records.
- Emergency guidance is visible on every route. Tell users to go to Casualty or tell nearby staff immediately; no token is needed. Links: tel:112 and tel:108.
- Never diagnose, triage, promise an alert was sent, or say the queue/wait/map is real.
- Staff PIN 2468 is only a bypassable demo gate; production requires server-side authorization, privacy review and audit logs.

## Architecture
- Vite + React + TypeScript; plain CSS; React Router; qrcode package; Vitest.
- Small modules: `src/data/`, `src/locales.ts`, `src/state/`, `src/routing/`, `src/utils/`.
- `localStorage` with guarded reads/writes; `BroadcastChannel` plus storage event synchronizes tabs in the same browser only.
- Wait = (people ahead × average service minutes) + doctor delay; round up to next 5, display “about”. Average is based on at most 10 completed demo services, with sample department timing as fallback.
- Dijkstra graph; when Avoid Stairs is on, remove stair edges before routing.

## Core flows
- Home → local language → alias-only registration (3 steps) → token slip / QR → My Turn or token lookup. Registration draft fields are never written to storage and reset after submission; registered fictional queue entries remain for the staff/board demo. Token allocation checks the full existing token set before assigning a number. A generic patient page without a token shows lookup, not the prior selected patient details.
- Patient route + token query opens My Turn if the browser has that local demo state.
- Staff console: call/start/complete/hold/return/no-show/requeue/send to end/move department; doctor status; pinned urgent flags.
- Judge Demo: A-112 has exactly 3 waiting people ahead; previous urgent flags cleared; one synthetic flag added.
- Waiting-room board shows current token and next 3 per department; registration counter assists a visitor without a phone.
- Emergency route, step-free map, help desk route, accessibility toggles, localized UI.

## Acceptance checks
- Tests for legal/illegal queue transitions, wait arithmetic, route connectivity/step-free edges, and equal locale key sets.
- Build passes, app renders at 360px without horizontal scrolling, direct deep links survive refresh, and all controls do their stated action.
- Live URL is reported only after a real deployment has been checked.

## Explicit limitations
- No backend or cross-device synchronization, real hospital queue, verified floor plan, protected medical records, real authentication, SMS/push delivery, or clinical decision support.
- QR scanning appears only in browser/OS combinations that implement BarcodeDetector and grant camera access; camera permission and secure-context requirements apply.
