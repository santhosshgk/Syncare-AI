# Problem Statement

## Challenges in today's hospital experience
- **Navigation:** large hospitals have many floors, departments and corridors. First-time visitors often cannot find the right room.
- **Multi-department confusion:** a single visit may involve registration, triage, a doctor, a lab, imaging, a specialist and the pharmacy. Patients are rarely told the whole sequence up front.
- **Waiting and queues:** patients usually cannot see which queue is shorter or how long they may wait.
- **Elderly and differently abled patients:** small text, language barriers, stairs and long distances make visits harder. Many rely on relatives who are not present.
- **No synchronized journey view:** patients, relatives and staff do not share one view of "where is the patient in the process".
- **Emergency coordination delays:** alerts depend on people finding and informing the right team, and emergency routes can be blocked by regular traffic.
- **Doctor availability:** consultation hours, lunch breaks, leave and delays are hard to check.
- **Communication gaps:** information is spread across signboards, counters and verbal instructions, often in one language.

## Why it matters and who is affected
- **Patients and families:** stress, wasted time, missed steps.
- **Elderly and differently abled patients:** the highest burden.
- **Doctors, nurses and reception staff:** repeated directions and queue questions.
- **Administrators and emergency teams:** crowding, unclear load, slower response coordination.

(No statistics are cited here on purpose; any figures should be added only with a verified source.)

## How SynCare AI addresses these challenges
| Challenge | SynCare AI prototype response |
|---|---|
| Not knowing the sequence | Department-specific consultation order and disease workflows |
| Finding rooms | 4-floor indoor map, shortest route, step directions, QR checkpoint |
| Accessibility | Wheelchair routing, elderly mode, four languages, voice on demand |
| Waiting information | Queue board with current token, waiting count and estimated wait |
| Doctor availability | Live Schedule with status, hours, lunch, leave and holidays |
| Relatives not informed | Token sharing and Patient tracking tab |
| Emergency delays | SOS, alert dashboard, assignment, guided routes, reserved emergency corridor |
| Staff control | Admin panel to close areas and mark doctor delays |

## Expected impact (proposed, not yet measured)
- **Social:** less confusion and anxiety, more independence for elderly patients, better inclusion across languages.
- **Operational:** fewer directional queries to staff, better visibility of crowding, faster emergency coordination.

These benefits are **hypotheses for a real deployment**. The prototype has not been tested in a hospital.

## What the prototype demonstrates
A working client-side demonstration of the patient journey, navigation, queues, doctor schedule, tracking and emergency workflows using **simulated data**.

## Scope and limitations
- Single-file web prototype; no backend, database, real authentication, SMS/push or hospital integration.
- Data is simulated and stored only in the browser.
- Provides process guidance only; it does not diagnose or prescribe. Tests and medicines happen only when a qualified doctor orders them.
- Appointment booking, analytics and AI-model integration are not implemented.
