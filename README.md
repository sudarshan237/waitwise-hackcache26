# WaitWise — HackCache '26 PS2

“A clearer next step for every hospital visit.” A standalone, mobile-first demo for a fictional government hospital.

## Run
Open `index.html` directly in a modern browser. It has no package installation or build step. For hosting, deploy `index.html` as a static site.

## Included
- English, Hindi and Kannada interface options.
- Three-step alias-only registration and token slip.
- Token lookup / My Turn and approximate queue wait.
- Staff dashboard with Call next, fictional sample patients, doctor status and urgent flags.
- Waiting-room board.
- Route finding over a fictional graph with Dijkstra shortest path and an avoid-stairs toggle.
- Emergency guidance with 112/108 tap-to-call links and staff-visible simulated urgent flag.
- Large text, high contrast, print/PDF slip, browser speech where supported.
- localStorage persistence and BroadcastChannel/storage events between tabs in the same browser.

## Honest limitations
This is a hackathon prototype, not a hospital system. Queue/doctor/patient data and alerts are simulated. It has no backend, staff authentication, real SMS/push messages, hospital integration, clinical triage, or cross-device sync. The route diagram is illustrative, not an indoor navigation authority. For possible emergencies, go to Emergency/Casualty or inform staff now; the app never diagnoses or decides clinical urgency. Only qualified staff assess urgent cases.
