# Technical Documentation

## HTML structure
`<header>` (logo, language, elderly mode, logout) and `<main>` with three sections: `#p1` login, `#pd` department grid, `#p2` dashboard. `#p2` holds the patient card, `#tabs`, `#alerts`, and panels `#t_j` Journey, `#t_m` Map, `#t_q` Queues & Doctors, `#t_d` Diseases, `#t_t` Tracking, `#t_a` Emergency/Admin (with `#ed` emergency dashboard and `#adm` admin).

## CSS architecture
Custom properties on `:root` (`--bg --card --ink --pri --acc --ok --warn --bad --bd`); dark theme via `prefers-color-scheme`; `body.big` for elderly mode; classes `.card .grid .dgrid .dd .step .pill` (status colours `sa sb sbr sd sn sf`), `.map`, `.alert`. Layout uses flex and CSS grid; safe-area insets are handled for phones.

## JavaScript architecture
One script, no modules or build. Sections: i18n, hospital model, doctors, state, speech, login, departments, persistence/QR, tabs/notifications, journey, map, queues/doctors, diseases, tracking, emergency/admin, emergency alerts and route management. Rendering is by string templates written to `innerHTML`; user text goes through `esc()`.

## Main functions
| Function | Purpose |
|---|---|
| `t(key, params)` | Translate by language index `li` |
| `render()` | Re-render everything after language change |
| `pickDept`, `setWf`, `mk` | Build the workflow (`wf`) |
| `rJ`, `cmp`, `skp` | Journey list, complete or skip a step |
| `path(a,b,wc,em)` | Dijkstra shortest path |
| `smart(a,b,wc)` | Choose emergency or regular routing |
| `dirs(path)` | Convert path to direction steps |
| `doRoute`, `draw` | Compute and draw the route |
| `simQ`, `rQ` | Queue simulation and table/chart |
| `dS(d)`, `rD` | Doctor status and cards |
| `sv`, `trk` | Save and read patient progress |
| `mkQR` | Draw token QR |
| `say`, `ordTxt` | Speech (click-only) and order text |
| `mkAlert`, `alS`, `alG`, `alJ`, `alV`, `rE` | Emergency alert create, status, guide, track, speak, dashboard |
| `resv`, `er` | Reserved emergency corridor and route length |
| `aList`, `tgR`, `tgD` | Admin area list, open/close, doctor delay |

## Data structures
- `T`: key -> `"en|ta|hi|ml"` strings (`{x}` placeholders).
- `FR`: 4 floors x 8 room keys; `R` room objects (`id, k, f, row, c, x, y, cx`); `RK` key -> room id; `G` adjacency list.
- `DW`, `DZ`: department and disease step strings (`?` marks "if ordered"); `SR` step -> room key; `CONS` consultation step set.
- `D`: doctors `{n,k,a,b,l1,l2,s,avg,q,c,dl,lv}`; `HOL` holidays.
- `Q[roomId]`: `{c current token, n waiting, w minutes}`.
- Alert: `{id,k,n,pid,tok,ts,loc,st,as,h[]}`.

## Department and workflow logic
`DW[dept]` or `DZ[disease][1]` is split on spaces into `{k, o, st}` (`o` optional, `st` 0 pending, 1 done, 2 skipped). The first step with `st===0` is current. Each step maps to a room by `SR`, defaulting to the department room.

## Map and routing
Nodes: rooms, corridor `C<f>_<c>`, alternate lane `A<f>_<c>`, lift `L<f>`, stairs `S<f>`. Weights: room-corridor 10, corridor step 12, alternate lane 14, lift 8-10, stairs 8-25. Distance shown in metres; walk time ~ 50 m/min. Wheelchair mode skips stairs edges. Closed areas (`closed[id]`) are skipped. Emergency mode (`em`) uses only the main corridor.

## Emergency route management
`resv()` computes the main-corridor and lift nodes on the shortest path from G-04 (Emergency) to each active alert (status below Resolved). Regular routes avoid those nodes via the alternate lane or stairs; if no alternative exists the route is shown with a notice. A 2 s poll recomputes and re-routes.

## Queue calculations
`simQ()` sets waiting `n` in 1-12 and wait `w = n x (2 or 3)` minutes, token `100 + 1..60`. Status colours: under 10 min low, under 20 moderate, else high.

## Doctor schedule logic
`dS()` returns Not Available if on leave, on a holiday today, or outside hours; On Break during lunch; Delayed if the admin flag is set; otherwise the base status. The demo clock (`clk`, minutes) can override real time (default 11:00). Estimated wait = queue x average + 30 if delayed.

## QR, storage, speech
- QR: `new QRCode(el, {text})` with text `SYNCARE|<id>|<token>|<dept>|<disease>|rec:<n>|doc:<steps>`.
- localStorage keys: `syn:<token>`, `syn:alerts`. Access is wrapped in try/catch.
- Speech: `speechSynthesis` with `en-IN, ta-IN, hi-IN, ml-IN`; only called from button handlers.

## Third-party dependencies
`qrcodejs 1.0.0` from cdnjs. Nothing else.

## Browser compatibility
Latest Chrome or Edge recommended. Safari and Firefox work for most features; speech voices and languages vary by device. Needs `localStorage`, `speechSynthesis` (optional), `AudioContext` (optional).

## Run and debug
Open `index.html` or serve with `python -m http.server`. Use DevTools Console and Application > Local Storage (`syn:` keys). Clear Local Storage to reset. Staff view: sign in with an email containing `admin`.

## Known issues and technical debt (documented, not changed)
- Authentication, OTP, captcha and roles are client-side only.
- Variables `recs` and `spoken` and the `CONS` set are leftovers from earlier features.
- Main Entrance/Exit and Billing appear in the admin list but not on the map.
- Alerts and tracking work only within one browser; 2-3 s polling is used instead of real-time channels.
- Patient location in alerts is the last chosen/checkpoint room, not live positioning.
- QR "scan" is a dropdown, not a camera scanner.
- The whole app is one file with large inline translation data; no tests or build pipeline.
- Tamil, Hindi, Malayalam text needs native/medical review.
- Fixed demo credentials are pre-filled in the login form.
