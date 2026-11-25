# User Guide

Screenshots: add yours in `docs/images/screenshots/` (names listed in the README).

## 1. Open the app
Open `index.html` in Chrome or Edge (or the GitHub Pages link). The header shows the logo, **Language** selector, **Elderly mode** and (after login) **Log out**.

## 2. Language
Use the **Language** dropdown (English, Tamil, Hindi, Malayalam). All text, map labels and voice change immediately.

## 3. Elderly mode
Press **Elderly mode** for larger text and buttons. Press again to turn it off.

## 4. Login (demo)
1. Enter an email and password (pre-filled: `raman@example.com` / `demo1234`; any password works).
2. Solve the captcha sum (↻ gives a new one).
3. Press **Send OTP**, or **Continue with Google** (simulated; the captcha is still required).
4. The demo OTP is shown on screen. Enter it and press **Verify & continue**.
5. Staff access: use an email containing `admin`, `doctor` or `nurse` (e.g. `admin@syncare.in`).

## 5. Select a department
Choose one of 10 departments. Each card shows the room, floor and related conditions. Press **Change department** to go back.

## 6. Patient card
Shows **Patient name**, **Patient ID**, your **Token**, a **QR code** and the red **SOS** button.

## 7. Journey tab
- **Conditions in this department:** *General order* or a disease (e.g. Diabetes) to see its workflow.
- **Consultation order:** numbered steps with room, floor, estimated wait. Steps marked *(if ordered)* only apply when a doctor orders them.
- The current step is highlighted. Buttons: **Navigate** (open route), **Complete (staff)** (marks the step done), **Not ordered** (skip optional step).
- **AI voice assistant:** shows the next suggestion. Press **🔊 Speak** to hear it or **Read my order** to hear the whole consultation order. Voice never plays automatically.
- **Pharmacy token:** five stages; **Next stage (staff)** advances them.

## 8. Map tab
1. Choose **From** and **To**. The route and directions appear automatically.
2. Tick **Wheelchair route** to avoid stairs.
3. **Show route / Recalculate** refreshes. **Scan QR** (choose a checkpoint, then press) sets your current location.
4. Use floor buttons (G, 1, 2, 3), **＋ － ⟲** to zoom/reset, and **Previous / Next** to move through directions. **🔊 Speak** reads the current step.
5. Room cards show code, name and wait; green/yellow/red dot shows crowding; red outline means closed. A red band marks the **emergency corridor** when an emergency is active.

## 9. Queues & Doctors tab
- **Live token queues:** current token, waiting count, estimated wait, status (Low/Moderate/High). **Simulate crowd change** randomises demo data.
- **Doctor Live Schedule:** 10 doctors with status (Available, Busy, On Break, Delayed, Not Available), today's hours, lunch, average consult time, token and estimated wait, leave and next holiday.
- **Demo clock:** choose 11:00, 13:15 (lunch), 19:00 or real time to preview automatic status changes.

## 10. Diseases tab
Cards for 10 conditions show department, location, workflow and specialist status. Press the button to load that workflow in Journey. Guidance only, not a diagnosis.

## 11. Patient tracking tab
- **Share this token with relatives:** shows your token. **Copy token** copies it.
- **Relative:** enter the token and press **Track** to see progress, current step and room. Works in the same browser in this demo.

## 12. Emergency
- Press **🚨 SOS** (patient card) or open **Emergency/Admin**.
- Choose the type (chest pain, stroke symptoms, breathing difficulty, heavy bleeding, accident/injury, unconscious) and press **Alert emergency team**.
- You are routed to the Emergency room. The **Emergency dashboard** shows your alert and its status: **New -> Acknowledged -> Responding -> Resolved**.
- Press **🔊 Speak** on an alert to hear a summary.

## 13. Staff / admin functions
- **Emergency dashboard:** counters, location, emergency route length, assign (doctor, nurse team, emergency team), status buttons, **Guide team to patient** (route from Emergency room), **Patient tracking**, status history.
- **Admin panel:** **Open/Closed** button for every area and floor (routes avoid closed areas); **Delay / clear** for a doctor.
- Patients see only the admin note "Admin only".

## 14. Notifications
Messages appear above the tabs (token near, test complete, pharmacy ready, follow-up, doctor status, emergency updates, route updates).
