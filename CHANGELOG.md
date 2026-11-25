# Changelog

All notable changes to SynCare AI. Format based on Keep a Changelog.

## [1.0.0] - Hackathon prototype
### Added
- Login with email/password or Google (simulated), captcha and OTP.
- Language support: English, Tamil, Hindi, Malayalam for all text and voice.
- 10 departments, each with its own consultation order.
- 10 disease workflows (Diabetes, Hypertension, CAD, Stroke, Asthma, CKD, Anemia, Thyroid, Dengue, TB) with stroke warning.
- Patient journey with optional ("if ordered") steps, staff completion and pharmacy token stages.
- Click-only voice assistant: Speak, Read my order, route directions, emergency alert summary.
- Indoor navigation: 4 floors, lift/stairs, shortest route, step directions, wheelchair mode, QR checkpoint, zoom.
- Live-style queues for 10 locations with chart; 10-doctor Live Schedule with automatic status (hours, lunch, leave, holidays) and demo clock.
- Patient tracking via shared token; patient token QR.
- Notifications: token near, test complete, pharmacy ready, follow-up, doctor status, emergency.
- Smart Emergency Alert System: SOS, 6 emergency types, New/Acknowledged/Responding/Resolved, assignment, guide-team routing, status history.
- Emergency route management: dedicated emergency routes, reserved emergency corridor/lift, alternate lane for regular patients, real-time reroute.
- Admin panel: Open/Closed toggle for all areas, doctor delay toggle.
- Elderly mode, light/dark theme.

### Changed
- Automatic speech removed; voice now only on user click.

### Removed
- Health-record file upload control.

### Not implemented
- Backend, database, real authentication, appointment booking, analytics dashboards, encryption.
