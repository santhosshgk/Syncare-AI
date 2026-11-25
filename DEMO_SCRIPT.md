# Demo Script (about 6 minutes)

**Before you start:** open the live link in Chrome; open a second tab with the same site for staff; turn volume on; check an English and a Tamil voice are installed; set Language to English; know the OTP appears on screen.

## Part 1: Introduction (30 s)
**Do:** show the login page and logo.
**Say:** "SynCare AI is Synchronized Patient and Hospital Services. It guides a patient from reception to consultation, tests, pharmacy and follow-up, and coordinates emergencies, in four languages."

## Part 2: Problem (45 s)
**Say:** "Patients don't know which department comes next or how to reach it. Waiting is unclear, elderly patients and relatives are left guessing, and emergencies need fast coordination."

## Part 3: Solution (45 s)
**Say:** "One platform gives a personalised consultation order, indoor navigation, live queues, doctor availability, relative tracking and an emergency system. This is a working prototype with simulated data."

## Part 4: Live demonstration (3 min)
1. **Login (20 s):** solve captcha, Send OTP, enter on-screen OTP. *Expect:* department screen. *Say:* "OTP and Google login are simulated."
2. **Language (10 s):** switch to Tamil, back to English. *Expect:* all text changes.
3. **Department (15 s):** pick Cardiology. *Expect:* Journey with its order. Select **Diabetes**-type chips under the department.
4. **Voice (20 s):** press **Read my order**. *Say:* "Voice speaks only on click, in the chosen language."
5. **Journey (20 s):** press **Complete (staff)**, then **Navigate** on the next step.
6. **Navigation (40 s):** Map shows the route across floors; tick **Wheelchair route**; press **Speak**. *Expect:* step directions.
7. **Queues and doctors (25 s):** open **Queues & Doctors**; press **Simulate crowd change**; change the **Demo clock** to 13:15 to show On Break.
8. **Patient tracking (25 s):** open **Patient tracking**, copy the token, paste into the relative box, **Track**. *Say:* "A relative follows the patient's progress."

## Part 5: Emergency demonstration (1 min)
1. Press **🚨 SOS**, choose *Chest pain*, **Alert emergency team**. *Expect:* alert card, route to Emergency.
2. In the second tab log in as `admin@syncare.in`; open **Emergency/Admin**. *Expect:* beep, alert with patient, type, time, location.
3. Press **Acknowledged**, assign **Emergency team 1**, **Responding**, **Guide team to patient** (red route, corridor band), then **Resolved**.
4. Show the Admin panel list: toggle **Lift (Floor 0)** closed. *Say:* "Regular routes avoid the emergency corridor and closed areas."

## Part 6: Future scope and conclusion (45 s)
**Say:** "Next: backend and database, real authentication, real-time queues and alerts, appointment booking, a safe AI assistant and hospital system integration. SynCare AI reduces confusion, supports elderly patients and speeds up emergency response."

## Transitions
Intro -> "Let's look at the problem" -> "Here is how we solve it" -> "Let me show it live" -> "Now the critical case: an emergency" -> "Here is where we go next."

## Backup plan
- **Voice silent:** show the on-screen text, say the browser voice is device dependent.
- **Tabs do not sync:** use the same browser profile, same site address; otherwise show the dashboard in one tab and narrate.
- **QR missing:** CDN blocked; say it needs internet once.
- **Anything breaks:** refresh, repeat from login (data is simulated), or play the recorded demo video.
