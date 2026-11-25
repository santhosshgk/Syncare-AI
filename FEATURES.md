# Feature Catalogue

Status legend: **IMPLEMENTED** present in the code; **SIMULATED** interface and workflow exist but use demonstration logic; **PLANNED** not implemented.

## Detailed features

| # | Feature | Purpose | User benefit | How it works | Technology | Status |
|---|---|---|---|---|---|---|
| 1 | Login (email/password, Google, captcha, OTP) | Entry gate and role | Familiar sign-in flow | Captcha sum and random OTP shown on screen; any password accepted; Google is mocked | HTML, JS | SIMULATED |
| 2 | Role-based views | Separate patient and staff | Staff see admin tools | Email containing admin/doctor/nurse = staff (client-side only) | JS | SIMULATED |
| 3 | Four languages | Inclusion | Patients use own language | Dictionary `T`, function `t()` | JS | IMPLEMENTED |
| 4 | Elderly mode | Readability | Larger text/buttons | CSS class `big` | CSS | IMPLEMENTED |
| 5 | Department selection | Start of journey | Clear starting point | 10 cards, `pickDept()` | JS | IMPLEMENTED |
| 6 | Department consultation order | Show full sequence | Know what comes next | Step strings per department (`DW`) | JS | IMPLEMENTED |
| 7 | Disease workflows | Condition-specific sequence | Right pathway; tests only if ordered | 10 workflows (`DZ`), optional steps | JS | IMPLEMENTED |
| 8 | Journey tracking | Progress through steps | Clear state per step | Complete / skip, saved in localStorage | JS, localStorage | IMPLEMENTED (completion by "staff" button is a demo) |
| 9 | Voice assistant | Spoken guidance | Helps elderly and low-literacy users | Speaks only on click: suggestion, order, route, alert | Web Speech API | IMPLEMENTED (depends on device voices) |
| 10 | AI suggestion text | Next-step hint | Quick guidance | Rule-based from workflow and queue data; **no AI model** | JS | IMPLEMENTED (rule-based) |
| 11 | Indoor map | Find rooms | Less wandering | 4 floors x 8 rooms, SVG cards, corridor | SVG, JS | IMPLEMENTED |
| 12 | Routing and directions | Shortest path and steps | Easy navigation | Dijkstra over graph; lift/stairs; step text | JS | IMPLEMENTED |
| 13 | Wheelchair routing | Accessibility | Avoids stairs | Stairs edges excluded | JS | IMPLEMENTED |
| 14 | QR checkpoint location | Set current location | No GPS needed | Choose checkpoint, scan button | JS | SIMULATED (no camera scanning) |
| 15 | Token QR | Share token data | Quick identification | QR text with token, ID, dept, workflow | QRCode.js | IMPLEMENTED |
| 16 | Queue board | Show waits | Pick when/where to go | Random demo values; status colours; chart | JS, SVG | SIMULATED |
| 17 | Doctor Live Schedule | Availability | Know doctor status | 10 doctors; status from time, lunch, leave, holidays; demo clock | JS | SIMULATED data, IMPLEMENTED logic |
| 18 | Patient tracking | Relatives follow progress | Peace of mind | Token lookup in localStorage, auto refresh | localStorage | SIMULATED (same browser only) |
| 19 | Pharmacy token | Paperless pickup status | Know medicine readiness | 5 stages advanced by staff button | JS | SIMULATED |
| 20 | Notifications | Timely messages | Fewer missed steps | In-page messages | JS | IMPLEMENTED (in-page only) |
| 21 | SOS and emergency types | Raise an emergency | Fast alert | 6 types, alert with location | JS | SIMULATED |
| 22 | Emergency dashboard | Monitor and manage | Clear response status | New / Acknowledged / Responding / Resolved, assign, history | JS, localStorage | SIMULATED |
| 23 | Emergency route management | Keep corridors clear | Faster emergency access | Emergency path reserved; regular routes use alternate lane/stairs; auto reroute | JS | SIMULATED (client-side) |
| 24 | Admin area control | Close/open areas | Routes avoid closed areas | Per-area toggle, all floors | JS | SIMULATED |
| 25 | Doctor delay toggle | Reflect delays | Accurate status | Admin toggle adds delay to estimate | JS | SIMULATED |
| 26 | Data masking | Privacy in UI | Less exposure | IDs masked for non-staff | JS | IMPLEMENTED (UI only) |
| 27 | Backend, database, real auth | Production readiness | Persistent secure system | n/a | n/a | PLANNED |
| 28 | Appointment booking, reschedule, history | Scheduling | Fewer queues | n/a | n/a | PLANNED |
| 29 | Analytics dashboard | Hospital insight | Better planning | n/a | n/a | PLANNED |
| 30 | Real AI assistant | Conversational help | Context-aware guidance | n/a | n/a | PLANNED |
| 31 | Push/SMS notifications | Reliable delivery | Staff/relatives alerted | n/a | n/a | PLANNED |
| 32 | Encrypted records, audit logs | Compliance | Protect data | n/a | n/a | PLANNED |

## Summary comparison
| Capability | Implemented | Simulated | Planned |
|---|---|---|---|
| Navigation and routing | Yes | QR checkpoint | Live positioning |
| Patient journey | Yes | Staff completion | EHR integration |
| Queues and doctors | Logic | Data | Real-time feeds |
| Emergency | UI and logic | Alerts, delivery | Real notifications |
| Authentication | UI | OTP, Google, roles | Real auth, RBAC |
| Data storage | localStorage | n/a | Database |
| AI | Rule-based hints | n/a | AI assistant |
