# Architecture

![Architecture](images/architecture.png)

## Overview
SynCare AI is a **client-side only** application delivered as one `index.html`. There is no server, database or AI API. All logic runs in the browser.

## Technology interaction
- **HTML** defines three screens (login, department selection, patient dashboard) and the tab panels.
- **CSS** (variables, light/dark via `prefers-color-scheme`, elderly mode class `big`) styles everything.
- **JavaScript** renders views with template strings, handles events, runs routing and business logic.
- **SVG** draws the indoor map (rooms, corridor, route, emergency highlights) and bar charts.
- **QRCode.js** (CDN) draws the token QR.
- **localStorage** stores patient progress and emergency alerts.
- **Web Speech API** speaks text when the user presses a Speak button. **Web Audio** plays a short beep for staff on new alerts.

## Modules
| # | Module | Responsibility |
|---|---|---|
| 1 | Authentication interface | Email/password or mock Google, captcha, OTP (demo), role from email |
| 2 | Language selection | `li` index and `t(key, params)` over dictionary `T` (EN/TA/HI/ML) |
| 3 | Accessibility controls | Elderly mode, wheelchair routing, click-only voice |
| 4 | Patient dashboard | Patient card (name, ID, token, QR, SOS), tabs, notifications |
| 5 | Department selection | 10 department cards -> `pickDept()` |
| 6 | Patient journey | Workflow list (`wf`), complete/skip, pharmacy stages |
| 7 | AI assistant interface | Rule-based suggestion text, Speak/Read order (no external AI) |
| 8 | Hospital map and navigation | Graph `G`, Dijkstra `path()`, `dirs()`, `draw()` |
| 9 | Queue management | `Q` per room, `simQ()`, table and chart |
| 10 | Doctor availability | Array `D`, `dS()` status from time, lunch, leave, holidays |
| 11 | Disease workflows | `DZ` (disease -> dept + steps), `DW` (department steps) |
| 12 | Patient tracking | Progress saved as `syn:<token>`, read by `trk()` |
| 13 | Emergency alerts | `mkAlert`, status flow, assignment, `resv()` corridor reservation |
| 14 | Administrative dashboard | Area open/closed toggles, doctor delay, emergency dashboard |

## Data flow
1. Login sets `U`, `role`, `tok`.
2. Department pick builds `wf` from `DW`/`DZ`; progress saved to `localStorage`.
3. Rendering functions (`rJ`, `rM`, `rQ`, `rD`, `rDz`, `rT`, `rA`, `rE`) read state and write HTML.
4. Timers: 2 s poll for alerts and corridor changes; 3 s refresh for tracking.

## User workflow
Language -> Login (captcha, OTP) -> Department -> Journey steps -> Navigate -> Complete steps -> Pharmacy -> Follow-up. A relative opens Patient tracking with the token.

## Navigation workflow
Select From/To -> `smart()` chooses mode -> `path()` Dijkstra over rooms, corridor nodes (`C`), alternate-lane nodes (`A`), lift (`L`) and stairs (`S`) -> `dirs()` builds steps -> `draw()` shows the route on the current floor. Closed areas are skipped. Wheelchair mode skips stairs. Speak reads the steps on click.

## Emergency workflow
Patient presses SOS -> chooses type -> alert saved (`syn:alerts`) with location -> staff dashboard shows it (poll) -> staff Acknowledge / assign / Responding / Resolved -> while active, `resv()` reserves the emergency path corridor and lift; regular routes avoid it via the alternate lane or stairs; routes refresh automatically.

## Storage approach
- In memory: rooms, doctors, queues, closed areas, notifications.
- `localStorage`: `syn:<token>` (patient progress), `syn:alerts` (alert list). Shared across tabs of one browser only.

## External dependencies
`https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js` only.

## Current technical limitations
No backend, persistence across devices, real security, push delivery, or automated tests. Routing graph is fixed in code. Alerts are not delivered to real staff devices.

## Recommended future backend (PLANNED, not implemented)
Frontend -> REST/WebSocket API -> auth service (OTP/OAuth, RBAC) -> database (patients, doctors, schedules, appointments, alerts) -> real-time/notification service -> optional AI assistant service with safeguards -> hospital information system integration; with encryption, audit logs and monitoring.
