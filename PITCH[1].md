# WaitWise — Pitch and judge notes

**Team name:** Sudarshan  
**Team lead:** Sudarshan A. Patil  
**Team members:** Shubham and Pruthviraj

## 60–90 second pitch
Imagine visiting a busy government hospital, walking slowly, and not knowing which counter to visit, where your room is, or whether your turn is close. Even after receiving an OPD slip, the next steps can remain confusing—especially for older adults and people who prefer a regional language.

WaitWise is a mobile-first prototype for HackCache ’26 Problem 2. Visitors can choose English, Hindi, Tamil or Kannada; register using a fictional alias; receive a simulated token and QR link; check their turn; and follow landmark-based, step-free directions on an illustrative hospital map. Staff can demonstrate queue updates, doctor status, and urgent-help flags, while a waiting-room board shows the same simulated queue. Emergency/Casualty guidance remains visible without requiring a token.

All patient records, queues, waits, doctors, alerts and maps are simulated. The app does not diagnose, triage, send real SMS, or connect to an actual hospital. A real rollout needs a secured backend, staff roles and audit logs, validated maps, privacy review, accessibility testing and hospital integration. The goal is straightforward: make the next step clearer when a hospital visit is already stressful.

## Technical explanation
React + TypeScript + Vite; React Router; plain CSS; generated QR codes; explicit queue state machine; wait calculation rounded upward to five-minute increments; Dijkstra route calculation that excludes stair edges in Avoid Stairs mode; guarded localStorage with BroadcastChannel/storage-event synchronization for tabs in one browser; Vitest suites for queue transitions, wait logic, routes and translation-key parity.

## Honest impact framing
Potential impact: reduce uncertainty, repeated questions and avoidable wayfinding confusion. These are hypotheses, not measured outcomes. No patient study, hospital partnership, or measured waiting-time improvement is claimed.

## Next steps for real deployment
Co-design with patients, helpers and hospital staff; survey and validate an approved floor map; add authenticated staff roles, backend queue APIs, audit logs and monitoring; complete privacy/security and accessibility reviews; then run a controlled, approved pilot.

## Judge Q&A
**Is this connected to a real hospital?** No, it is a front-end prototype using fictional data and an illustrative layout.

**Does it sync between phones?** No. Open tabs in the same browser profile synchronize. Cross-device sync requires a secured server.

**Can it judge an emergency?** No. It directs visitors to Emergency/Casualty or nearby staff without a token; qualified staff assess urgent cases.

**How does the wait estimate work?** People ahead × average simulated service duration from up to ten completed demo consultations (or a sample department baseline), plus simulated doctor delay; rounded up to the next five-minute increment.

**What protects the staff console?** The `2468` gate is only for the demo and can be bypassed. Production needs server-side authentication, authorization and audit logs.

**What makes this more than a queue display?** It combines registration, slip and QR, My Turn, an accessible destination route, staff controls and a public waiting-room board in one journey.

**Team attribution:** Team name: Sudarshan. Team lead: Sudarshan A. Patil. Team members: Shubham and Pruthviraj. Describe each person’s actual contributions accurately; no mentors, hospital partnerships or interviews are claimed.
