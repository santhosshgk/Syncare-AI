# Security Policy

## Status
SynCare AI is a **client-side hackathon prototype**. It is **not secure for real patient data** and must not be used in a clinical setting.

## Known limitations
- **Authentication is simulated.** Any password is accepted; OTP and captcha are generated and checked in the browser; Google sign-in is a mock.
- **Role-based access is client-side.** Staff access is granted if the email contains `admin`, `doctor` or `nurse`. Anyone can bypass it with browser tools.
- **Client-side data exposure.** All data lives in browser memory and `localStorage` (`syn:<token>`, `syn:alerts`) in plain text, readable and editable by anyone using the device.
- **No encryption, no audit logs, no server-side validation.**
- **Patient privacy.** Names and IDs entered are stored unencrypted in the browser. IDs are only masked in the UI for non-staff.
- **Alerts are not reliable.** Emergency alerts are shared between tabs of one browser, not delivered to real staff devices. Never rely on this for real emergencies.
- **Third-party script.** `qrcodejs` loads from cdnjs. Pin the version and consider self-hosting with Subresource Integrity.

## Guidance for a production version
- Server-side authentication (OTP/SMS, OAuth) with secure sessions and role-based access control.
- HTTPS everywhere, secure HTTP headers and a Content Security Policy.
- Encryption of patient data in transit and at rest, minimal data collection, retention limits.
- Audit logging of all access to patient records and alerts.
- Secure REST/WebSocket APIs with input validation, rate limiting and authorization checks.
- Compliance review under applicable health-data law (e.g. DPDP Act in India, HIPAA/GDPR elsewhere) before handling real data.
- Regular dependency scanning, penetration testing and incident response plan.

## Reporting a vulnerability
Please report privately; do **not** open a public issue.
- Email: `<security contact email>`
- Include: description, steps to reproduce, impact, and suggested fix.
- We aim to acknowledge reports within 7 days.

## Scope
In scope: the code in this repository. Out of scope: issues that stem only from the documented prototype limitations above.
