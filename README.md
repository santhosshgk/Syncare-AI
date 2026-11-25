# Syncare-AI
# SynCare AI: Synchronized Patient and Hospital Services

A single-file web app that guides a patient through a hospital visit, from login and department choice to consultation, tests, pharmacy and follow-up. It includes indoor navigation, live queues, a doctor schedule, relative tracking and an emergency alert system. It works in **English, Tamil, Hindi and Malayalam**.

> **Prototype notice:** OTP, Google sign-in, queues, doctor data and emergency alerts are simulated in the browser. A production build needs a backend, database, real authentication and encryption (see [Limitations](#limitations)).

## Tech stack
- HTML, CSS and vanilla JavaScript in one file (`index.html`)
- [qrcodejs 1.0.0](https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js) for QR codes (CDN)
- Browser Web Speech API for the voice assistant
- `localStorage` for demo persistence (patient progress, emergency alerts)
- SVG for the indoor map and charts
- Light and dark themes follow the device setting

## Run it
1. Download or clone the repo.
2. Open `index.html` in a modern browser (Chrome or Edge recommended). No build step or server is needed.
3. QR codes need internet access once for the CDN script.

## Login
1. Sign in with email and password, or use **Continue with Google** (simulated).
2. Solve the captcha.
3. Enter the 6-digit OTP. The demo OTP is shown on screen.

**Roles:**
- A normal email is a **patient**.
- An email containing `admin`, `doctor` or `nurse` is **staff**, with the Admin panel and Emergency dashboard controls.

## Features

### Patient flow
- **Department selection** after login: General Medicine, Neurology, Orthopedics, General Surgery, Gastroenterology, Pulmonology, Obstetrics & Gynecology, Cardiology, Endocrinology, Nephrology.
- **Separate consultation order for each department**, for example Registration → Triage/Vitals → Doctor → Examination → Tests (if ordered) → Results Review → Treatment → Follow-up.
- **Disease-based workflows** under each department: Diabetes, Hypertension, Coronary Artery Disease, Stroke, Asthma, Chronic Kidney Disease, Anemia, Thyroid Disorders, Dengue, Tuberculosis.
  - Steps marked *(if ordered)* can be skipped.
  - Tests appear only when a doctor orders them.
  - It gives guidance only, not a diagnosis.
  - A stroke warning is shown.
- **Pharmacy token** (paperless), with 5 stages.
- **Elderly mode** with larger text and buttons.

### Voice assistant (click-only)
- The voice speaks **only when the user presses a Speak button**. There is no automatic speech.
- Speak buttons: assistant suggestion, **Read my order**, route directions, and each emergency alert.
- Speaks in the selected language (en-IN, ta-IN, hi-IN, ml-IN). This depends on a voice for that language being installed on the device.

### Indoor navigation map
- 4 floors (G, 1, 2, 3), each with 8 rooms plus lift and stairs (for example G-01 Reception, G-05 Waiting Hall, G-06 Blood Test Lab).
- Shortest-path routing with step-by-step directions.
- Wheelchair mode (avoids stairs).
- QR checkpoint or manual choice for the current location. There is no live GPS.
- Zoom and floor switching.
- Closed areas are avoided in routes.
- An alternate pathway lane is drawn beside the main corridor.

### Queues and Doctor Live Schedule
- Live queues for Reception, Waiting Hall, Doctor Room, Blood Test Lab, ECG & Scan, Cardiology, Neurology, Orthopedics, Emergency and Pharmacy. Each shows the current token, number waiting, estimated wait and status. A bar chart and a *Simulate crowd change* button are included.
- **10 doctors** with specialization, today's hours, lunch break, average consult time, token, waiting count and estimated wait.
- Status (Available / Busy / On Break / Delayed / Not Available) updates automatically from hours, lunch, leave and holidays.
- A demo clock selector lets you preview daytime and lunch states.

### Patient tracking and QR
- Each patient gets a **token** and a **QR code** containing the token, patient ID, department, workflow and the number of health records.
- **Patient tracking tab:** relatives enter the shared token to see progress, the current step and the room. It refreshes automatically.

### Smart Emergency Alert System
- **SOS button** on the patient dashboard.
- Emergency types: chest pain, stroke symptoms, breathing difficulty, heavy bleeding, accident/injury, unconscious/not responding.
- Each alert records patient name, masked ID, token, type, timestamp and location (room and floor). It shows doctors, nurses and the emergency team as alerted.
- **Emergency dashboard** (Emergency/Admin tab):
  - Statuses: **New → Acknowledged → Responding → Resolved**, with counters.
  - Staff can assign a doctor, nurse team or emergency team.
  - **Guide team to patient** routes from the Emergency room (G-04) to the patient.
  - **Patient tracking** opens the patient's journey from the QR token.
  - A status history is shown on each alert.
  - Staff hear a beep and get a notification on a new alert. Patients see their own status updates.
- **Emergency route management:**
  - Emergency patients and staff get a dedicated shortest route (red).
  - The emergency corridor and lift are reserved while an alert is active.
  - Regular patients are rerouted by the alternate lane or stairs.
  - Routes update automatically as alerts change and when an alert is resolved.
  - If there is no alternative, a notice asks the patient to follow staff directions.
- **Data security (demo level):** patients see only their own alerts, and IDs are masked for non-staff.

### Admin panel
- Open/Closed toggle for every area on every floor (rooms, lift, stairs, plus Main Entrance/Exit and Billing in the list). Closed areas are avoided by routes.
- Mark a doctor as delayed or clear the delay.
- Staff roles only.

### Notifications
Token approaching, test step complete, pharmacy ready, follow-up reminder, doctor availability change, emergency alerts, route updates.

### Languages
All text, including map labels and voice, is available in English, Tamil, Hindi and Malayalam via the header selector.

## Project structure
```
index.html   # the entire app (HTML + CSS + JS, logo embedded)
README.md
```

## Limitations
- OTP, Google login, queue numbers, doctor data and alerts are **simulated**. Data is not real and is not shared across devices.
- Alerts and patient tracking work between tabs of the **same browser** (via `localStorage`).
- No real push or SMS delivery to staff phones.
- Health-record upload was removed from the interface, and no medical records are stored.
- Data is not encrypted and there are no audit logs.
- Voice depends on the device having a voice for the chosen language, especially Malayalam.
- Main Entrance/Exit and Billing appear in the admin list but are not drawn on the map.

## Roadmap (production)
- Backend and database (doctors, schedules, patients, appointments, alerts)
- Real authentication (OTP/SMS, Google OAuth) and role-based access control
- Real-time queues and alerts (WebSockets or push notifications)
- Encrypted records with access logging
- Appointment booking, rescheduling and doctor-delay handling with patient confirmation
- Analytics dashboard (department load, waiting time, patient flow)
- Secure health-record upload

## Disclaimer
SynCare AI provides navigation and process guidance only. It does not diagnose conditions or prescribe medicines. Tests and treatment are decided by qualified doctors.
